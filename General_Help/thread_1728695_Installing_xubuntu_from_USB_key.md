---
title: "Installing xubuntu from USB key"
date: 2011-04-14
forum: General Help
---

### Post by onlycuteusernames on 2011-04-14
Hey... I have an MSI netbook with a non-functioning version of Ubuntu (the GUI is GNOME, and currently not working) and I'm trying to replace that with xubuntu. For whatever reason, I cannot get the system to mount the USB key, which currently has nothing on it except for the xubuntu .iso file. My computer is encrypted with sda5_crypt, which comes up and demands a password just after the MSI boot screen. I assume I need to press some kind of key before the sda5_crypt screen, but I'm not sure which button that is. There is an option of pressing F11 for "boot menu", and from there I can select "flash card", but it doesn't do me any good to do that.

Any help is appreciated!

---

### Post by deathadder on 2011-04-14
Hi,

Sorry I'm not entirely sure what you're asking. Can you not boot of the USB drive or does the current install not recognise it?

If you can not boot off it, apart from having to change the boot order, you wouldn't be able to boot up the Xubuntu install but just placing the ISO image onto the disk. You'll need write the ISO file to the USB stick, there's instructions on the wiki: [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

If it doesn't work after doing that you'll need to get into the BIOS and change the boot order, not entirely sure what key you'll need to press but some common ones are: Del, Esc, F11

If you Google you're netbook version you should be able to find a manual that tells you how to do it.

---

### Post by XubuRoxMySox on 2011-04-14
[This page]("https://help.ubuntu.com/community/Installation") offers some alternate installation methods! Including network installation.

-Robin

---

### Post by EdwardR on 2011-04-26
You can't just copy the iso file onto the usb stick, you need to use a program to extract the individual files and directories from within the iso file and install them onto the usb stick.  See the following [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by C.S.Cameron on 2011-04-26
Try using UNetbootin to make your Live USB.

---

