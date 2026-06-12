---
title: "Dual-boot (win7/ubuntu) with ubuntu on an USB external drive"
date: 2011-08-20
forum: General Help
---

### Post by boyouzhao on 2011-08-20
I recently installed Ubuntu 10.10 on an usb external hard drive with my thinkpad t420. The installation was independent from windows (non-wubi). However, when I unplug the external drive the laptop wont boot. It always goes to the grub rescue command screen. I need to carry my laptop around without the external drive. Could anyone help me with this?

---

### Post by oldfred on 2011-08-20
Welcome to the forums.

You need to install grub to the external drive and set it to boot first in BIOS the when not plugged in it will boot the internal. You also need the windows boot loader or any windows like boot loader in the MBR of the internal drive.

This walks you thru the process.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive)

---

