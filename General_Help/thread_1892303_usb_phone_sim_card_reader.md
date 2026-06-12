---
title: "usb phone sim card reader"
date: 2011-12-07
forum: General Help
---

### Post by Robbyx on 2011-12-07
Has anyone been able to use a cheap sim reader? It is not being seen as a temporary storage device in my file manager. I had hoped that I would be able to see it in the file manager, as I can a memory stick,  and look at the contents of the sim. Nothing shows up in the file manager.

```
robin@robin-EP35-DS3L:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 051d:0002 American Power Conversion Uninterruptible Power Supply
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 050: ID 046d:c051 Logitech, Inc. G3 (MX518) Optical Mouse
Bus 001 Device 048: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port
Bus 001 Device 047: ID 0d8c:000c C-Media Electronics, Inc. Audio Adapter
Bus 001 Device 046: ID 1a40:0101 TERMINUS TECHNOLOGY INC. USB-2.0 4-Port HUB
Bus 001 Device 007: ID 046d:c315 Logitech, Inc. Classic New Touch Keyboard
Bus 001 Device 006: ID 046d:0990 Logitech, Inc. QuickCam Pro 9000
Bus 001 Device 003: ID 1a40:0101 TERMINUS TECHNOLOGY INC. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Device 48 is the sim card reader.

I also tried accessing it via Virtual box. The device shows up under the USBs and I have been able to connect to the reader, but it shows no sms messages as being present. I have too many there and am trying to save them to disk before deleting them to make more space on the phone. So the software supplied is not seeing the messages that are on the machine.

Robin

Robin

---

