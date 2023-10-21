# ESP32 Bluetooth RFID Reader

This Arduino project utilizes an ESP32 microcontroller and an MFRC522 RFID module to create a Bluetooth RFID reader. It employs the ESP32's Bluetooth capabilities and the RFCOMM protocol for data transmission and retrieval between devices.
This project not only can read data from RFID cards or fobs but can also program them

## Project Structure

The heart of the project lies within a case statement that interprets specific operation codes (opcodes) and determines the actions to take based on these codes. Below are the defined opcodes and their corresponding operations:

### Device RFID Error Return Codes

- `RFID_AUTH_FAILED_CODE (0x00000031)`: Indicates an authentication failure during RFID card reading.
- `RFID_WRIT_FAILED_CODE (0x00000032)`: Signifies a write operation failure to the RFID card.
- `RFID_READ_FAILED_CODE (0x00000033)`: Represents a read operation failure from the RFID card.
- `RFID_CARD_DETECT_CODE (0x00000034)`: Indicates the successful detection of an RFID card.
- `RFID_OPRX_SUCCES_CODE (0x00000035)`: Denotes the success of a specific operation.
- `RFID_CARD_SELECT_CODE (0x00000036)`: Marks the selection of an RFID card.

### Device Command Opcodes

- `RFID_READ_OPCODE_CODE (0x00000037)`: Initiates a command to read RFID data.
- `RFID_WRIT_OPCODE_CODE (0x00000038)`: Initiates a command to write RFID data.
- `RFID_PUSH_DATA_OPCODE (0x00000039)`: Initiates a command to push data to the connected device.
- `RFID_PULL_DATA_OPCODE (0x00000030)`: Initiates a command to pull data from the connected device.

### Appended Codes & Opcodes

- `RFID_OPRX_FAILED_CODE (0x00000041)`: Indicates the failure of a specific operation.
- `RFID_RESET_MCU_OPCODE (0x00000042)`: Initiates a command to reset the ESP32 microcontroller.

## How the Code Works

The ESP32, acting as a Bluetooth RFID reader, continuously listens for specific RFCOMM messages. Upon receiving an opcode, it determines the action to perform based on the opcode received. Here's how the code operates:

- When the opcode is `RFID_PUSH_DATA_OPCODE`:
  - The ESP32 collects data from the connected device, stores it, and responds with success or failure.
- When the opcode is `RFID_PULL_DATA_OPCODE`:
  - The ESP32 retrieves data from its memory and sends it to the connected device.
- When the opcode is `RFID_READ_OPCODE_CODE`:
  - The ESP32 reads data from the RFID module and responds with success or failure.
- When the opcode is `RFID_WRIT_OPCODE_CODE`:
  - The ESP32 writes data to the RFID module and responds with success or failure.
- When the opcode is `RFID_RESET_MCU_OPCODE`:
  - The ESP32 resets when the opcode is sent
