# EV3 HuskyLens Stuff
An adapter allow HuskyLens communication with LEGO Mindstroms EV3 (support SPIKE/RI).

## How it works
The EV3/SPIKE/RI using LEGO UART protocol to communicate with sensors, and HuskyLens provide I2C and UART to transmit data, so we use an Arduino as an "Translator", to convert HuskyLens data to LEGO UART format.

## Hardware
We use an Arduino Pro Mini, and a simple PCB to connect HuskyLens pins and EV3 ports.
* Arduino Pro Mini 5V, 16 MHz with baud 115200 for EV3
* Arduino Pro Mini 3v3, 8 Mhz with baud 57600 for SPIKE/RI
* HuskyLens and Arduino communicate with baud 9600 (swuart)

Using avrdude or XLoader to upload firmware hex file to your Arduino Pro Mini, if you using ICSP to program your arduino, you can choose "_with_Bootloader" one hex file to programming to keep the bootloader there.

## Software
Go to release page to download EV3-G blocks, the block will return following info:
  * For a block:
    * `Connection status` see **Connection Status Code** below
    * `ID` ID of Block
    * `X` X Center of Block
    * `Y` Y Center of Block
    * `W` Width of Block
    * `H` Height of Block
  * For an arrow:
    * `Connection status` see **Connection Status Code** below
    * `ID` ID of Arrow
    * `x1` X Origin of Arrow 
    * `y1` Y Origin of Arrow
    * `x2` X Target of Arrow
    * `y2` Y Target of Arrow

### Connection Status Code:

|  Code  | Means                                                                       |
| -----  | --------------------------------------------------------------------------- |
|   9    | Adapter connected but HuskyLens not.                                        |
|   8    | Connection is OK but no objects learned.                                    |
|   7    | Connection is OK and objects is learned, but no objects appears.            |
|   1    | Objects found.                                                              |
|   0    | Port not connected or data loss.                                            |
| -----  | Port not connected or data loss.                                            |

## Documents used
 - [HUSKYLENSArduino](https://github.com/HuskyLens/HUSKYLENSArduino)
 - [EV3 Hardware Developer Kit](https://education.lego.com/en-us/support/mindstorms-ev3/developer-kits)

## Disclaimer
LEGO® is a trademark of the LEGO Group of companies which does not sponsor, authorize or endorse this software.
The LEGO Group and contributors to this repo are not liable for any loss, injury or damage arising from the use or misuse of the provided code or hardware.
