---
title: "NEC USB 3.0 µPD720200 Driver"
date: 2011-05-25
forum: General Help
---

### Post by jamgood96 on 2011-05-25
First off, hi to everyone. I'm a rather new Linux user (as of the last 5 hours). I just built a small computer based on the E350N-USB3 motherboard from GigaByte. They don't provide any drivers for linux installs, and say to consult the chipset vender's for drivers. I got ones for the audio and LAN (but have yet installed them). The motherboard has USB 3.0, and based on gigabyte's website, it's the NEC usb 3.0 µPD720200. I can't seem to find any drivers for this. Are there even drivers available for this? Am I going down the wrong path? Thanks!

---

### Post by linuxinstalledfromhdd on 2011-05-25
You should download and create either an installation disc of Ubuntu 10.10 or a live stick USB that is Bootable of Ubuntu.   That way you can boot from that USB drive and check it out.

---

### Post by Objekt on 2011-08-08
I need to know the answer too.  Installing Ubuntu has nothing to do with it.

I recently put a USB 3.0 card in my machine.  It's connected by means of a PCI Express 2.0 1x slot, and uses the common NEC µPD720200 USB 3.0 controller.  However, when I connect a USB 3.0 drive (Western Digital MyBook Essential 1130), Disk Utility shows it as a USB 2.0 device.

I know the kernel I'm using (2.6.32-33-generic-pae) should support USB 3.0, so what is the problem?

Oddly, Gparted does not see the 3.0 TB drive at all.  It is just one big NTFS volume, but does not show up.  Normally, there isn't a problem with USB devices appearing in Gparted.

I get full USB 3.0 speeds when running Windows 7, so I know the drive, card, and cable are all good.

(Current Ubuntu version is shown in my profile at left.)

---

### Post by Objekt on 2011-08-09
FWIW, here is my lsusb output:
```
user4@user4-desktop:~$ sudo lsusb
[sudo] password for user4: 
Bus 009 Device 002: ID 1058:1130 Western Digital Technologies, Inc. 
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 002: ID 046d:c01b Logitech, Inc. MX310 Optical Mouse
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 003: ID 050d:0815 Belkin Components Nostromo n52 HID SpeedPad Mouse Wheel
Bus 007 Device 002: ID 06a3:8020 Saitek PLC 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 003: ID 04f2:0963 Chicony Electronics Co., Ltd 
Bus 006 Device 002: ID 1267:0103 Logic3 / SpectraVideo plc G-720 Keyboard
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

I am having almost exactly the same problem in Windows 7.  The ports worked at USB 3.0 speed for the first day or so, but several reboots and power cycles later, they will only work as USB 2.0 ports.

I suppose it's possible the USB 3.0 card is simply defective.  Or it could be the cable, though it's hard to see how it would stop working spontaneously.  I've checked and re-checked physical connections several times, and everything seems to be as it should.

---

### Post by Objekt on 2011-08-17
Confirmed: it was the MyBook enclosure that was the problem, or else the cable supplied with it.

Regardless of which one was at fault, I got a solid USB 3.0 connection as soon as I transferred the 3 TB drive to a new enclosure.  So there is nothing wrong with the USB 3.0 card after all.

---

