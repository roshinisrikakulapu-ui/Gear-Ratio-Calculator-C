#include <stdio.h>

float calculateGearRatio(int driverTeeth, int drivenTeeth) {
    return (float)drivenTeeth / driverTeeth;
}

float calculateOutputSpeed(float inputSpeed, float gearRatio) {
    return inputSpeed / gearRatio;
}

float calculateOutputTorque(float inputTorque, float gearRatio) {
    return inputTorque * gearRatio;
}

int main() {
    int choice;
    int driverTeeth, drivenTeeth;
    float inputSpeed, inputTorque;
    float gearRatio, outputSpeed, outputTorque;

    while (1) {
        printf("\n====================================\n");
        printf("      GEAR RATIO CALCULATOR\n");
        printf("====================================\n");
        printf("1. Calculate Gear Ratio\n");
        printf("2. Calculate Output Speed\n");
        printf("3. Calculate Output Torque\n");
        printf("4. Calculate All Parameters\n");
        printf("5. Exit\n");
        printf("------------------------------------\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        if (choice == 5) {
            printf("\nThank you for using Gear Ratio Calculator!\n");
            break;
        }

        if (choice < 1 || choice > 5) {
            printf("Invalid choice! Please try again.\n");
            continue;
        }

        printf("\nEnter Driver Gear Teeth: ");
        scanf("%d", &driverTeeth);

        printf("Enter Driven Gear Teeth: ");
        scanf("%d", &drivenTeeth);

        if (driverTeeth <= 0 || drivenTeeth <= 0) {
            printf("Gear teeth must be greater than zero!\n");
            continue;
        }

        gearRatio = calculateGearRatio(driverTeeth, drivenTeeth);

        switch (choice) {

            case 1:
                printf("\nGear Ratio = %.2f\n", gearRatio);
                break;

            case 2:
                printf("Enter Input Speed (RPM): ");
                scanf("%f", &inputSpeed);

                outputSpeed = calculateOutputSpeed(inputSpeed, gearRatio);

                printf("\nGear Ratio = %.2f\n", gearRatio);
                printf("Output Speed = %.2f RPM\n", outputSpeed);
                break;

            case 3:
                printf("Enter Input Torque (Nm): ");
                scanf("%f", &inputTorque);

                outputTorque = calculateOutputTorque(inputTorque, gearRatio);

                printf("\nGear Ratio = %.2f\n", gearRatio);
                printf("Output Torque = %.2f Nm\n", outputTorque);
                break;

            case 4:
                printf("Enter Input Speed (RPM): ");
                scanf("%f", &inputSpeed);

                printf("Enter Input Torque (Nm): ");
                scanf("%f", &inputTorque);

                outputSpeed = calculateOutputSpeed(inputSpeed, gearRatio);
                outputTorque = calculateOutputTorque(inputTorque, gearRatio);

                printf("\n========== RESULTS ==========\n");
                printf("Gear Ratio    : %.2f\n", gearRatio);
                printf("Output Speed  : %.2f RPM\n", outputSpeed);
                printf("Output Torque : %.2f Nm\n", outputTorque);
                printf("=============================\n");
                break;
        }
    }

    return 0;
}
