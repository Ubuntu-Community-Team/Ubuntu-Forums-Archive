---
title: "expand free space after dd"
date: 2010-01-20
forum: General Help
---

### Post by gdanko on 2010-01-20
I used dd to copy a 320G drive to a 750G drive but my 750G drive is effectively now a 320. I have another 300+ GB of free space on /dev/sdd2. Is there a way to expand it? I've searched around but cannot find anything. I am using Ubuntu 9.10 64 bit desktop.

My dd command was: dd if=/dev/sda2 of=/dev/sdd2 bs=2048

**fdisk /dev/sda**

The number of cylinders for this disk is set to 38913.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): p

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009068c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           38671       38913     1951897+  82  Linux swap / Solaris
/dev/sda2   *           1       38670   310616743+  83  Linux


**fdisk /dev/sdd**

The number of cylinders for this disk is set to 91201.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): p

Disk /dev/sdd: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009068c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1         262     2104483+  82  Linux swap / Solaris
/dev/sdd2             263       91201   730467517+  83  Linux

**df -h**

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             292G  2.7G  275G   1% /
/dev/md0              1.4T  487G  820G  38% /data
/dev/sdd2             292G  2.7G  275G   1% /mnt/newroot

---

### Post by zollie on 2010-01-20
you shouldn't have used dd on drives of mismatched sizes.

you should have rsync'ed the data from one to another.

the way you wanted it to work, dd would have worked fine for drives of identical sizes.  In this case, you've overwritten the partition table, messing it up.

Just repartition your new 720g drive the way you want it, create a new file system and then rsync the data over.

---

