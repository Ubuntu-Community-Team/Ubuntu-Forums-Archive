---
title: "Bootable Drive +"
date: 2011-05-13
forum: General Help
---

### Post by trsmash on 2011-05-13
Hey Everyone,

This is one of my first post so I'm not quite sure if the question I am about to ask is in the right location or not (hopefully it is). I'm hoping that I can at least be put in the right direction.

So what I want to do is make a bootable flash drive which I can use to boot Ubuntu from but also use as a normal storage device. I have a 16GB flash drive which I want to put two paritions on. I want to use one partition to be able to boot Ubuntu while the other partition can be used as normal storage media. I am having a little trouble with it though. I can make the partitions, I can make it bootable, but I can't seem to see the second partition for storing data. Any suggestions are appreciated.

---

### Post by Elfy on 2011-05-13
Thread moved to General Help.

---

### Post by oldfred on 2011-05-13
If you want windows compatibility you have to make the first partition NTFS or FAT32 as it only sees the first partition. Then you can create additional partition(s) for Ubuntu. If you just want to be able to boot & install you can make a ISO loop mounted with grub2 or do a full install and be able to update and save data. Be sure to use manual install so you can install grub2's boot loader the the MBR of the flash drive.

See post #19 C.S.Cameron - recommends disconnection sda so grub can only install to flash drive.
Maverick now only gives combo box on grub location if you use manual install.
Lucid:
[http://ubuntuforums.org/showthread.php?t=1509603](http://ubuntuforums.org/showthread.php?t=1509603)
Step by Step Full install 8GB C.S.Cameron Post #7
[http://ubuntuforums.org/showthread.php?t=1719346](http://ubuntuforums.org/showthread.php?t=1719346)

It does not have to be encrypted:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html]("http://members.iinet.net/%7Eherman546/p19.html")
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)

Use ext2 or ext4 without journal:
tune2fs -O ^has_journal /dev/sda1
No swap or set swapiness
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler

You want journal to speed up system recovery if you have to do repairs or run fsck. But if partition is small then it does not take long to fsck anyway and without journal writing is reduced. While flash is a lot slower than SSD, some of the same configuration parameters need to be used.
SSD&#8217;s, Journaling, and noatime/relatime 
[http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/](http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/)
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)

---

