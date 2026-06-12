---
title: "USB ports not working"
date: 2012-01-18
forum: General Help
---

### Post by KYHRL on 2012-01-18
Okay, so I'm a new user to Ubuntu, and I'm not all familiar with the terminal and the environment in general, although from what I've seen so far, I've enjoyed it very much.  Anyhow, I'm having a problem with my Compaq Presario SR1630NX.  The machine can't be that old, and it seems to be running Ubuntu 11.10 rather nicely, with the exception of the USB ports not working.  I discovered this problem when trying to get my NetGear WG111v2 adapter to work.  Basically, I've done just about everything Google searches have warranted me to do, and still none of my USB ports will work (I have 7 in total).  It would be much appreciated if anyone could please help me with this matter. 
NOTE: I am a beginner, so please keep the lingo simple.  Thank you very much!

-KYHRL

---

### Post by sudodus on 2012-01-18
Almost always the USB connections work with Ubuntu. Often there are problems with wireless adapters. So please try to attach some other hardware to your USB connections, for example a USB flash drive (pendrive or stick).

However, NetGear WG111v2 is a wireless adapter that is reported to work, at least with older versions of Ubuntu. Look at the following link.

[[COLOR="Red"]_https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear#USB_[/COLOR]]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear#USB")

---

### Post by debiant on 2012-01-18
Mine are not working too, both on a desktop PC runing Ultimate Edition 2.8 and a laptop running 11.04.

:confused:

---

### Post by sudodus on 2012-01-18
Do you mean the USB does not work with any equipment attached to it?

---

### Post by WasMeHere on 2012-01-18
Hi KYHRL

Please describe how you are running Ubuntu!

- from a live CD or USB drive
- installed to an own partition
- wubi install under Windows
- in a virtual machine (for example VirtulBox) under Windows

Have you tried another equipment (not only the wifi stick) in your USB connectors?

Have fun finding out :-)
Olle

---

### Post by KYHRL on 2012-01-18
I have totally uninstalled Windows XP and replaced it with Ubuntu 11.10... Ha Ha, I jump in head first I guess.

---

### Post by KYHRL on 2012-01-18
And to answer some of the other questions... NONE of the USB devices I have plugged in work on ANY of the ports.

---

### Post by WasMeHere on 2012-01-19
> **KYHRL said:**
> And to answer some of the other questions... NONE of the USB devices I have plugged in work on ANY of the ports.
Did USB work on that computer with Windows?

Try the following commands (to see what output you get about USB) ```
gksudo lshw | less
```
```
lsusb
```
when at least one USB device is connected

---

### Post by xyzzyman on 2012-01-19
> **KYHRL said:**
> The machine can't be that old

It's over 5 years old, so technically.... That means that performance aside, the USB ports should be detected. Maybe you should verify they haven't been disabled in the BIOS? When was the last time anything has worked in the USB port?

---

### Post by KYHRL on 2012-01-19
Okay, for starters, when I do lsusb, it says, "Unable to initialize libusb: -99" I get a lot of output for the other command, but I'm not sure what I'm looking for.

---

### Post by KYHRL on 2012-01-19
Oh, and when I do the other command, I notice that all of the USB things are listed as [UNCLAIMED]

---

### Post by WasMeHere on 2012-01-20
Something is wrong or missing in your Ubuntu 11.10 installation. Maybe it would work better with an older version of Ubuntu, since your computer was released 2005. ***I suggest that you download the iso file of Ubuntu 10.04.3 and make a bootable CD or USB drive. Don't install at once, only run a live session to test how it works!***

Of course you can also run Ubuntu 11.10 live, and hope that is works. In that case, something happened to the USB drivers during or after installation.

---

### Post by KYHRL on 2012-01-20
I will try that out and let you know how it goes.

---

### Post by rmarti on 2012-01-20
I had similar problem with my USB. After checking the hwinfo the usb port was disable. 

1.  (hwinfo –short)Command will displays the hardware

2.  My computer didn't had hwinfo installed a message display to download hwinfo.

3. (sudo echo on)Command will enable the usb port

---

