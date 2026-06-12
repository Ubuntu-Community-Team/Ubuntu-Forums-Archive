---
title: "waiting for device to settle before scanning"
date: 2010-03-24
forum: General Help
---

### Post by blahheh on 2010-03-24
I'm trying to access my memory card through my phone (Samsung Alias 2) and well it seems to get stuck on something. End of dmesg:

[517493.330027] usb 2-6: new full speed USB device using ohci_hcd and address 43
[517493.559801] usb 2-6: configuration #1 chosen from 1 choice
[517493.569742] scsi25 : SCSI emulation for USB Mass Storage devices
[517493.569802] usb-storage: device found at 43
[517493.569803] usb-storage: waiting for device to settle before scanning


lsusb:

Bus 002 Device 045: ID 05c6:1000 Qualcomm, Inc.
Bus 002 Device 002: ID 062a:0000 Creative Labs Optical mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


Any ideas? I saw a fix for something just like this for digital cameras/mp3 players involving libgphoto2-patch0, but that didn't  work for me.

Thanks!
-Chris

---

