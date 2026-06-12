---
title: "External hardware (USB-flash drive etc) not recognized, udev corrupted?"
date: 2010-08-29
forum: General Help
---

### Post by hjer0099 on 2010-08-29
Hello!

I'm a Ubuntu beginner encountering some problems after the latest upgrade to 10.04. I've done my best to find solutions on the web but wasn't successful. The problem is described below.

PROBLEM: After upgrading to Xubuntu 10.04 my system, while running, no longer automatically recognizes several external hardware devices including USB memory sticks and USB speakers. The devices run correctly if I connect them before the computer is turned on, but can only be unmounted from a terminal window. Once working, if they are removed, they can be reconnected again and are then automatically recognized.

ADDITIONAL INFORMATION: When a USB memory stick is connected AFTER start up, running dmesg yields

> 
[  524.580082] usb 1-3: new high speed USB device using ehci_hcd and address 2
[  524.716300] usb 1-3: configuration #1 chosen from 1 choiceand sudo fdisk -l

> Disk /dev/sda: 40,0 GB, 40007761920 byte
255 huvuden, 63 sektorer/spår, 4864 cylindrar
Enheter = cylindrar av 16065 · 512 = 8225280 byte
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Diskidentifierare: 0xa0cda0cd

    Enhet Start     Början        ****     Block    Id  System
/dev/sda1   *           1        4702    37768783+  83  Linux
/dev/sda2            4703        4864     1301265    5  Utökad
/dev/sda5            4703        4864     1301233+  82  Linux växling / SolarisApparently the memory stick is not associated with an sda device or the like.

SUGGESTED SOLUTION: On the #ubuntu IRC channel it was suggested I do a complete reinstallation. The consensus was that there was probably something wrong with udev.

SYSTEM: I run Xubuntu 10.04 on an acer TravelMate 2003LC laptop computer.

PROBABLY UNRELATED: Also after the upgrade to version 10.04 my analogue microphone is no longer recognized at all by the system while the analogue headphones run whenever connected.

---

