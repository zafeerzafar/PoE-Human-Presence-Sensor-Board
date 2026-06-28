# PoE-Powered Multi-Sensor Human Presence Detection Board

A 4-layer ESP32-S3 based development board designed for human presence detection applications, powered over Ethernet (PoE) at 48V with onboard isolated DC-DC conversion and support for five different UART-based mmWave radar sensors.

---

## Overview

This board was designed to enable flexible, wired-network-connected human presence sensing in smart building, occupancy monitoring, and security applications. It accepts 48V PoE input and provides clean, regulated power to the ESP32-S3 and connected sensors, with galvanic isolation between the PoE power rail and sensitive signal circuitry.

The board supports five Hi-Link mmWave radar sensor modules interchangeably, all communicating over UART, making it adaptable to different detection range and resolution requirements without hardware redesign.

---

## Key Specifications

| Parameter | Value |
|---|---|
| Input Voltage | 48V (PoE) |
| Main Power Output | 5V @ 4A (20W) |
| Isolated Power Output | 5V @ 200mA (1W) via B0505S |
| Microcontroller | ESP32-S3 |
| PCB Layers | 4 |
| Signal Layers | Top + Bottom |
| Inner Layers | Dedicated GND planes |
| Sensor Interface | UART |
| Design Tool | EasyEDA |

---

## Supported Sensors

The board is designed to support the following Hi-Link mmWave human presence radar modules interchangeably:

| Sensor | Description |
|---|---|
| LD2410B | 24GHz presence detection, GPIO + UART output |
| LD2410C | Compact variant of LD2410 series |
| LD2420 | Multi-target presence and motion detection |
| LD2450 | Multi-target tracking with position data |
| LD2412 | High sensitivity presence detection |

All sensors communicate with the ESP32-S3 over UART.

---

## Connectivity

The board exposes the following interfaces:

- **PoE** — 48V input, primary power source
- **Ethernet** — Wired network connectivity for ESP32-S3
- **USB Type-C** — For firmware flashing and serial debugging
- **Barrel Jack** — Alternative 5V power input (bypasses PoE)

---

## Power Architecture

```
48V PoE Input
     │
     ├──► DC-DC Buck Converter ──► 5V @ 4A ──► ESP32-S3 + Sensors
     │
     └──► B0505S Isolated DC-DC ──► Isolated 5V @ 200mA ──► Isolated signal circuitry
```

The B0505S isolated DC-DC converter provides galvanic isolation between the PoE power domain and sensitive analog/signal circuitry, preventing ground loops and protecting downstream components from PoE transients.

---

## PCB Design Highlights

### 4-Layer Stackup
```
Layer 1 (Top)    — Signal + Components
Layer 2          — Dedicated GND plane
Layer 3          — Dedicated GND plane
Layer 4 (Bottom) — Signal
```
Dual internal GND planes provide:
- Low impedance return paths for high-frequency signals
- Effective EMI shielding between top and bottom signal layers
- Controlled impedance for Ethernet and USB traces

### Signal Integrity Measures
- **Ethernet traces** — impedance controlled to 100Ω differential per IEEE 802.3 requirements
- **USB differential pair** — impedance controlled to 90Ω with trace length matching to minimise skew and ensure USB signal integrity
- **PoE isolation** — physical and electrical separation between 48V PoE domain and 5V signal domain
- **EMI mitigation** — ground planes, component placement, and trace routing optimised to minimise radiated emissions

### Design Challenges Solved
- Studied datasheets for all five sensor modules to determine correct UART pinouts, voltage levels, and power requirements
- Achieved impedance matching for Ethernet and USB differential pairs on a 4-layer stackup in EasyEDA
- Implemented galvanic isolation between PoE input and signal circuitry using the B0505S module
- Managed trace length matching for USB differential pair to maintain signal integrity at USB 2.0 speeds
- Routed high-current 48V and 5V power traces with appropriate width for thermal and current capacity

---

## Repository Contents

```
├── Schematics/          # EasyEDA schematic files and PDF exports
├── PCB/                 # EasyEDA PCB layout files
├── 3D_Renders/          # 3D renders of the board (top and bottom views)
├── BOM/                 # Bill of Materials
└── README.md
```

---

## 3D Renders

*(Add top and bottom 3D render images here)*

---

## Status

| Stage | Status |
|---|---|
| Schematic Design | ✅ Complete |
| PCB Layout | ✅ Complete |
| Design Rule Check (DRC) | ✅ Passed |

---

## Tools Used

- **EasyEDA** — Schematic capture and PCB layout
- **Hi-Link sensor datasheets** — LD2410B, LD2410C, LD2420, LD2450, LD2412

---

## Author

**Muhammad Zafeer Zafar**  
Embedded Systems Engineer | FPGA · Bare-Metal Firmware · PCB Design  
[LinkedIn](https://www.linkedin.com/in/zafeerzafar) | [GitHub](https://github.com/zafeerzafar)
