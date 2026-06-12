---
title: "Webcam stopped working"
date: 2010-11-21
forum: General Help
---

### Post by Meshaal on 2010-11-21
I searched through the related threads, but couldn't find any that answered my question.

I've used Ubuntu for several months, and my laptop's built-in webcam has worked wonderfully in it during that time.  However, today I went to use it (using kdenlive), and got the error "Cannot read from device /dev/video0".  I downloaded Camorama, which gave the same error.

As I said, it's worked fine up until today.  I'm sort of at a loss.  I'm not sure how to determine the exact model number, but it's a Dell Inspiron 1525 Integrated Webcam.

---

### Post by randumnumber on 2010-11-21
I don't have much experience with Webcams, but perhaps you should navigate to /dev to ensure that the video0 device is still in existence. If it has a different name or doesn't exist then the programs you are using wont be able to find it. If the device name has changed to say video1 then you should edit the .conf file of the program you are trying to use so it knows where to look for the device.

This is the first thing i would check, if i had this issue.

---

### Post by Meshaal on 2010-11-21
I checked in there, and couldn't find anything which remotely resembled video0.  I'm assuming it had to be there before for the device to work, but I don't know what could have caused it to disappear or how to recover it, if that's the issue.

---

### Post by randumnumber on 2010-11-21
Yep thats your problem alright. post the output of these commands.
```

lspci

```
and
```

lsusb

```

This will list all the devices on your computer, then we can try to work from there.

---

### Post by Meshaal on 2010-11-21
> **randumnumber said:**
> Yep thats your problem alright. post the output of these commands.
```

lspci

```
and
```

lsusb

```

This will list all the devices on your computer, then we can try to work from there.
Thanks for your help. lspci outputs:
```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
02:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
```
and lsusb gives
```
Bus 007 Device 004: ID 0a5c:4503 Broadcom Corp. 
Bus 007 Device 003: ID 0a5c:4502 Broadcom Corp. 
Bus 007 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a/HP M-UV96 Optical Wheel Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. OV2640 Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

### Post by randumnumber on 2010-11-21
try doing this. it probably wont work but its a common issue with your laptop. (at least in older versions of buntu)

[http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Built_In_Digital_Camera_Does_Not_Work](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Built_In_Digital_Camera_Does_Not_Work)

---

### Post by randumnumber on 2010-11-21
Here is a bug report for people who upgraded and had a problem with your type of webcam. Some say after a a reboot it works, but from resume it does not.  

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/459586](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/459586)

read over see if anything helps...ill keep diging

---

### Post by randumnumber on 2010-11-21
Ok i think i found the solution....i hope. 

```

$ sudo rmmod uvcvideo
$ sudo modprobe uvcvideo

```

If that doesnt work try running this script
```

#!/bin/sh

# A script to re-enable OmniVision OV2640 Webcam

# Unload the modules first
rmmod uvcvideo gspca_ov519 gspca_main vloopback videodev v4l1_compat v4l2_common

# Reload the required modules
modprobe gspca_ov519
modprobe v4l1_compat
modprobe v4l2_common
modprobe uvcvideo

# Exit

exit 0

```


I dont know your level of skill, if you dont know how to run a script.


```

pico myscript.sh

```
COPY TEXT TO THIS
then hit ctrl+o then ctrl+x
then at the shell prompt
```

chmod 775 myscript.sh   #this makes it execuitble
./myscript.sh           # this executes it

```

---

### Post by Meshaal on 2010-11-21
Sorry for the delay, my email notification was being buggy.  The first part of your most recent post seems to have done the trick.  Thanks for your support, I'd be lost without it :D

---

### Post by randumnumber on 2010-11-21
please mark it as solved. no problem, believe me, i rely on other people for my issues too. lease i can do is help others.

---

