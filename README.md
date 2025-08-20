# Arduino-Ultrasonic-Obsticle-Detector
# Arduino Smart Blind Stick

An assistive technology project designed to enhance mobility for the visually impaired. This smart stick uses ultrasonic sensors to detect obstacles within a close range and provides haptic (vibration) and auditory (buzzer) feedback to the user.

## ✨ Features

*   **Obstacle Detection:** Accurately detects obstacles up to 10 cm away using an HC-SR04 ultrasonic sensor.
*   **Dual Alert System:** Provides immediate feedback through:
    *   **Auditory Alert:** A loud buzzer sound.
    *   **Visual Alert:** A bright LED (can be replaced with a vibrating motor for discretion).
*   **Simple & Robust:** Built with minimal, widely available components for reliability and ease of replication.

## 📦 Bill of Materials (Components)

| Component | Quantity | Notes |
| :--- | :--- | :--- |
| Arduino Uno | 1 | Or any compatible board (Nano, etc.) |
| HC-SR04 Ultrasonic Sensor | 1 | The core distance sensor |
| Buzzer | 1 | For audible alerts |
| LED | 1 | For visual alerts (or use a Vibrating Motor) |
| 220Ω Resistor | 1 | For the LED (if used) |
| Jumper Wires | Several | For connections |
| Breadboard | 1 | For prototyping |
| Power Source | 1 | 9V Battery + Barrel Jack or USB Power Bank |

## 🔌 Circuit Diagram & Wiring

The wiring is simple and follows the provided diagram. The sensor, buzzer, and LED are all powered by the Arduino's 5V pin.

| Arduino Pin | Component | Pin Name |
| :--- | :--- | :--- |
| `5V` | HC-SR04 | `VCC` |
| `GND` | HC-SR04 | `GND` |
| `9` | HC-SR04 | `Trig` |
| `10` | HC-SR04 | `Echo` |
| `11` | Buzzer | Positive (+) |
| `13` | LED | Anode (+) (via resistor) |
| `GND` | Buzzer & LED | Cathode / Negative (-) |

**Note:** For a more practical and discreet stick, **replace the LED with a vibrating motor (e.g., from an old phone)**. Connect it to pin `13` instead of the LED.

![Wiring Diagram]([images/circuit_diagram.jpg](https://github.com/shiv-rathod-bme/Arduino-Ultrasonic-Obsticle-Detector/blob/403e3ae6f0783d01d4fac598c10dc99b03a9fc39/circuit_image.png))

## 🚀 Getting Started

### 1. Hardware Setup
1.  Connect all components on a breadboard according to the wiring table above.
2.  Double-check all connections, especially power (5V) and ground (GND).
3.  For a permanent build, solder the components onto a perfboard and secure them to the walking stick.

### 2. Software Setup
1.  **Upload Code:** Connect your Arduino to your computer. Open the `.ino` file from this repository in the Arduino IDE and upload it to the board.
2.  **Test:** The system is now active. Wave your hand in front of the sensor (within 10 cm) to trigger the buzzer and LED.

### 3. Enclosure & Power
1.  Mount the Arduino, breadboard/perfboard, and sensors securely onto a walking stick.
2.  Power the device using a portable USB power bank for extended mobility.

## ⚙️ How It Works

The code operates in a simple loop:
1.  **Trigger:** The Arduino sends a short ultrasonic pulse from the `Trig` pin.
2.  **Listen:** The `Echo` pin listens for the return pulse.
3.  **Calculate:** The Arduino calculates the distance to the obstacle based on the time it took for the sound wave to return.
4.  **Alert:** If the calculated distance is **10 cm or less**, the Arduino immediately activates the buzzer and LED to warn the user.

You can easily adjust the sensitivity by changing the `10` in the line `if (safetyDistance <= 10)` to a larger or smaller number.

