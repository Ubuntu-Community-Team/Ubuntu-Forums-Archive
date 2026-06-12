---
title: "Dual boot with USB drive"
date: 2010-12-16
forum: General Help
---

### Post by ebasa on 2010-12-16
I recently installed another Linux on my USB drive. All works well and can boot into Ubuntu or PeppermeinOS. 

HOWEVER, the system will not boot at all unless the USB is plugged in. How can I fix this?

---

### Post by sgosnell on 2010-12-16
The way to avoid it is to put grub on the USB drive when you install, NOT on the internal HDD.  Search for 'reinstall grub' and you should find detailed instructions for fixing your problem.

---

### Post by oldfred on 2010-12-17
What do you have on internal drive? That is what you want installed into the MBR of the internal drive. You want the system you have installed in the USB drive installed to the MBR of the external drive. Change sda & sdb if reversed in my examples.

If you can boot either system you can install its grub to its drive.

reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
if it's "/dev/sda"  then just run:
sudo grub-install /dev/sda
If that returns any errors run:
sudo grub-install --recheck /dev/sda
Then after rebooting:
sudo update-grub

I do not know if Pepermint is grub or grub2 but you need to do the same if it is the one in sdb. 

If grub legacy this is the command:
sudo grub-install /dev/sdb
This is to automatically generate a new menu.lst file for you.
sudo update-grub

If you do not install from the working system to the working systems MBR, then you will have to use a liveCD to reinstall grub and the instructions are different and different for grub legacy and grub2.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by C.S.Cameron on 2010-12-17
Yes, when doing a Full install to USB use manual partitioning and make sure you install bootloader to the USB drive.
Better yet, unplug your internal drive before proceeding, it makes for a neater grub.

A simple method that fixes a Windows 7 MBR:

[http://ubuntuforums.org/showpost.php?p=10228004&postcount=2](http://ubuntuforums.org/showpost.php?p=10228004&postcount=2)

---

