---
title: "Problem with USB2 recognition and slow transfer rate (1-2 Mbps)"
date: 2010-03-24
forum: General Help
---

### Post by lucasg123 on 2010-03-24
Hi,

I am running Ubuntu 10.04 Beta on a Dell XPS m1530. I am a college student that has been using Ubuntu for about a semester now, so I have some basic knowledge. However, I am no expert. I purchased a 1TB USB2 Western Digital My Book Essential Hard Drive to store a few hundred gigs of programs and movies. I am unable to get it to be recognized as USB 2.0 and my transfer rates are (obviously) awful (1-2 mbps). If anybody has any experience with this problem I will be greatly appreciative! (and spread the word about how awesome Ubuntu is around campus:D)


Here is the lsusb output....

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 003: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 005: ID 046d:0a12 Logitech, Inc. 
Bus 005 Device 003: ID 1058:1110 Western Digital Technologies, Inc. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. OV2640 Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub




Thanks for any help you can offer. It is greatly appreciated!

---

### Post by DawieS on 2010-03-24
Try swapping the USB drive to another port (Bus 002 Device 001). According to the table it is currently unused. Also, it seems as if your motherboard supports only 2 x USB2, with the webcam using one at the moment. The rest are USB1. I have noticed the same on some of my desktop motherboards.

---

### Post by lucasg123 on 2010-03-24
I disconnected all my other usb devices minus the fingerprint reader and the webcam as they are internal components. I reconnected it to (Bus 002 Device 001) and it appears to now be recognized as usb 2.0. I guess thats a step in the right direction! Unfortunately however, the transfer rate has not increased. Any other Ideas?

lucas@lucas-laptop:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 008: ID 1058:1110 Western Digital Technologies, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. OV2640 Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


Thanks! :D

---

