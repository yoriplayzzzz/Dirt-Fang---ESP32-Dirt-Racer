
# Dirt Fang - A Dirt Racer

In this project, we will create a **RC Car** capapble of Racing in dirt and overcoming several obstacles which you face on dirt and uneven roads using **ESP32-WROOM.**

## Hardware Required
| Component | Specification | Details |
| :--- | :--- | :--- |
| **Microcontroller** | ESP32 Dev Board | Dual-core processing & Bluetooth control |
| **Addons*** | ESP32 Expansion Board | Easy Accessibility of pins and power |
| **Motor Drivers** | 2x BTS7960 | High-current capacity for 4WD |
| **Motors** | 4x Johnson DC Gear | 500 RPM high-torque output |
| **Power Source** |11.1V Li-ion/Li-po Battery | High-discharge for explosive movement |
| **Regulation** | LM2596 Buck Converter | Steps down 11.1V to 5V for the ESP32 |
| **Drivetrain** | 4-Wheel Drive (4WD) | Rubber tires for maximum pitch traction |
| **Tools** | USB data Cable, Screwdriver, Soldering Iron | Necesaasry tools |

**⚠️ Note:*** This is only ***Optional*** and you can continue the project without its use.
## Wiring Pinout
The way this project works is that instead of connecting 2 motors diagnolly in the same power source, **we have decided to use it parallely for efficient use of code.** 

Therefore The motors on the ***left side are connected to the same BTS7960*** and ***the Right saide is done the same with another BTS7960.***

### Left Side

| ESP32 Pin | BTS7960 Pin | Function |
| :--- | :--- | :--- |
| **GPIO 25** | RPWM | Right PWM |
| **GPIO 26** | LPWM | Left PWM |
| **GPIO 27** | R_EN | Right Enable |
| **GPIO 14** | L_EN | Left Enable |

### Right Side 

| ESP32 Pin | BTS7960 Pin | Function |
| :--- | :--- | :--- |
| **GPIO 32** | RPWM | Right PWM |
| **GPIO 33** | LPWM | Left PWM |
| **GPIO 12** | R_EN | Right Enable |
| **GPIO 13** | L_EN | Left Enable |


<img width="1600" height="1504" alt="Circuit Diagram" src="https://github.com/user-attachments/assets/0e56af0c-94a2-4d88-9085-936ebf3b8629" />

## Power Distribution

| Connection | Path | Target |
| :--- | :--- | :--- |
| **Main Power** | 11.1V LiPo | Driver 1, Driver 2, & Buck Converter |
| **Logic Power** | 5V Out (Buck) | ESP32 VIN & BTS7960 VCC Pins |
| **Driver 1 Out** | Motor Leads | Front Left & Rear Left Motors |
| **Driver 2 Out** | Motor Leads | Front Right & Rear Right Motors |
## Installation

For the Installation, first we need to download the USB to UART Convertor Drivers. The most used is CP2102.

### Installing CP2102 Drivers
- Go to [***Silicon Labs Website.***](https://www.silabs.com/software-and-tools/usb-to-uart-bridge-vcp-drivers?tab=overview)
- Open the Download Section
- Download The ***Windows VCP Driver***
  
  <img width="1899" height="825" alt="Cp2102" src="https://github.com/user-attachments/assets/bfe82991-2dab-4705-aceb-4ca50d5ab3cf" />


Now the second step is to Download the Flash Tool. We will use the Flash Tool Downloader provided by [**Espressif themselves**](https://docs.espressif.com/projects/esp-test-tools/en/latest/esp32c6/production_stage/tools/flash_download_tool.html).

### The Flash
- Open the Flash Download Tool.
- Select the Chip Type as **ESP32**.
- Set the Downloading path(in Hexedecimal format on the following way)
```text
/
├── 0x1000
├── 0x8000
└── 0x10000
```
- Now in the first columnm, add **ESP32-BTS7960.ino.bootloader.bin**
- **ESP32-BTS7960.ino.partitions.bin** in the second one.
- **ESP32-BTS7960.ino.bin** in the third one.
```text
/
├── |ESP32-BTS7960.ino.bootloader.bin| 0x1000|
├── |ESP32-BTS7960.ino.partitions.bin| 0x8000|
└── |ESP32-BTS7960.ino.bin| 0x10000
```

<img width="423" height="689" alt="Screenshot 2026-05-10 172659" src="https://github.com/user-attachments/assets/3effde10-cbdd-4e87-a20a-d5c06d593be0" />


- Click ***START***. Now the code is uploaded.
- Hit the **EN** button and reset the ESP32. Now Open your bluetooth settings and try searching for ***ESP32-Dirt-Fang***
  <img width="1080" height="730" alt="1778414071412" src="https://github.com/user-attachments/assets/c6e14c40-5e4d-4efc-a395-bcd66c7be9cb" />


- Download the [***BLUETOOTH RC CAR CONTROL APP***](https://drive.google.com/file/d/1Wrmlk7zawrU3TbYtjh0lwUrek8ABfNiz) on your mobile. 


## The Project is accomplished

Now you can play with the RC CAR.
