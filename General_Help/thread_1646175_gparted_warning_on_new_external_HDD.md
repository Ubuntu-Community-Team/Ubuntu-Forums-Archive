---
title: "gparted warning on new external HDD"
date: 2010-12-15
forum: General Help
---

### Post by Hyphy on 2010-12-15
I just got a WD 1TB external hard drive and was going to re-format it to get rid of WD smartware. When I started gparted and looked at the information it shows a warning.

warning
unable to find mountpoint
unable to read the contents of this filesystem!
because of this some operations may be unavailable.                      


But the drive is mounted, and i can see everything in the drive. I wanted to come here for help on this warning before i did anything to the drive. Im really new to ubuntu, so please bear with me.

---

### Post by pellgarlic on 2010-12-17
generally, you don't want the drive to be mounted when you run a partitioning tool on it...

try unmounting the drive, then running gparted.

---

### Post by dcstar on 2010-12-18
> **pellgarlic said:**
> generally, you don't want the drive to be mounted when you run a partitioning tool on it...

try unmounting the drive, then running gparted.

Rubbish. Gparted will work fine on mounted drives and will clearly show if any detected partitions are mounted or not, it will not allow any changes to mounted partitions.

Most likely the external drive has Windows software on it which makes it look like a CD and installs specialised Windows software when it is plugged in.

If this is the case, gparted can be used to write a new partition table to the device so it can then be used as any other drive.

---

### Post by pellgarlic on 2010-12-21
> **dcstar said:**
> Rubbish. 
charmed, i'm sure. =P

> **dcstar said:**
> Gparted will work fine on mounted drives and will clearly show if any detected partitions are mounted or not, it will not allow any changes to mounted partitions.


i was merely trying to say that as the OP stated they wanted to reformat the drive, that it would be have to be unmounted to do so. they certainly _would_ want to make changes to the partition(s).

sometimes it's worth trying to skin the cat a different way - perhaps unmounting before running gparted would make a difference, especially seeing as gparted seems to be reporting a different status for the drive than the OP sees elsewhere...

admittedly, i could have gone into more detail, as you did, but i was trying to offer a simple starting point to solve the stated problem.

to the OP - if you're not concerned about trying to keep any of the data on the drive (which i assume you're not), why not just try ignoring those warnings (but being sure it is going to try to operate on the desired drive) and try performing a repartition (using gparted) on the external drive, to see what happens?

---

### Post by psusi on 2010-12-21
Is this an 'elements' drive?  I have seen reports from several people now of problems with these drives that I have diagnosed as WD shipping the drive with a broken format.  The NTFS filesystem claims it is larger than the disk is, resulting in errors when certain utilities try to access the backup boot sector at the end of the drive.  Unmount and reformat the drive to fix this.

---

