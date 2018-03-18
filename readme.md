### Protocol specification
https://www.noo.com.by/assets/files/PDF/MTRF-64-USB.pdf

### Running on macOS
https://github.com/libusb/libusb/wiki/FAQ#how-can-i-run-libusb-applications-under-mac-os-x-if-there-is-already-a-kernel-extension-installed-for-the-device

```
kextstat | grep -i ftdi
sudo kextunload -b com.FTDI.driver.FTDIUSBSerialDriver
sudo kextunload -b com.apple.driver.AppleUSBFTDI
```

### Running on linux
To have access on device from common user add the next rule to udev. For example to /etc/udev/rules.d/50-noolite.rules next line:
```
ATTRS{idVendor}=="1027", ATTRS{idProduct}=="24577", SUBSYSTEMS=="usb", ACTION=="add", MODE="0666", GROUP="noolite"
```
Then add your user to noolite group:
```
sudo usermod <user> -aG noolite
```