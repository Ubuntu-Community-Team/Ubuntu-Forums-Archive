---
title: "Partition Messed Up HELP!"
date: 2010-05-02
forum: General Help
---

### Post by ArmchairArmada on 2010-05-02
I think something about my partition tables messed when I was trying to shut down and now I cannot boot up Ubuntu.  The problem primarily seems to be with the partition I was using for my Home directory -- where all my stuff is!

I think maybe it can be fixed with fdisk, but I don't know what I'm suppose to do.  Please help.

Right now I'm using a Live CD of Ubuntu 9.04.

---

### Post by wilee-nilee on 2010-05-02
> **ArmchairArmada said:**
> I think something about my partition tables messed when I was trying to shut down and now I cannot boot up Ubuntu.  The problem primarily seems to be with the partition I was using for my Home directory -- where all my stuff is!

I think maybe it can be fixed with fdisk, but I don't know what I'm suppose to do.  Please help.

Right now I'm using a Live CD of Ubuntu 9.04.

So it would be helpful to know a little more, are you running more then one operating system, and what were you doing before this happened?

---

### Post by dino99 on 2010-05-02
> **ArmchairArmada said:**
> I think something about my partition tables messed when I was trying to shut down and now I cannot boot up Ubuntu.  The problem primarily seems to be with the partition I was using for my Home directory -- where all my stuff is!

I think maybe it can be fixed with fdisk, but I don't know what I'm suppose to do.  Please help.

Right now I'm using a Live CD of Ubuntu 9.04.

you should have seen some errors when it have happened or when you try to boot again. Have you an other distro installed or several kernel boot lines ? Have you booted with recovery mode ?

---

### Post by ArmchairArmada on 2010-05-02
64bit Ubuntu 9.10 is the only operating system that I have.  Immediately before the hard drive problem happened GFCU Ultra (NES emulator) went crazy in the background and filled .xsession-errors with 488.4 GB worth of errors.  I killed that process and deleted the file and everything seemed fine, but when I tried to shut down it hung for a long time.  Then it messed up and when I tried to reboot my /home partition couldn't be mounted anymore.

fdisk -l says this:
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d35bf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24899   200001186   83  Linux
/dev/sda2           24900      121601   776758815    5  Extended
/dev/sda5          120108      121601    12000523+  82  Linux swap / Solaris
/dev/sda6           24900      104575   639997407   83  Linux
/dev/sda7          104576      120107   124760758+  83  Linux

Partition table entries are not in disk order

```

fdisk /dev/sda6 tells me this:
```
ubuntu@ubuntu:~$ sudo fdisk /dev/sda6
Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel
Building a new DOS disklabel with disk identifier 0xb7f2b8ee.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.


The number of cylinders for this disk is set to 79675.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)
Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

Command (m for help): 

```

---

### Post by dino99 on 2010-05-02
need to google about: "invalid flag 0x0000 of partition table"

have you tried: sudo dpkg --configure -a

or installed gpart

you should use fsck -N fisrt

[https://help.ubuntu.com/community/SystemAdministration/Fsck](https://help.ubuntu.com/community/SystemAdministration/Fsck)

---

### Post by ArmchairArmada on 2010-05-02
Well, for some strange reason my computer booted up without any noticeable problems.  Strange considering how many times it failed to boot before.

What does "invalid flag 0x0000 of partition table" mean?

---

### Post by dino99 on 2010-05-02
> **ArmchairArmada said:**
> Well, for some strange reason my computer booted up without any noticeable problems.  Strange considering how many times it failed to boot before.

What does "invalid flag 0x0000 of partition table" mean?

= mess
normally everything has to be well known ordered, linux need to find each thing at the logical place

thats why the system run fsck time to time. you should ask the system to force a fsck at next reboot:

[http://www.cyberciti.biz/faq/linux-force-fsck-on-the-next-reboot-or-boot-sequence/](http://www.cyberciti.biz/faq/linux-force-fsck-on-the-next-reboot-or-boot-sequence/)

it should be a goog idea to clean your system too: install and use gconf-cleaner

---

