# UART Protocol 

This repository contains a complete **UART protocol design** in Verilog, including **baud rate generator, transmitter, receiver, and top-level integration** with testbenches. The project demonstrates asynchronous serial communication with configurable baud rate, parity checking, and error detection.

---

## 📘 Module Overview

### 1. Baud Rate Generator (`baud_rate.v`)
- **Inputs**: `clk`, `rst`
- **Outputs**: `tx_br`, `rx_br`
- **Function**: Divides system clock to generate baud pulses for TX and RX.

### 2. UART Transmitter (`uart_tx.v`)
- **Inputs**: `clk`, `en`, `start`, `tx_br`, `data[7:0]`
- **Outputs**: `done`, `busy`, `tx_out`
- **Function**: Sends start bit, 8 data bits, parity bit, and stop bit.

### 3. UART Receiver (`uart_rx.v`)
- **Inputs**: `clk`, `en`, `rx_br`, `rx_data`
- **Outputs**: `rx_out[7:0]`, `done`, `busy`, `error`
- **Function**: Detects start bit, receives 8-bit data, checks parity, validates stop bit.

### 4. Top Module (`uart_top.v`)
- **Inputs**: `clk`, `rst`, `en`, `start`, `tx_data[7:0]`
- **Outputs**: `rx_data[7:0]`, `tx_done`, `tx_busy`, `rx_done`, `rx_busy`, `rx_error`
- **Function**: Integrates baud generator, TX, and RX. TX output is looped back to RX input for verification.

---

## 🔧 Features
- Configurable baud rate.  
- Start, data, parity, and stop bit handling.  
- Error detection using parity and stop bit checks.  
- Testbenches for baud rate, TX, RX, and top-level verification.  

---

## 📊 Results (Simulation Output)
```
rx_data:00000000, rx_data:xxxxxxxx, tx_done:x, rx_done:x, tx_busy:x, rx_busy:x
rx_data:10110011, rx_data:xxxxxxxx, tx_done:0, rx_done:0, tx_busy:0, rx_busy:0
rx_data:10110011, rx_data:xxxxxxxx, tx_done:0, rx_done:0, tx_busy:1, rx_busy:0
rx_data:10110011, rx_data:xxxxxxxx, tx_done:0, rx_done:0, tx_busy:1, rx_busy:1
rx_data:10110011, rx_data:xxxxxxxx, tx_done:1, rx_done:0, tx_busy:0, rx_busy:1
rx_data:10110011, rx_data:10110011, tx_done:0, rx_done:1, tx_busy:0, rx_busy:1
rx_data:11001010, rx_data:10110011, tx_done:0, rx_done:1, tx_busy:0, rx_busy:0
rx_data:11001010, rx_data:10110011, tx_done:0, rx_done:0, tx_busy:1, rx_busy:0
rx_data:11001010, rx_data:10110011, tx_done:0, rx_done:0, tx_busy:1, rx_busy:1
rx_data:11001010, rx_data:10110011, tx_done:1, rx_done:0, tx_busy:0, rx_busy:1
rx_data:11001010, rx_data:11001010, tx_done:0, rx_done:1, tx_busy:0, rx_busy:1
```

---

## 🎯 Applications
- Debugging and console communication in microcontrollers.  
- Interfacing with GPS, GSM, Bluetooth, and Wi-Fi modules.  
- PC ↔ Embedded board communication.  
- Educational use for learning serial communication and protocol verification.  

---
