---
title: "Boot to operating system selection- urgent!"
date: 2011-01-27
forum: General Help
---

### Post by Sankou on 2011-01-27
I just decided to put ubuntu 9.01 on my spare flash drive earlier today. I accidental picked the wrong option during the install though. I made it to where it boots to the grub and then I pick my operating system. Windows 7 is install on my hard drive. I don't want to boot to the grub! If I remove my flash drive, my computer is rendered useless! I want to boot the windows operating system selection menu. Please help, I can't figure this out at all....

---

### Post by Foxheadz on 2011-01-27
GRUB is a boot loader. It let's you pick which os you want to boot from. If you have any problems this should be able to help [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by oldfred on 2011-01-27
You can use windows to reinstall a windows boot loader and from Ubuntu reinstall grub to the external drive.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Full set of instructions for exactly your problem, using just Ubuntu liveCD and lilo boot loader to boot windows.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive)

---

