---
title: "grub error 17"
date: 2006-04-26
forum: General Help
---

### Post by cosmoshell on 2006-04-26
grub error 17. ive tried to reinstall grub 7 time ive tried to reinstall ubuntu 10 its apperent im not going to get grub to work how can i uninstall this piece of crap. i dont have a windows cd.


shame never thought i would have a problem with grub the rest of my computers it works on.

---

### Post by r4ik on 2006-04-27
Try,
Boot using a DOS  Floppy.

fdisk /mbr
Should clear the Grub boot loader, assuming that you didn't move the partition number that XP boots from. 
Here's the link,

[http://www.bootdisk.com/bootdisk.htm](http://www.bootdisk.com/bootdisk.htm)

Good luck !

---

### Post by cosmoshell on 2006-04-27
i have no floppy drive

---

### Post by cosmoshell on 2006-04-28
HELP... someone..... echo......

---

### Post by wubunty on 2006-04-29
Try to reset BIOS setting to default

---

### Post by cosmoshell on 2006-04-29
same old error.

---

### Post by r4ik on 2006-04-29
Try,

[http://ubcd.sourceforge.net/](http://ubcd.sourceforge.net/)

Same story no floppy needed.

Good luck !

---

### Post by cosmoshell on 2006-04-29
oh ya i forgot all about ultimate boot cd that thing is asume

---

### Post by lemix on 2006-04-29
trying to uninstall something? why not go through the installation process of ubuntu and just delete your partitions and leave after its formatted

youll get like a Error, no root filesystem specified but ubuntu will be uninstalled and your hard drive will be clean.

---

### Post by Toxicity999 on 2006-04-29
I can verify that for you, just abuse the Partition manager in ubuntu, and just bail out before you actually install anything.

---

### Post by cosmoshell on 2006-05-01
actualy im just going to leave ubuntu in here and take the long and pain in the *** way of adding ubuntu to the windows boot loader once fixed.

---

### Post by stevenjoseph on 2006-05-01
try this boot using a live cd then 

mkdir /mnt/tmp
mount /dev/<root_partition> /mnt/tmp
chroot /mnt/tmp
grub

grub>root (hd<number_of_root>,<partition_no>)
grub>setup (hd<number_of_root>)
grub>quit

exit 
restart 


this might work.
Its about time for grub to be obsolete .. too many problems

---

### Post by Kallid on 2006-05-01
I am getting a similar error.

I reinstalled windows and found i was unable to enter ubuntu(boot loader).  

So I was told to try this:
su
grub
find /boot/grub/stage1
root (hd1,3) - whatever it spits out.
setup(hd1,3)

once I was able to get this to work; I tried to use the bootloader I get this error below.
-------------
Im getting the same error but mine says,

root (hd1,0)
File system type unknown, partition type 0x7

kernel /boot/vmlinuz-2.6.12-10-386 root = /dev/hdb1 ru quiet splash

Error 17: cannot mound selected partition
------------

---

### Post by cosmoshell on 2006-05-01
ive tried that befor kept getting some error somewhere saying it couldent mount when i was in the live cd

---

