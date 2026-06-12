---
title: "MD RAID partition lost on boot, every time."
date: 2011-08-08
forum: General Help
---

### Post by StrangeWill on 2011-08-08
I have two disks in a RAID.
```

SATA device C	465.76 GB	ATA WDC WD5000AVDS-6
SATA device D	465.76 GB	ATA WDC WD5000AAKS-0
```


D keeps losing it's partition on boot:

```

ls /dev/sd*
/dev/sda   /dev/sda2  /dev/sdb   /dev/sdc   /dev/sdd
/dev/sda1  /dev/sda5  /dev/sdb1  /dev/sdc1

```
I can rebuild and remount it, but on reoobt it's back to sdd only, if I open up fdisk:

```
sudo fdisk /dev/sdd

The number of cylinders for this disk is set to 60801.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): p

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x88da42e2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       60802   488386552+  fd  Linux raid autodetect

Command (m for help):
```

fdisk sees the partition, so does Webmin.

I can rebuild it every time, but it's awfully annoying. What is going on here?


Edit: noticed this:

Extent	1 - 60802 of 60801

Uh... ??

---

### Post by Habitual on 2011-08-09
post your /etc/fstab

---

### Post by StrangeWill on 2011-08-09
> **Habitual said:**
> post your /etc/fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=10ec9d05-7c79-45d3-ad0b-f1ea8da0a318 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=418ae0be-1b93-4498-b27a-68e9b802a460 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/VolGroup01/VolStorage01  /VirtualMachines/  ext3  suid,dev,exec  0  0
/dev/md0  /storage/  ext3  suid,dev,exec  0  0
/storage/nfs  /storage/nfs  bind  bind  0

```

However, I've even tried booting with these drives unpowered and hot-plugging them while on (they're in hot-swap bays). Still does it.


Edit:

If it helps, I'd re-partition it and save the changes and go to add it, but it says sdd1 doesn't exist, after that if I try to re-partition it and re-add it, it works.

So weird :(

---

### Post by StrangeWill on 2011-09-05
Still plaguing me. Webmin sees the partition, FDISK sees the parition, Linux still only shows sdd. :(

```


william@LinuxServer:/# partprobe -s
/dev/sda: msdos partitions 1 2 <5>
/dev/sdb: msdos partitions 1
/dev/sdc: msdos partitions 1
/dev/sdd: msdos partitions 1
william@LinuxServer:/# ls /dev/sd*
/dev/sda   /dev/sda5  /dev/sdb1  /dev/sdc1
/dev/sda1  /dev/sdb   /dev/sdc   /dev/sdd


```

---

### Post by YesWeCan on 2011-09-05
Have you tried unmounting sdd1 and running a file system check?

sudo e2fsck /dev/sdd1

---

### Post by StrangeWill on 2011-12-04
> **YesWeCan said:**
> Have you tried unmounting sdd1 and running a file system check?

sudo e2fsck /dev/sdd1

Actually it gets better, I've wondered if it had anything to do with the RAID, so I create a new partition and RAID on sdd1, copy everything over.... it loses it on boot.


Fine, create a new partition on sdd, sdd1 -> type Linux... reboot.

It's gone.

What is going on?! I'm tempted to contact Western Digital and see if there is a known issue with this drive or something.


Here is a full report of what I've done to replicate this (what I'll be sending Western Digital too):

[http://www.roushtech.net/badDrive.html](http://www.roushtech.net/badDrive.html)

---

