# 🚗 EV-ADAS-STM32
## Real-Time Electric Vehicle Advanced Driver Assistance System

> A real-time embedded Electric Vehicle ADAS prototype built using
> **STM32F103C8T6**, Embedded C, HC-SR04 ultrasonic sensors, ADC,
> UART, GPIO, and timer peripherals.

---

# 🔎 Overview

**EV-ADAS-STM32** is an embedded Electric Vehicle Advanced Driver
Assistance System developed around the **STM32F103C8T6 (Blue Pill)**.

The project combines an **EV control and vehicle-dynamics simulation**
with real-time ADAS functions.

The system continuously monitors vehicle parameters such as:

- Vehicle speed
- Accelerator input
- Brake input
- Battery State of Charge (SOC)
- Motor temperature
- Motor torque
- Regenerative braking
- Power consumption
- Estimated driving range

At the same time, three ultrasonic sensors monitor the surrounding
environment for obstacle detection and driver-assistance functions.

The system implements:

- Forward Collision Warning (FCW)
- Time-to-Collision (TTC)
- Blind Spot Detection (BSD)
- Overspeed Detection
- Obstacle Detection
- Vehicle Fault Detection
- UART-based testing and debugging

The project is intended as an **embedded automotive prototype and
educational platform** for studying EV control, sensor interfacing,
real-time processing, and ADAS safety logic.

---

# ✨ Features

### 🚘 EV Monitoring & Control

- Real-time vehicle speed calculation
- Accelerator pedal monitoring
- Brake pedal monitoring
- Motor torque calculation
- Motor temperature monitoring
- Battery SOC monitoring
- Regenerative braking model
- Power estimation
- Estimated driving range
- Vehicle state management
- Configurable maximum vehicle speed

### 🛡️ ADAS Functions

- Forward Collision Warning
- Time-to-Collision calculation
- Critical collision detection
- Left Blind Spot Detection
- Right Blind Spot Detection
- Overspeed detection
- Distance-based obstacle detection
- ADAS warning levels
- Warning hysteresis

### 🔊 Ultrasonic Perception

- Front HC-SR04 sensor
- Left HC-SR04 sensor
- Right HC-SR04 sensor
- Echo-time measurement
- Distance calculation
- Sensor validity checking
- Microsecond timing using TIM2

### ⚠️ Safety & Fault Handling

- Motor over-temperature detection
- Low battery SOC detection
- Collision-related fault detection
- Fault state handling
- Fault clearing
- Safety output indication

### 🔌 Communication

- UART debugging
- UART command shell
- Vehicle parameter injection
- Speed injection
- SOC injection
- Temperature injection
- System status monitoring

---

# 🧰 Hardware

| Component | Quantity | Purpose |
|---|---:|---|
| STM32F103C8T6 Blue Pill | 1 | Main controller |
| HC-SR04 Ultrasonic Sensor | 3 | Front/left/right obstacle detection |
| Potentiometer / Analog Input | As required | Accelerator/brake simulation |
| ADC Inputs | 4 | Vehicle parameter acquisition |
| LEDs | As required | Warning/status indication |
| ST-Link | 1 | Programming/debugging |
| USB-UART | 1 | Serial monitoring |
| Breadboard | 1 | Prototype implementation |
| Jumper Wires | As required | Connections |
| Power Supply | 1 | System power |

---

# 🔌 Pin / Peripheral Mapping

The project uses the STM32F103C8T6 peripherals for vehicle
input acquisition, sensor timing, communication, and warning outputs.

## ADC Inputs

| ADC Channel | Function |
|---|---|
| PA0 / ADC Channel 0 | Accelerator input |
| PA1 / ADC Channel 1 | Brake input |
| PA2 / ADC Channel 2 | Battery SOC input |
| PA3 / ADC Channel 3 | Temperature input |

---

## Timers

| Timer | Function |
|---|---|
| TIM1 | EV control periodic update |
| TIM2 | Microsecond timing for HC-SR04 |
| TIM3 | ADAS / sensor periodic update |

                  ┌────────────────────────┐
                  │     Vehicle Inputs     │
                  │                        │
                  │ Accelerator            │
                  │ Brake                  │
                  │ Battery SOC            │
                  │ Temperature            │
                  └───────────┬────────────┘
                              │
                              ▼
                  ┌────────────────────────┐
                  │     STM32F103C8T6       │
                  │    Main Controller      │
                  └───────────┬────────────┘
                              │
             ┌────────────────┴────────────────┐
             │                                 │
             ▼                                 ▼
   ┌────────────────────┐           ┌────────────────────┐
   │    EV CONTROL      │           │   ADAS PROCESSING  │
   │                    │           │                    │
   │ Speed              │           │ Distance           │
   │ Torque             │           │ TTC                │
   │ SOC                │           │ FCW                │
   │ Temperature        │           │ BSD                │
   │ Power              │           │ Overspeed          │
   │ Range              │           │                    │
   └──────────┬─────────┘           └──────────┬─────────┘
              │                                │
              └────────────────┬───────────────┘
                               │
                               ▼
                    ┌────────────────────┐
                    │  FAULT MANAGEMENT  │
                    │                    │
                    │ Over Temperature  │
                    │ Low SOC           │
                    │ Collision         │
                    └─────────┬──────────┘
                              │
                              ▼
                    ┌────────────────────┐
                    │ WARNING / STATUS   │
                    │                    │
                    │ LEDs               │
                    │ UART               │
                    └────────────────────┘
