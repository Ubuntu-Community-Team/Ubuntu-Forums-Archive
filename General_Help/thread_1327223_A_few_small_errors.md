---
title: "A few small errors"
date: 2009-11-15
forum: General Help
---

### Post by Bearded-flower on 2009-11-15
I finally got 'round to upgrading to 9.10
Its all good 'n' fine i guess, exept there a few tiny niggeling errors.
The first is a biggie, It wont recognise USBs
and the second isnt so big. on my laptop fn + F5 makes the screen brighter, but as soon as i get to maximum it goes down one level.
Any ideas?
I really need to get the first one fixed i use a USB wireless dongle to conect to the net.

---

### Post by Bearded-flower on 2009-11-15
Bump

---

### Post by Bearded-flower on 2009-11-15
Anything? any ideas?

---

### Post by Rayve on 2009-11-15
I'm not sure, but a quick scan of the forum sounds like an update for Karmic today may have led to a bug regarding USB.  

Not sure if you've tried this, but apparently after updating printer drivers, a user was able to get their USB printer working by doing the following:

Disconnect printer from USB port and turn it off, restart your computer, log in and wait until everything loads, plug USB (make sure it's plugged correctly), turn on your printer after plugging USB, wait for system to recognize it automatically.....  printer and scanner work!!!  

See here: [http://ubuntuforums.org/showthread.php?t=1311713&highlight=USB+Karmic&page=4](http://ubuntuforums.org/showthread.php?t=1311713&highlight=USB+Karmic&page=4)

And regarding the bug: [http://ubuntuforums.org/showthread.php?t=1311865&highlight=USB+Karmic](http://ubuntuforums.org/showthread.php?t=1311865&highlight=USB+Karmic) (this post refers to a mouse problem, but the bug link [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/425755](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/425755) talks about any usb device)

---

### Post by Bearded-flower on 2009-11-19
Yeah no luck.
anything else i could do?

---

### Post by lavinog on 2009-11-19
post the output of dmesg after connecting a usb device.
also does lsusb report anything?

---

### Post by Bearded-flower on 2009-11-19
I dont get anything when i plug in a USB peripheral, 
I have found everyone with this problem has a MSI u100.
and this is what happened when i typed lsusb in terminal
```
Bus 001 Device 002: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

---

### Post by lavinog on 2009-11-19
> **Bearded-flower said:**
> I dont get anything when i plug in a USB peripheral, 
I have found everyone with this problem has a MSI u100.
and this is what happened when i typed lsusb in terminal
```
Bus 001 Device 002: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```
is the camera the device that you just plugged in?

---

### Post by Bearded-flower on 2009-11-19
No O.o
I had two thing plugged in. a LAN cable, and a USB mass storage device...

---

### Post by Bearded-flower on 2009-11-19
Any ideas about the flickering screen?
the brightness goes up...
the down...
then up...

---

### Post by jhann on 2009-11-19
Possibly check power managment? 
Mines set to always take the screen to a default level when on battery, even if I use the controls to set it to full after a second it'll drop down to minimum.

---

### Post by lavinog on 2009-11-19
bug report for brightness issue:
[https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/447764](https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/447764)

some usb bugs:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/435352](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/435352)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/455408](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/455408)
Look at post #13...it might help.

---

