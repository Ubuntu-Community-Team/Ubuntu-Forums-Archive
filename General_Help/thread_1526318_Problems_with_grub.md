---
title: "Problems with grub"
date: 2010-07-07
forum: General Help
---

### Post by xo-mitsu-ox on 2010-07-07
Hello first that nothing
 I am new in ubuntu and believe that parti with the left foot xD

 My computer has two physical hard disks
 And to the moment to install on having finished the installation I put advanced configurations
 And accidentally I put the engine of item of ubu on the second hard disk
 In that I have XP's files
 And now every you see that I want to use the PC I have to choose from the boot the second disc in order that the grub takes

 My consultation is that if it is manero of taking the grub and to bring it to the disc where I have the ubu installed

---

### Post by oldfred on 2010-07-08
Welcome to the forums:

reinstall from working (not liveCD) system - first find Ubuntu drive (if sdb change all sda to sdb):
sudo fdisk -l
if it's "/dev/sda"  then just run:
sudo grub-install /dev/sda
If that returns any errors run:
sudo grub-install --recheck /dev/sda
Then:
sudo update-grub

To make sure it remembers to reinstall on updates to the correct direct also run this:
sudo dpkg-reconfigure grub-pc
spacebar to choose drive, enter to accept, do not choose partitions

To reinstall from liveCD or reinstall windows:
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

