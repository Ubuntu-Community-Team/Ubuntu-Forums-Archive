---
title: "Grub Bootloader gone"
date: 2010-04-18
forum: General Help
---

### Post by KaiJordanDay on 2010-04-18
Ok. I installed ubuntu 9,04 a few months back. Upgraded to 9.10.

Needed windows programs, so installed (but overwrote grub with windows bootloader)

Now, I want to re access this ubuntu partition.

Disk 0
- Windows Bootloader
- Windows 7

Disk 1
- Storage
- Linux
- 4GB Partition. Not sure what it is.


How can I reinstall Grub, with both Linux and Windows 7 on the menu.

---

### Post by KaiJordanDay on 2010-04-18
Bump, need this as soon as possible.

---

### Post by drs305 on 2010-04-18
This post should help you out:
[How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)]("http://ubuntuforums.org/showthread.php?t=1014708")

---

### Post by Serpher on 2010-04-18
Windows overwrites your MBR, so it'll point at the Windows boot loader rather than GRUB. You'll have to reinstall GRUB using a live CD.

[quote=http://www.linux.com/community/blogs/changing-the-default-boot-with-ubuntu-910-grub-2.html]

1. cat /etc/group/group.cfg 
see the order of the wanted kernel. Starts from 0. 
2. vi /etc/default/grub 
change GRUB_DEFAULT=0 value to wanted kernel 
3. run update-grub to update 
4. reboot and check with uname -r to see if correct kernel selected.[/quote]

EDIT: Ninja'd

---

