---
title: "How do I delete Ubuntu from my PC?"
date: 2006-02-26
forum: General Help
---

### Post by YellowHat on 2006-02-26
I used F-Disk and the Windows 98 CD and they both couldn't do it? How do I delete the partition?

---

### Post by ironmaiden6669 on 2006-02-26
You will have to Low Level Format ("Zero") the drive if you want to put a windows/dos partition on it.

Windows doesn't like drives that have experienced Linux.

---

### Post by YellowHat on 2006-02-26
How do I do the above? Do, I get a floppy disk format it to zero then pop it in and then it will start the process of deleting it? How do I start the process of formatting it to zero? 

Can you tell me detailed?

---

### Post by pestilence4hr on 2006-02-26
Not true.  You can use whatever fdisk to repartition.  I prefer cfdisk, in ubuntu.  If you are interested in removing the boot loader, you can run fdisk /mbr with windows fdisk.

In summary, don't bother with a low level format.

---

### Post by drachir on 2006-02-26
I was messing with it bit and I used my xp cd that came with my dell to reformat a drive.Here is what I did. 

Change you bios to boot from cd first. 
Place cd in rom drive
hit any key to boot from cd
run through all the steps until you get to the partition section
I deleted all partitions (Linux, Swap, Fat32) and created 1 new partition and formated it NTFS. From there you can use you microsoft products.

---

### Post by ironmaiden6669 on 2006-02-26
An XP disk might be the best way to go.
Win98 & older versions of fdisk were pretty useless with some things.
Go with drachir's method & use an XP disk to wipe partitions & re-format.
If you want to use Win98, format it as fat32 with the XP disk then quit XP setup and install Win98.

---

