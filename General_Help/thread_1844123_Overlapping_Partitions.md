---
title: "Overlapping Partitions"
date: 2011-09-14
forum: General Help
---

### Post by UCDguy on 2011-09-14
Hi guys,

It appears I may have recently messed up my partition table, I cannot boot into any OS. Parted and Gparted both say I have overlapping partitions.

/dev/sda1 : start= 2048, size= 209632, Id= 7, bootable
/dev/sda2 : start=206848, size= 1560449312, Id=7
/dev/sda3 : start=0, size =0, Id=0

I can see that sda1 and sda2 are overlapping but I'm not sure how to go about fixing it? Sorry I'm a bit of a noob.

Thank for looking!:D

---

### Post by cryptotheslow on 2011-09-14
Ouch - that's doesn't look good.

I've not had to fix an issue specifically like that, but I think TestDisk may well be able to sort it out.

It can even work on an image of the drive i.e. use dd to make a bitwise clone of sda to another drive and then attempt to patch things up there without risking what's on your actual live disk.

Read up well and if at all possible take a back up before you start.
[http://drehsen.com/compusectools/testdisk/testdisk/doc/testdisk.html](http://drehsen.com/compusectools/testdisk/testdisk/doc/testdisk.html)

It may well be on an Ubuntu Live CD and it is certainly on the GParted Live CD:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)


Wait for others to comment before diving in as this is just how I would try and tackle it - which doesn't mean it's a good idea :D

---

### Post by Quackers on 2011-09-14
Boot from the Ubuntu live cd/usb and select "try Ubuntu" and when the desktop loads please post the output of this terminal command ```
sudo fdisk -lu
```

---

