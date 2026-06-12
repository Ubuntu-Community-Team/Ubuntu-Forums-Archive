---
title: "cannot load installer from usb key"
date: 2012-08-13
forum: General Help
---

### Post by El-ahrairah on 2012-08-13
Hi everybody,

I'm opening this thread in order to try to solve this problem:

I installed ubuntu 12.04 on my HP Pavillion DV6022EA using an USB Key which I prepared under Windows using unetbootin.

It worked flawlessly the first time, but now I need to do a fresh install again, and it won't boot from the usb key!

I tried altering the boot order on my bios giving priority to usb, and also tried to explicitely booting the usb key when given the option to do so, but it would still boot my actual installation of ubuntu 12.04, not the live installer one.

What can I do in order to reinstall again using the usb key? Do I need to recreate the live key?

---

### Post by oldfred on 2012-08-13
Did something get overwritten on the flash drive? It might be easier just to reinstall to flash drive.

---

### Post by plucky on 2012-08-13
> What can I do in order to reinstall again using the usb key? Do I need to recreate the live key? 

It might be the file system is dirty due to it being un-mounted incorrectly.

Boot your 12.04 and plug in the usb drive and after it mounts automatically,right click on the icon and safely remove drive.

After that try to boot the drive and see if it now boots.

Good Luck

---

### Post by El-ahrairah on 2012-08-15
It seems that the partition got somehow damaged, so I reformatted it and reprepared the live key using latest unetbootin.

I'll try now to see if it works.

---

### Post by El-ahrairah on 2012-08-16
I've discovered what corrupted the live key during the previous install: while the system was installed on my hard disk, the boot loader got installed on the usb key itself instead of the hard drive.

This also happened during the second fresh install I made.

What can I do to prevent this from happening again?

---

### Post by oldfred on 2012-08-16
Did you use auto install? Grub defaults to install in sda, normally. And some BIOS make a flash drive sda.

The best way to avoid that is to use manual install. But you have to understand a little about partitions. You have to create a partition, choose that it be / (root) and format usually ext4. You do the same for swap, but no format and any additional partition like /home or data.

If with flash drive installed you can boot into your install, you can install the grub to the MBR of the hard drive.

#reinstall from working (not liveCD) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions, it may be sda when booted):
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub

Grub may remember the device installed into.
#To see what drive grub2 uses see this  - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub


#to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

### Post by C.S.Cameron on 2012-08-16
Boot to your hard drive using the USB, once booted remove the USB and in terminal do ```
update-grub
```

---

### Post by El-ahrairah on 2012-08-17
> **oldfred said:**
> Did you use auto install? Grub defaults to install in sda, normally. And some BIOS make a flash drive sda.

Yes, I followed the standard procedure leaving the default for everything.

I already managed to correct this problem, and thanks for explaining me how to avoid this in the future.

---

