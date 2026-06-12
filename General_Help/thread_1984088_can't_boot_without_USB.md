---
title: "can't boot without USB"
date: 2012-05-21
forum: General Help
---

### Post by koloss on 2012-05-21
[SIZE=2]Hey guys
[/SIZE]  [SIZE=2]I am using Sylvania gnet 13001 which is running Ubuntu 12 but it can't boot without the USB flash driver (I installed Ubuntu from the USB flash driver , and I after it boot I can remove the driver and everything works fine could anybody help me to make it boot by itself[/SIZE]

---

### Post by oldfred on 2012-05-21
Grub defaults to installing the boot to the MBR of sda. Some computers promote the USB flash drive to sda, where most computers make it sdb or later.

You need to install grub to the MBR of the hard drive which may not be sda.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive)

---

### Post by 89j on 2012-08-10
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive)

hi i did what it says on the above link but it says no partition active when i try to reboot without usb..

---

### Post by 89j on 2012-08-10
p.s. im using a compaq mini 702EA if thats relevant.

i replace a windows xp os using the usb installer

---

### Post by oldfred on 2012-08-11
Oldfred may have given some bad advice. Shock! The link is to add a boot loader to the external drive, not an internal drive.

Easiest is to use Boot-Repair.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

Or manually.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 and later with grub2) by talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

---

