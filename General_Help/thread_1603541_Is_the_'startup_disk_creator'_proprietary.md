---
title: "Is the 'startup disk creator' proprietary?"
date: 2010-10-22
forum: General Help
---

### Post by Scooter_X on 2010-10-22
Hey all, I'm trying to make a live USB of openSUSE from the 'startup disk creator' in Ubuntu. I wanna try it and see what it's like. As well as Fedora and gOS. As soon as the downloads for Fedora and gOS finish I'll try making the startup disk with 'startup disk creator' for each of those. But my problem is that I tried openSUSE and I select the .iso and it doesn't do anything.... I would imagine it should work with any old .iso, right? Or no? Can I only make an ubuntu startup disk with it?

EDIT: Fedora doesn't work either

EDIT again: Yea, requirements state that I can only make a USB startup disk of Ubuntu desktop edition

---

### Post by oracle2b on 2010-10-22
Use [unetbootin]("http://unetbootin.sourceforge.net/") instead.

---

### Post by beew on 2010-10-22
> **Scooter_X said:**
> Hey all, I'm trying to make a live USB of openSUSE from the 'startup disk creator' in Ubuntu. I wanna try it and see what it's like. As well as Fedora and gOS. As soon as the downloads for Fedora and gOS finish I'll try making the startup disk with 'startup disk creator' for each of those. But my problem is that I tried openSUSE and I select the .iso and it doesn't do anything.... I would imagine it should work with any old .iso, right? Or no? Can I only make an ubuntu startup disk with it?

EDIT: Fedora doesn't work either

EDIT again: Yea, requirements state that I can only make a USB startup disk of Ubuntu desktop edition

Fedora has its own live usb creator which you can install in Ubuntu.[http://ubuntuforums.org/showthread.php?t=1527260&page=3 ]("http://ubuntuforums.org/showthread.php?t=1527260&page=3")

If you want to create live usb for other distros (including Fedora) in Ubuntu you may want to try Multiboot  [http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)

> **oracle2b said:**
> Use [unetbootin]("http://unetbootin.sourceforge.net/") instead.


Unetbootin doesn't support persistence so it would be pretty near useless unless you just want to make the usb for installation or doing things like onliine banking so you don't want to save any setting.

---

### Post by C.S.Cameron on 2010-10-22
Different distros use different techniques for making Live USBs persistent.
There is not a USB installer out there that makes persistent drives for more than one distro, (and it's remix).

You can do a Full install of any distro.
Unplug your HDD, insert the USB drive and run install from the Live CD or Multiboot USB.

I have had success using MultiBootUSB for making non persistent Live USBs:

[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)

---

### Post by kalos on 2010-10-23
You could try [unetbootin]("http://unetbootin.sourceforge.net/"): "UNetbootin allows you to create bootable Live USB drives for Ubuntu, Fedora, and other Linux distributions without burning a CD."

---

