---
title: "Clone drive using dd results in unformatted drive..???"
date: 2012-03-01
forum: General Help
---

### Post by meanmrmustard on 2012-03-01
I'm wanting to copy my entire Natty install from /dev/sda to the new disk - /dev/sdc and be able to boot into it.

Yesterday I added a 3 TB USB drive to my system and proceeded to erase the useless software that comes on the drive (Seagate Go Flex), formatted as ext3, then clone a 2 TB internal SATA drive using clonezilla. 

This failed so I then tried the dd command (dd if=/dev/sda of=/dev/sdc) as root.

The operation completed after several hours, with no errors and claimed it had copied 2 TB of data to the new disk, so I tried to boot it. The message said something like - insert disk or bootable media..."

What was supposed to happen according to a guide I found, was after the copy was made I was supposed to go into gparted to expand the size of the partition (since I was cloning a smaller drive to a larger one) but gparted reports the entire drive as 'unformatted', and also as being 2.7 TB (100+ GB - 1% reserved for root, since I first formatted as ext3).

The system no longer sees the drive in file manager but is recognized by fdisk, and BIOS (under the cdrom drives section).

fdisk -lu reports:
Disk /dev/sdc: 3000.6 GB, 3000592977920 bytes
255 heads, 63 sectors/track, 45600 cylinders, total 732566645 sectors
Units = sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000d1faa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048    59375615   237494272   83  Linux
/dev/sdc2        59377662  3907028991  2505703432    5  Extended
Partition 2 does not start on physical sector boundary.

fdisk /dev/sdc1 returns:

"Note: sector size is 4096 (not 512)
Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel
Building a new DOS disklabel with disk identifier 0xd01e4e29.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.

Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

WARNING: DOS-compatible mode is deprecated. It's strongly recommended to
         switch off the mode (command 'c') and change display units to
         sectors (command 'u').
"

Googling on 'invalid flag' I found this [http://ubuntuforums.org/showthread.php?t=1192598](http://ubuntuforums.org/showthread.php?t=1192598) on sfdisk but I'm unsure that this is the actual problem.

sfdisk -l reports:
Disk /dev/sdc: 364801 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sdc1   *      0+   3695-   3696-  29686784   83  Linux
/dev/sdc2       3696+ 243201- 239506- 1923825665    5  Extended
/dev/sdc3          0       -       0          0    0  Empty
/dev/sdc4          0       -       0          0    0  Empty
/dev/sdc5      10504+ 243201- 232698- 1869139968   83  Linux
/dev/sdc6       3696+   3817-    122-    975872   82  Linux swap / Solaris
/dev/sdc7       3817+  10504-   6687-  53707776   83  Linux

The drive I attempted to clone is sda - sfdisk says:

Disk /dev/sda: 243201 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+   3695-   3696-  29686784   83  Linux
/dev/sda2       3696+ 243201- 239506- 1923825665    5  Extended
/dev/sda3          0       -       0          0    0  Empty
/dev/sda4          0       -       0          0    0  Empty
/dev/sda5      10504+ 243201- 232698- 1869139968   83  Linux
/dev/sda6       3696+   3817-    122-    975872   82  Linux swap / Solaris
/dev/sda7       3817+  10504-   6687-  53707776   83  Linux

Ubuntu's disk utility shows:
[IMG]http://i51.tinypic.com/ajv4h2.jpg[/IMG]
and:
[IMG]http://i56.tinypic.com/10z08z4.jpg[/IMG]

With all this:
 "Partition 2 does not start on a physical sector boundary"
and:
"Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)" and Note: sector size is 4096 (not 512)"
and:
"Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel
Building a new DOS disklabel with disk identifier 0xd01e4e29.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable." 

... I'm unsure what the next step would be if this is even recoverable at all.
Can someone see what the problem might be?

Thanks
Mr. M

---

### Post by HavarN on 2012-03-01
It is normally better to just clone partitions with the dd command. However you must have created as large or larger partitions on the new drive before doing so.

Clone partition table. Warning! It will erase whatever partition table is already on /dev/sdc:```
sfdisk -d /dev/sda | sfdisk /dev/sdc
```

Copy partition 1:```
dd if=/dev/sda1 of=/dev/sdc1 bs=1M conv=noerror
```Do the last step over for each partition.

---

### Post by meanmrmustard on 2012-03-01
> **HavarN said:**
> It is normally better to just clone partitions with the dd command. However you must have created as large or larger partitions on the new drive before doing so.

Clone partition table. Warning! It will erase whatever partition table is already on /dev/sdc:```
sfdisk -d /dev/sda | sfdisk /dev/sdc
```


Copy partition 1:```
dd if=/dev/sda1 of=/dev/sdc1 bs=1M conv=noerror
```Do the last step over for each partition.

Thanks!
I suppose if I knew how to write a script I could get all partitions copied while I'm away from the machine?

---

### Post by oldfred on 2012-03-01
I do not fully understand the new 4k drives. Some try to work as 512.

MBR drives have a max of 2.2TiB or 2TB, drives over 2TB need to be formated with gpt. Not sure how 4K drives change that, but if it is tring to be seen as 512sectors then it will not work in MBR. If 4K then it is not the same as a 512 drive.

First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of RAID arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)
srs's to show 8 sector alignment
$ sudo parted /dev/sda unit s print

GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)

Do not use dd with gpt partitions.

---

### Post by meanmrmustard on 2012-03-01
Lots of great info there, thank you Oldfred.
I've decided to install Oneiric on the new drive for now and I plan to get back to the cloning a bit later after I digest all the links.
I'll be sure to come back here and post results.
Thanks again!

---

