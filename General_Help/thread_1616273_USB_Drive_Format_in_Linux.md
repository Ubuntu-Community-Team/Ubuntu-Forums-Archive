---
title: "USB Drive Format in Linux"
date: 2010-11-08
forum: General Help
---

### Post by vikrang on 2010-11-08
I am having trouble in getting Windows 7 to recognize partition of my 2GB Kinston data traveler Pen Drive
 
I usually try different Distros using this USB and do a quick format before trying the next one.
 
I prefer the dd command in Linux to using Unetbootin / USB creator software.
 
I format the USB in (FAT 32 or FAT ) using
 
mkdosfs -F 32 /dev/sdb1 (sdb1 is my USB drive)
 
I also tried
 
mkfs.vfat /dev/sdb1
 
After that I do 
 
dd if=/usr/src/*****.iso of=/dev/sdb1
 
It writes properly...
 
However on reboot , I get the error "Bootsector not defined " and goes on to boot the next device (HDD) in BIOS
 
Then I have to go to windows and use Unetbootin to copy the ISO and make a bootable disk
 
Also , I noticed some ISO's , even though created using Unetbootin are not able to run the Live CD ...
 
There is some error in mounting the root partition 
 
"Cannot find tty /dev/sr0 /dev/sdb1/,/dev/sda1 
 
Kernel panic "
 
I remember for some distros like Arch the LABEL for the USB should be the same as the LABEL of CD..
 
Can someone throw some light on this?

---

### Post by jocko on 2010-11-08
> **vikrang said:**
> I am having trouble in getting Windows 7 to recognize partition of my 2GB Kinston data traveler Pen Drive
 
I usually try different Distros using this USB and do a quick format before trying the next one.
 
I prefer the dd command in Linux to using Unetbootin / USB creator software.
 
I format the USB in (FAT 32 or FAT ) using
 
mkdosfs -F 32 /dev/sdb1 (sdb1 is my USB drive)
 
I also tried
 
mkfs.vfat /dev/sdb1
 
After that I do 
 
dd if=/usr/src/*****.iso of=/dev/sdb1
 
It writes properly...
 
However on reboot , I get the error "Bootsector not defined " and goes on to boot the next device (HDD) in BIOS
 
Then I have to go to windows and use Unetbootin to copy the ISO and make a bootable disk
 
Also , I noticed some ISO's , even though created using Unetbootin are not able to run the Live CD ...
 
There is some error in mounting the root partition 
 
"Cannot find tty /dev/sr0 /dev/sdb1/,/dev/sda1 
 
Kernel panic "
 
I remember for some distros like Arch the LABEL for the USB should be the same as the LABEL of CD..
 
Can someone throw some light on this?

I think there is more to it than just copying the iso to the usb drive. You also need to install a boot manager on it, and set it to boot the correct partition. Why not just use the boot disk creator?

---

### Post by v1ad on 2010-11-08
yes use a boot disk creator. unetbootin is one that i tend to use quite often.
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by vikrang on 2010-11-08
Dear Jocko , thanks....Agreed that there should be bootable files and mere copying wont work....But since it is an extract of the Linux Distro ISO , there is an iso linux folder which has the necessary bootfiles....To put it simply , I am using USB i/o burning to a CD and rnning from it

---

### Post by jocko on 2010-11-08
> **vikrang said:**
> Dear Jocko , thanks....Agreed that there should be bootable files and mere copying wont work....But since it is an extract of the Linux Distro ISO , there is an iso linux folder which has the necessary bootfiles....To put it simply , I am using USB i/o burning to a CD and rnning from it
That is not enough. The first stage of the boot loader needs to be installed to the master boot sector (mbr) of the disk. Since you only copy the iso to a partition on the disk, the part of the boot loader that needs to be in the mbr will never be installed.

---

### Post by psusi on 2010-11-08
What you are doing does not make sense.  An iso file is an image of the iso9660 cdrom filesystem.  You are essentially formatting the usb stick with iso9660 instead of vfat when you dd the image like that.  This will not produce something that is bootable in a pc, nor that windows will mount ( it only recognizes iso9660 on a cdrom, not hard disk ).

If you are trying to make a bootable usb stick then you need to use the startup disk creator on the menu in Ubuntu, or unetbootin.

---

