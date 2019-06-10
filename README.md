# Install SSD1306-based OLED Display on Raspberry Pi 3 

## Requirements
 * Raspberry Pi 3
 * Raspbian Stretch Lite
 * AZ-Delivery 0,96 Zoll I2C OLED Display 

## Update modules to load at boot time
```console
sudo nano /etc/modules
```

Add the following lines:
```console
i2c-bcm2708
i2c-dev
```

## Update boot config 
```console
sudo nano /boot/config.txt
```

Add or uncomment these lines (search with [strg]+[w]):
```console
dtparam=i2c_arm=on
dtparam=i2c1=on
```

## Install Git and Python 
```console
sudo apt-get update
sudo apt-get upgrade -y
sudo apt-get install libssl-dev libffi-dev git python python-dev python-pip python-pil python-smbus -y
```

## Install dependencies with pip
```console
sudo pip install Adafruit-SSD1306
```

## Test
Reboot your device with `sudo shutdown -r now`.

Then run the examples:
```console
cd /tmp
git git@github.com:plakna/raspberry-pi-oled-display-ssd1306.git
cd examples

python animate.py
python buttons.py
python image.py
python shapes.py
python stats.py
```