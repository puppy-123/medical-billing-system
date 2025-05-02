class Patient:
    def __init__(self, name, sickness, symptoms, procedures, prevention):
        self.name = name
        self.sickness = sickness
        self.symptoms = symptoms
        self.procedures = procedures
        self.prevention = prevention
        self.bill = self.calculate_bill()

    def calculate_bill(self):
        base_cost = 20  # Affordable price per procedure
        total_cost = base_cost * len(self.procedures)
        return min(total_cost, 100)  # Max affordable limit

    def display_bill(self):
        print("\n--- Medical Bill ---")
        print(f"Patient Name     : {self.name}")
        print(f"Sickness         : {self.sickness}")
        print(f"Symptoms         : {', '.join(self.symptoms)}")
        print(f"Procedures       : {', '.join(self.procedures)}")
        print(f"Prevention Tips  : {self.prevention}")
        print(f"Total Bill Amount: ${self.bill:.2f}")
        print("---------------------")


# Main loop to input and display patient data
if __name__ == "__main__":
    while True:
        print("\nEnter patient details:")

        name = input("Patient Name: ")
        sickness = input("Sickness: ")
        symptoms = input("Symptoms (comma separated): ").split(',')
        procedures = input("Procedures (comma separated): ").split(',')
        prevention = input("Prevention Tips: ")

        # Clean up spaces
        symptoms = [s.strip() for s in symptoms]
        procedures = [p.strip() for p in procedures]

        patient = Patient(name, sickness, symptoms, procedures, prevention)
        patient.display_bill()

        another = input("\nDo you want to enter another patient? (yes/no): ").strip().lower()
        if another != 'yes':
            print("Exiting system. Stay healthy!")
            break
