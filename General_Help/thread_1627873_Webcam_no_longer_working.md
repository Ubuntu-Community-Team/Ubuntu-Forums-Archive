---
title: "Webcam no longer working"
date: 2010-11-21
forum: General Help
---

### Post by cfree220 on 2010-11-21
Hi all,

I'm having some trouble with my webcam. When I try to launch Cheese, or Camorama (or any application which wants to use the webcam), it comes up with no device found.

It was working a few days ago, and I can see the webcam when I run lsusb:

```
cfreeman@Ulysses:~$ lsusb
Bus 007 Device 009: ID 0a5c:4503 Broadcom Corp. 
Bus 007 Device 008: ID 0a5c:4502 Broadcom Corp. Keyboard (Boot Interface Subclass)
Bus 007 Device 007: ID 413c:8126 Dell Computer Corp. Wireless 355 Bluetooth
Bus 007 Device 006: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 1058:1100 Western Digital Technologies, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. OV2640 Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

The computer is a Dell XPS M1530 running 64 bit Ubuntu 10.10

Thanks in advance!

---

### Post by no2498 on 2010-11-22
if mine acts up i reset v4l

hope it helps you


open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

cheese has a nice help file look in the faq's



if gstreamer is not loaded it needs the
good,bad,ugly, and 10 installed

---

### Post by cfree220 on 2010-11-23
Thanks. This worked for me once, but then the problem returned (quickly) and I couldn't get it working again.

---

### Post by no2498 on 2010-11-23
if your not using 64 bit try this program wxcam

[http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)

---

### Post by cfree220 on 2010-11-29
Alas, I do use 64 bit.

---

### Post by no2498 on 2010-11-29
you try the gstreamer-properties again

---

### Post by cfree220 on 2010-11-29
Well, it's an intermittent problem. It worked fine today.

---

### Post by no2498 on 2010-11-29
i have had to do it over 10 times in/on 10.04

---

