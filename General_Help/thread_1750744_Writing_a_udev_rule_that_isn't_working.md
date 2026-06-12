---
title: "Writing a udev rule that isn't working"
date: 2011-05-05
forum: General Help
---

### Post by JMcFly on 2011-05-05
I have an FTDI IR transmitter on Mythbuntu 10.04 that I cannot get to work properly

udevadm info for the transmitter:
> john@AMDQuad:/dev$ udevadm info -q all -n /dev/ttyUSB0
P: /devices/pci0000:00/0000:00:12.1/usb4/4-2/4-2:1.0/ttyUSB0/tty/ttyUSB0
N: ttyUSB0
S: char/188:0
S: serial/by-path/pci-0000:00:12.1-usb-0:2:1.0-port0
S: serial/by-id/usb-FTDI_TTL232R_FTFAJ5VX-if00-port0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:12.1/usb4/4-2/4-2:1.0/ttyUSB0/tty/ttyUSB0
E: MAJOR=188
E: MINOR=0
E: DEVNAME=/dev/ttyUSB0
E: SUBSYSTEM=tty
E: ID_PORT=0
E: ID_PATH=pci-0000:00:12.1-usb-0:2:1.0
E: ID_VENDOR=FTDI
E: ID_VENDOR_ENC=FTDI
E: ID_VENDOR_ID=0403
E: ID_MODEL=TTL232R
E: ID_MODEL_ENC=TTL232R
E: ID_MODEL_ID=6001
E: ID_REVISION=0600
E: ID_SERIAL=FTDI_TTL232R_FTFAJ5VX
E: ID_SERIAL_SHORT=FTFAJ5VX
E: ID_TYPE=generic
E: ID_BUS=usb
E: ID_USB_INTERFACES=:ffffff:
E: ID_USB_INTERFACE_NUM=00
E: ID_USB_DRIVER=ftdi_sio
E: ID_IFACE=00
E: ID_VENDOR_FROM_DATABASE=Future Technology Devices International, Ltd
E: ID_MODEL_FROM_DATABASE=FT232 USB-Serial (UART) IC
E: DEVLINKS=/dev/char/188:0 /dev/serial/by-path/pci-0000:00:12.1-usb-0:2:1.0-port0 /dev/serial/by-id/usb-FTDI_TTL232R_FTFAJ5VX-if00-port0Whenever I run ["./rc5 34" from here]("http://www.huitsing.nl/irftdi/") as non-root, I get:
> unable to open ftdi device: -8 (inappropriate permissions on device!)When I run it with sudo, my IR transmitter blinks.

Trying to fix the permissions, I wrote /etc/udev/rules.d/20-ftdi.rules:
> ACTION=="add", SUBSYSTEM=="tty", ATTR{idProduct}=="6001", ATTR{idVendor}=="0403", MODE="666"But restarting udev and unplugging/hot plugging the transmitter does not fix the issue and the "unable to open device" error message returns when I try ./rc5 again.

Any ideas or suggestions on my 20-ftdi.rules file?

---

