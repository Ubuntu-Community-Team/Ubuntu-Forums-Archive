---
title: "Read data from USB port"
date: 2011-06-21
forum: General Help
---

### Post by Haalle on 2011-06-21
Hi all,

I have just got a new USB device (Ventus W831 weather station) that I would like to get data from. I have used the program Weather Display with no luck, and now I just want to see if I can get the data stream from the USB port.

When I plugin the USB cable, the files /dev/hidraw0 and /dev/usb/hiddev0 appears. I have tried to use "sudo cat /dev/hidraw0" (for both files), but I get no output.

I am running 9.10, but I have also tried briefly in a live 11.04 - also without luck.
The output of lsusb is as follows:

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 0a5c:2101 Broadcom Corp. A-Link BlueUsbA2 Bluetooth
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 003: ID 1130:6801 Tenx Technology, Inc. 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 04f2:b013 Chicony Electronics Co., Ltd USB 2.0 Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

As far as I can tell, it is the Tenx Technology, Inc. which is my weather station. The last few lines of dmesg:

[17046.449181] usb 7-1: USB disconnect, address 2
[17046.451226] hidraw device with minor 0 doesn't exist
[17049.032099] usb 7-1: new low speed USB device using uhci_hcd and address 3
[17049.197451] usb 7-1: configuration #1 chosen from 1 choice
[17049.213544] generic-usb 0003:1130:6801.0003: hiddev96,hidraw0: USB HID v1.10 Device [ ] on usb-0000:00:1d.2-1/input0

Any help is much appreciated!

---

