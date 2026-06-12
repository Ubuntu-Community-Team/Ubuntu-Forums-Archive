---
title: "xsane suddenly not detecting scanner"
date: 2006-05-22
forum: General Help
---

### Post by poiuytr on 2006-05-22
I can't think of anything I did which might have caused this, but xsane is suddenly not detecting my usb scanner (HP ScanJet 3300C), which has previously always worked fine in Ubuntu 5.10.  I'm not sure what to do to diagnose the problem. If I run xsane I get "no devices available."

I i run sane-find-scanner I get:

"No USB scanners found. If you expected something different, make sure that
  # you have loaded a driver for your USB host controller and have installed a
  # kernel scanner module."

I tried re-installing xsane, and that's as far as I have gotten.

Ideas?  Thanks.

---

### Post by Zimmer on 2006-05-24
[QUOTE=poiuytr]I can't think of anything I did which might have caused this, but xsane is suddenly not detecting my usb scanner (HP ScanJet 3300C), which has previously always worked fine in Ubuntu 5.10.  I'm not sure what to do to diagnose the problem. If I run xsane I get "no devices available."

I i run sane-find-scanner I get:

"No USB scanners found. If you expected something different, make sure that
  # you have loaded a driver for your USB host controller and have installed a
  # kernel scanner module."

I tried re-installing xsane, and that's as far as I have gotten.

Ideas?  Thanks.[/QUOTE]
Try plugging the device in properly, and/or testing it connects on another machine. I suffered the same thing for a half hour or so of software troubleshooting only to find the USB connector was not fully inserted in the scanner :)

Try another USB device in the same USB slot, in case you have a problem there

---

### Post by poiuytr on 2006-05-24
Wow, Zimmer, thank you so much.  Often times it is the most obvious thing that we forget to check.

Following your suggestion I tried using another USB slot on my computer, and that slot is working fine for whatever USB devices I connect to it, a scanner, a camera or whatever.  But the slot I had the scanner plugged into is dead, for any device.

I guess I have some Googling to do, and some searching in the Ubuntu forums to see if anyone else has ever encountered this before.  

I've never heard of a USB slot going "bad."  Any ideas on what causes this, most typically?  A hardware issue, or software?

---

### Post by Zimmer on 2006-05-25
> I've never heard of a USB slot going "bad." Any ideas on what causes this, most typically? A hardware issue, or software?
Can't help you there, I'm afraid. I have never experienced any problems with the USB ports themselves, only the connecting leads...The Device MAnager may provide clues as to the condition/recognition of the USB controller..and narrow down the search for the root of the problem

---

### Post by from_beyond on 2006-07-07
ubuntu@ubuntu-desktop:~$ sane-find-scanner
ubuntu@ubuntu-desktop:~$ sudo apt-get install sane-utils

Adding saned group and user...

ubuntu@ubuntu-desktop:~$ sudo sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x03f0 [HP], product=0xc202 [Photosmart 8200 series]) at libusb:005:004
found USB scanner (vendor=0x03f0 [Hewlett-Packard], product=0x1b05 [HP Scanjet Scanner], chip=GL841) at libusb:005:003
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.
closer-----

---

