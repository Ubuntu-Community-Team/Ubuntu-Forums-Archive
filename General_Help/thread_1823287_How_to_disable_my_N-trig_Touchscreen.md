---
title: "How to disable my N-trig Touchscreen"
date: 2011-08-11
forum: General Help
---

### Post by tamer_radi on 2011-08-11
I have Hp touch-smart tablet pc -which sucks btw-
lately the touch gone crazy and started clicking randomly all over the screen !!

So, I wanna disable it for now, I searched for a tool to configure my N-trig device, but I didn't find any.

Anyway, I thought since the device is connected via USB, I could disable it, but I don't know how

here is the output of lsusb
```
~$ lsusb
Bus 007 Device 003: ID 1b96:0001 N-Trig Duosense Transparent Electromagnetic Digitizer
Bus 007 Device 002: ID 08ff:1600 AuthenTec, Inc. AES1600
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 1bcf:05c5 Sunplus Innovation Technology Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04f2:b132 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 04e8:6033 Samsung Electronics Co., Ltd 
Bus 001 Device 004: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 003: ID 1a40:0101 TERMINUS TECHNOLOGY INC. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


```
and 
```
 lsusb -t
6-1:1.2: No such file or directory
6-1:1.3: No such file or directory
7-1:1.0: No such file or directory
7-2:1.2: No such file or directory
/:  Bus 07.Port 1: Dev 1, Class=root_hub, Driver=ohci_hcd/2p, 12M
    |__ Port 1: Dev 2, If 0, Class=vend., Driver=, 12M
    |__ Port 2: Dev 3, If 0, Class=HID, Driver=usbhid, 12M
    |__ Port 2: Dev 3, If 1, Class=HID, Driver=usbhid, 12M
    |__ Port 2: Dev 3, If 2, Class=>ifc, Driver=, 12M
/:  Bus 06.Port 1: Dev 1, Class=root_hub, Driver=ohci_hcd/3p, 12M
    |__ Port 1: Dev 2, If 0, Class='bInterfaceClass 0xe0 not yet handled', Driver=btusb, 12M
    |__ Port 1: Dev 2, If 1, Class='bInterfaceClass 0xe0 not yet handled', Driver=btusb, 12M
    |__ Port 1: Dev 2, If 2, Class=vend., Driver=, 12M
    |__ Port 1: Dev 2, If 3, Class=app., Driver=, 12M
/:  Bus 05.Port 1: Dev 1, Class=root_hub, Driver=ohci_hcd/3p, 12M
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=ohci_hcd/3p, 12M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=ohci_hcd/3p, 12M
    |__ Port 1: Dev 2, If 0, Class=HID, Driver=usbhid, 1.5M
    |__ Port 1: Dev 2, If 1, Class=HID, Driver=usbhid, 1.5M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/6p, 480M
    |__ Port 2: Dev 2, If 0, Class='bInterfaceClass 0x0e not yet handled', Driver=uvcvideo, 480M
    |__ Port 2: Dev 2, If 1, Class='bInterfaceClass 0x0e not yet handled', Driver=uvcvideo, 480M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/6p, 480M
    |__ Port 2: Dev 3, If 0, Class=hub, Driver=hub/4p, 480M
        |__ Port 3: Dev 5, If 0, Class=stor., Driver=usb-storage, 480M
    |__ Port 4: Dev 4, If 0, Class=stor., Driver=usb-storage, 480M

```

I am using Ubuntu Natty 32-bit

---

### Post by Favux on 2011-08-11
Hi tamer_radi,

I doubt you need to disable touch.  Likely you just need to recalibrate the digitizer.  Calibration as in eliminating noise or "degaussing" rather than getting coordinates.  See the stuff on Rafi's calib.c and calibration in Miscellaneous Notes on the [N-Trig HOW TO]("http://ubuntuforums.org/showthread.php?t=1252492").

If you do want to turn touch off see "3) Turning touch on and off" on the same HOW TO.  Magick Rotation also let's you turn touch off.

---

### Post by tamer_radi on 2011-08-12
Wow ... Magick Rotation is what I am searching for
Thank you very much, I wonder why such program isn't in Ubuntu Software center. I'll consider Calibration later.
Thanks very much.

---

