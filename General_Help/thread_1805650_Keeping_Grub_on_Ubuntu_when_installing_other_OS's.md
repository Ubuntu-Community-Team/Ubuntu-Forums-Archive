---
title: "Keeping Grub on Ubuntu when installing other OS's"
date: 2011-07-16
forum: General Help
---

### Post by djpemberton on 2011-07-16
I currently have Window's Vista and Ubuntu 11.04 on my desktop. I have two other partitions set aside to try other Linus distros. Currently Grub2 is used from the Ubuntu partition (I guess) in order to access the OSs. How can I install other linux distro's in the other partitions, while still using Grub as the bootloader from the Ubuntu partition?

---

### Post by dino99 on 2011-07-16
your installed grub will detect the other OSs when you run: sudo update-grub

---

### Post by oldfred on 2011-07-16
Most other distributions let you choose whether to install a boot loader. Ubunbu gives choices but you have to install it somewhere and windows just auto installs to the MBR.

If the distribution uses old grub legacy, install grub to the same partition as your install. You then also have an option to chainload (like windows is booted). If it uses grub2 do not install. If other versions of Ubuntu and you have to install grub2 to the MBR boot back into your Ubuntu install and reinstall that grub2 boot loader to the MBR. Or use liveCD if you cannot boot into Ubuntu.

#reinstall from working (not liveCD) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub

Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2")
Grub2 info & full chroot version - see METHOD 3 - CHROOT:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 and later with grub2) by talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

