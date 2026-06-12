---
title: "Can't boot"
date: 2011-12-15
forum: General Help
---

### Post by anime4049 on 2011-12-15
I trying to intall Ubuntu trough usb flash drive (kingston 8gb) , but all I get is a blank screen with a "_" ticking. :confused:   , and yes I can't load it into cd/dvd/etc since it a netbook. any one know what the problem and how to solve it?

---

### Post by Mark Phelps on 2011-12-15
How did you create the flash drive? Did you just copy the files from an Ubuntu desktop CD to the drive?

You need to use unetbootin to make a bootable USB install.

---

### Post by seawolf167 on 2011-12-15
Echoing Mark Phelps' post - is your USB bootable or did you simply copy/paste the downloaded Ubuntu .iso image file onto the USB drive?

Again as previously suggested, you'll want to use UNetBootin. You can download it from [here]("http://unetbootin.sourceforge.net/"), and installation instructions are [here]("http://unetbootin.sourceforge.net/#install"). Additionally, since this is a Live USB, you can add persistence, so that changes you make while booted in the Live environment are saved and carried over to future live environments.

---

### Post by grahammechanical on 2011-12-15
Did you see any kind of message? Such as something like isolinux loading? The live CD/USB loads a form of Linux and then a Graphical User Interface. You may be getting a Linux command prompt because the live CD/USB is having trouble detecting the video capabilities of your graphics adapter.

This link has a lot of information. Look for settings you can change in order to get a working live USB.

[http://ubuntuforums.org/showthread.php?t=1743535]("http://ubuntuforums.org/showthread.php?t=1743535")

Regards.

---

### Post by anime4049 on 2011-12-15
> **Mark Phelps said:**
> How did you create the flash drive? Did you just copy the files from an Ubuntu desktop CD to the drive?

You need to use unetbootin to make a bootable USB install.
Yes I use unetbootin. (load from ISO)

> **grahammechanical said:**
> Did you see any kind of message? Such as something like isolinux loading? The live CD/USB loads a form of Linux and then a Graphical User Interface. You may be getting a Linux command prompt because the live CD/USB is having trouble detecting the video capabilities of your graphics adapter.

This link has a lot of information. Look for settings you can change in order to get a working live USB.

[http://ubuntuforums.org/showthread.php?t=1743535]("http://ubuntuforums.org/showthread.php?t=1743535")

Regards.

No , no such thing , I only went to bootscreen on the bios , pick usb , and then blank screen with as I mention above.

---

