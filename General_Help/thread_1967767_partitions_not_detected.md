---
title: "partitions not detected"
date: 2012-04-28
forum: General Help
---

### Post by jworr on 2012-04-28
I'm trying to resize the partitions on my hard disk but gparted on the 12.04 and 11.10 cds doesn't detect any partitions on my disk.  The unusual thing is that my system still works and can obviously see my / & /home partitions.  Are there any bugs with gparted that would cause this issue?  Does anyone know of a fix to make gparted see my partitions?

---

### Post by ventrical on 2012-04-28
> **jworr said:**
> I'm trying to resize the partitions on my hard disk but gparted on the 12.04 and 11.10 cds doesn't detect any partitions on my disk.  The unusual thing is that my system still works and can obviously see my / & /home partitions.  Are there any bugs with gparted that would cause this issue?  Does anyone know of a fix to make gparted see my partitions?

  I had just seen this  a few days back .. but I forget where it was (the solution). I do know that there are some big problems with Ubiquity on older machines. What type of PC do you have?

---

### Post by oldfred on 2012-04-28
The most common issue is some sort of partition table corruption, but it must not be a partition you normally use or system would not work. I could be chkdsk needed on a NTFS partition or RAID data on drive, but your old install would not have installed with RAID data.

Post this:

```
sudo fdisk -lu
```

---

### Post by jworr on 2012-04-28
My problem is with the disk /dev/sdb - has / & /home partitions which are /dev/sdb5 & /dev/sdb6 respectively

/dev/sda is my windows disk
/dev/sdc is a storage disk

sudo fdisk -lu

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcb50c77f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   117227519    58612736    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 60.0 GB, 60021399040 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117229295 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0dd91fd7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sdb2          208894   117229567    58510337    5  Extended
/dev/sdb5          208896    15831039     7811072   83  Linux
/dev/sdb6        15833088   117227519    50697216   83  Linux

Disk /dev/sdc: 750.2 GB, 750155292160 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465147055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003641e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   830269439   415134688+  83  Linux
/dev/sdc2       850747392  1465143295   307197952    7  HPFS/NTFS/exFAT
/dev/sdc3       830271330   840504734     5116702+  83  Linux
/dev/sdc4       840505344   850747391     5121024   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by jworr on 2012-04-28
Also, my machine is fairly new:

AM3 compatible motherboard, Phenom 2 cpu
/dev/sda & /dev/sdb are SSD hard disks
/dev/sdc is a traditional spinning disk

---

### Post by oldfred on 2012-04-28
I do not see any obvious partition error, boot script often finds thing as it mounts in a similar way as gparted.

post the link to the Boot info.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or Create BootInfo report & post the link to a run of boot info script so we can see your exact configuration.

---

### Post by jworr on 2012-04-28
Here is the boot-repair info:

URL: [http://paste.ubuntu.com/953412/](http://paste.ubuntu.com/953412/)

---

### Post by oldfred on 2012-04-28
I missed it in you fdisk list. Fortuneately boot script says where the issue is. 
```

Disk /dev/sdb: 60.0 GB, 60021399040 bytes
255 heads, 63 sectors/track, 7297 cylinders, total [COLOR=Red]117229295 [/COLOR]sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sdb2             208,894   [COLOR=Red]117,229,567 [/COLOR]  117,020,674   5 Extended
/dev/sdb5             208,896    15,831,039    15,622,144  83 Linux
/dev/sdb6          15,833,088   117,227,519   101,394,432  83 Linux

[COLOR=Red]/dev/sdb2 ends after the last sector of /dev/sdb[/COLOR]

```First backup partition table and save this to some other drive.
sudo sfdisk -d /dev/sdb > parts_sdb.txt


Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by jworr on 2012-04-29
Awesome, fixparts fixed the issue.  Thanks for your help!

---

