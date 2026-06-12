---
title: "Installation help, multi boot"
date: 2012-10-11
forum: General Help
---

### Post by longshanks62 on 2012-10-11
Hi,
I am absolutely new to Ubuntu, I run a windows 7/XP dual boot system from a single HDD, I have a spare installed HDD of 80 gig which I have formatted and wish to install Ubuntu 11.10 onto it< I have the live CD I have tried to do the install from the cd but I need a basic walk through,
   So far I have got as far as "The installation type" menu box were I select dev/sda when I select continue I am given an error message "No root file system is denied please correct from the partition menu then I struggle.
Ideally I want a triple boot system as described above.
kind regards
Brian

---

### Post by sienile on 2012-10-11
You have to set the mount point to "/" for the drive you want to install Ubuntu on.

I had the same confusion when I tried installing for the first time. Selecting it does nothing. You can even set the mount point and then have your Windows partition selected when you click next/continue/whatever-it-says. :P Just be sure that the right partition has the mount point set.

Welcome to Linux. You'll enjoy it.

---

### Post by oldfred on 2012-10-11
Some examples with walk thru screen shots. Herman's are the alternative installer which is just text based not gui but process is still the same.

The important part of the install is the combo box at the bottom of the partitioning screen. That is the drive where the grub2 boot loader will be installed. You want in in the same drive as Ubuntu not overwriting the Windows boot files. But then want to set BIOS to boot the Ubuntu drive.

Install to external drive 11.04. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/2/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/2/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail - now alternative (text based) installer
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

Also grub will only show one Windows boot entry as Windows moves boot files from second install to the first. Your second Windows install is only bootable from the first Windows. If you want to boot both directly from grub, you have to run Windows repairs.

Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

