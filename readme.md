# 🌈 Mitsubishi WF-RAC Air Conditioner Control Script

It's YOUR device on YOUR LAN, so you should be able to control it ;)

This script allows interfacing with the Mitsubishi Heavy Industries air conditioners equipped with the WF-RAC module.


## Features

- Retrieve current air conditioner status.
- Set operational parameters:
  - Power state (On/Off).
  - Preset temperature.
  - Airflow level.
  - Wind direction (Up/Down and Left/Right).
  - Operation mode (Auto, Cool, Heat, Fan, Dry).
- Register devices with the air conditioner.
- Discover air conditioner devices on the network.

## Requirements

- Python 3.7 or higher
- Required Python libraries:
  - `requests`
  - `zeroconf`

Install the required libraries using:
```bash
pip install -r requirements.txt
```

## Usage

### 1. Register with the Air Conditioner
Before you can use the `set` functions to control your air conditioner, you **must register the device** with the script.

```bash
python aircon.py register <IP_ADDRESS>
```

This step is required only once to establish communication with the air conditioner. Replace `<IP_ADDRESS>` with your air conditioner's IP address.

### 2. Get Device Info
Retrieve the air conditioner's ID and MAC address.

```bash
python aircon.py info <IP_ADDRESS>
```

### 3. Get Air Conditioner Status
Retrieve the current status of the air conditioner.

```bash
python aircon.py status <IP_ADDRESS>
```

### 4. Set Air Conditioner Parameters
After registering the device, you can set various parameters for the air conditioner. You can combine multiple options in a single command.

```bash
python aircon.py set <IP_ADDRESS> [OPTIONS]
```

#### Options:
- `--on`: Turn the air conditioner on.
- `--off`: Turn the air conditioner off.
- `--temp <TEMPERATURE>`: Set the preset temperature (e.g., `25.5`).
- `--airflow <LEVEL>`: Set airflow level (0=Auto, 1=|, 2=||, 3=|||, 4=||||).
- `--wind-ud <POSITION>`: Set wind direction (Up/Down) (0=Auto, 1, 2, 3, 4).
- `--wind-lr <POSITION>`: Set wind direction (Left/Right) (0=Auto, 1-7).
- `--mode <MODE>`: Set operation mode (0=Auto, 1=Cool, 2=Heat, 3=Fan, 4=Dry).

#### Example:
- Turn on the air conditioner in "Cool" mode at 24°C:
  ```bash
  python aircon.py set <IP_ADDRESS> --on --temp 24 --mode 1
  ```

- Set airflow to maximum and wind direction to auto:
  ```bash
  python aircon.py set <IP_ADDRESS> --airflow 4 --wind-ud 0 --wind-lr 0
  ```



---

**Disclaimer**: Use this script at your own risk. The author assumes no responsibility for issues caused by this tool.

