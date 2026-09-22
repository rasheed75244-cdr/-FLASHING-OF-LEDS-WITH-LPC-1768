# FLASHING-OF-LEDS-WITH-LPC-1768

# AIM: 
   To interface and toggle the led with ARM LPC 1768 microprocessor           
           
# COMPONENTS REQUIRED:
##  HARDWARE:
ARM LPC1768
LED
## SOFTWARE:
KEIL MICRO VISION 4.0 IDE

# PROCEDURE:


⮚	Open the Keil software and select the New uvision project from Project Menu as shown below.
⮚	Browse to your project folder and provide the project name and click on save.
⮚	Once the project is saved a new pop up “Select Device for Target” opens, Select the controller (NXP: LPC1768) from NXP (founded by philips) and click on OK.
⮚	Select the controller (NXP: LPC1768) and click on OK.
⮚	As LPC1768 needs the startup code, click on Yes option to include the LPC17xx Startup file.
⮚	Create a new file by file → new to write the program.
⮚	Type the code.
⮚	After typing the code save the file as main.c eg. (abc.c).
⮚	Right click target and Add the suitable files to source group1 and header for the project.
⮚	Add the main.c along with system_LPC17xx.c.
⮚	Build the project and fix the compiler errors/warnings if any.
⮚	Code is compiled with no errors. The .bin file is still not generated.
⮚	Right Click on Target Options to select the option for generating .bin file.
⮚	Set IROM1 start address as 0x2000. Bootloader will be stored from 0x0000- 0x2000 so application should start from 0x2000
⮚	Write	the	command	to	generate	the .bin file	from
.axf file
Command: fromelf --bin projectname.axf --output filename.bin
⮚	in c/c++ → include paths → desktop (00-libfiles).
⮚	.Bin file is generated after a rebuild.
⮚	Check the project folder for the generated .Bin file.

# ADD FILES:
Target1:
Source group1:
Startuplpc17xx.s, main.c (t), delay.c (t), systemlpc17xx.c (t), gpio.c (t)
Header:
Delay.h, stdutils.h, gpioi.h

# PIN DIAGRAM :
 <img width="767" height="416" alt="image" src="https://github.com/user-attachments/assets/780562e3-06d7-40ac-a1d7-86c0a3f5e08a" />


# CIRCUIT DIAGRAM:
 <img width="715" height="366" alt="image" src="https://github.com/user-attachments/assets/56b1894f-7675-4e1f-b08e-378b777124aa" />

 
# PROGRAM:

#include <lpc17xx.h> \
#include "delay.h"       // User-defined library for delay routines \
#include "gpio.h"        // User-defined GPIO library \

#define LED P1_29        // LED is connected to P1.29 \


int main()

{
    SystemInit();                          // Clock and PLL configuration

    GPIO_PinFunction(LED, PINSEL_FUNC_0);  // Configure P1.29 as GPIO
    GPIO_PinDirection(LED, OUTPUT);        // Configure P1.29 as OUTPUT
    GPIO_PinWrite(LED, LOW);               // Initially turn OFF LED

    while(1)
    {
        // Turn ON LED
        GPIO_PinWrite(LED, HIGH);
        DELAY_ms(100);                     // Wait for 100 ms

        // Turn OFF LED
        GPIO_PinWrite(LED, LOW);
        DELAY_ms(100);                     // Wait for 100 ms
    }
}
 
# Output:

<img width="960" height="1280" alt="image" src="https://github.com/user-attachments/assets/127c88b8-715e-4565-8b66-f89d1b2de1d6" />




# Result :
Thus, a LED is interfaced and toggled with ARM LPC1768 Microprocessor.

