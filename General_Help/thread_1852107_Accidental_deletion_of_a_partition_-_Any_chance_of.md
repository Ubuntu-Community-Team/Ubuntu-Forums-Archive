---
title: "Accidental deletion of a partition - Any chance of recovery?"
date: 2011-09-29
forum: General Help
---

### Post by sammya on 2011-09-29
So i ****** up. Deleted the partition which has all my files on it..pretty gutted. Tired..wasn't concentrating..******. Seeing if there is any chance of recovering the partition I deleted? It is currently showing as unallocated space. Haven't touched it since and currently running ubuntu via live usb.

Any help is appreciated and not taking any further action until certain there is nothing I can do about this.

Cheers

Sam

---

### Post by sammya on 2011-09-29
Oh, running ubuntu 11.04 btw

---

### Post by matt_symes on 2011-09-29
Hi

Try TestDisc.

> 
[COLOR=#000000][FONT=Times New Roman][FONT=sans-serif][SIZE=1]**TestDisk** is *powerful* free data recovery software! It was primarily designed to help **recover lost partitions** and/or **make non-booting disks bootable again** *when* these symptoms are caused by *faulty software*, certain types of *viruses* or*human error* (such as *accidentally* deleting a Partition Table). Partition table recovery using TestDisk is really easy[/SIZE].[/FONT][/FONT][/COLOR][http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Kind regards

---

### Post by sammya on 2011-09-29
yeah stumbled across this..any chance of doing this from the ubuntu 11.04 live usb?

on a bus wifi so terrible wifi means i can't download stuff. cheers

---

### Post by oldfred on 2011-09-29
Testdisk is in the repositories, so you have to download it.

I would do this first no matter what:
Backup partition table to text file & save to external device.
sudo sfdisk -d /dev/sda > PTsda.txt


Do you know where the partition started and ended. parted which you have will let you key in approximate values and try to find a partition.

Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)

Do you have gparted. If liveCd you should have it.
GParted's partition-recovery tool.
Device -> Attempt Data Rescue in GParted

gparted is just gui version of parted, but not sure of difference in how they try to find partition to recover it.

---

