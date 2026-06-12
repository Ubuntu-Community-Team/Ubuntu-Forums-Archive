---
title: "Blackberry used to connect"
date: 2011-05-17
forum: General Help
---

### Post by jolts89 on 2011-05-17
Hey, I have a Blackberry Curve 8310 v4.5 with a 4Gb SDHC memory. I used to be able to connect to Ubuntu 11.04 with it to add and remove files. When I connected it a usb icon with the name RIM would pop up on the desktop and in the places menu. One day I plugged in my Blackberry and it didn't pop up. I've searched everywhere for a solution, but haven't had any success. I know that my USB hardware works because I can plug in a USB flash drive, and it shows up.

lsusb:
```
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 006: ID 0fca:0001 Research In Motion, Ltd. Blackberry Handheld
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a/HP M-UV96 Optical Wheel Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 008: ID 08ec:0016 M-Systems Flash Disk Pioneers Kingston DataTraveler U3
Bus 001 Device 003: ID 058f:6377 Alcor Micro Corp. Multimedia Card Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```fdisk -l:
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009048d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       59682   479393792   83  Linux
/dev/sda2           59683       60802     8990721    5  Extended
/dev/sda5           59683       60802     8990720   82  Linux swap / Solaris

```The codes were entered with the Blackberry connected to the computer.
-Media Card Support: ON
-Encryption Mode: None
-Mass Storage Mode Support: On
-Auto Enable Mass Storage Mode When Connected: Prompt
plz Help!

---

