---
title: "rezise partition"
date: 2010-08-11
forum: General Help
---

### Post by armandointer on 2010-08-11
I tried to upgrade to ubuntu 9.10 and says that there is not enough disk space .
What should i do?

---

### Post by Sunseeker.ch on 2010-08-11
* resize your partition
* delete some files
* backup your files and do a fresh install
* buy a bigger/larger harddrive

---

### Post by armandointer on 2010-08-11
Yeah easy to say to format my laptop.But is there anyother way to resize partiotion without format ?

---

### Post by Mark Phelps on 2010-08-11
> **armandointer said:**
> I tried to upgrade to ubuntu 9.10 and says that there is not enough disk space .
What should i do?

Impossible to say without some details ...

First, is this a Wubi installation, or an installation in a separate Linux partition.  Important because resizing is done completely different, depending on how Ubuntu was installed.

Second, let's get a look at your current partitioning scheme.  Open a terminal and run "sudo fdisk -lu" (that's a lowercase L, not a one), and post the results back here.

---

### Post by armandointer on 2010-08-11
Disk /dev/sda: 160.0 GB, 160041885696 bytes 255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors Units = sectors of 1 * 512 = 512 bytes Disk identifier: 0xe897e897     Device Boot      Start         End      Blocks   Id  System /dev/sda1   *      206848   199766015    99779584    7  HPFS/NTFS /dev/sda2       205004800   312578047    53786624    6  FAT16 /dev/sda3       199768275   204989399     2610562+   5  Extended /dev/sda5       199768338   204652034     2441848+  83  Linux /dev/sda6       204652098   204989399      168651   82  Linux swap / Solaris  Partition table entries are not in disk order

---

### Post by armandointer on 2010-08-11
please help me!

---

### Post by B00R4dL3y on 2010-08-11
I'd boot up Ubuntu from a CD (or USB stick) and run gparted to resize your partitions.

If you didn't do too much to customize your Ubuntu (like install lots of extra software) or don't mind installing from scratch instead of an upgrading, then I'd just get Ubuntu version 10.04LTS, burn it to a CD (or USB stick).  Check that I can boot from CD (or USB).  Copy everything from my home directory to external storage.  And proceed with re-installing.  After I re-install I just copy everything back to my home folder.

I'd just skip 9.10 - might as well just install the latest stable release.

---

### Post by Mark Phelps on 2010-08-13
It's hard to help folks that won't answer basic questions -- such as the one I asked regarding whether or not this was a Wubi installation.

Since you didn't answer that, I'm going to guess (based on reading your fdisk results) that it's NOT a Wubi installation.

If the MS Windows version is Vista or Win7, do NOT use Gparted to shrink that partition to make room to expand Ubuntu.  Doing so will run the risk of corrupting the Vista/Win7 OS and rendering it unbootable. In either of these cases, use the builtin Disk Management utility to shrink the OS partition.

IF it's WinXP, you should be OK to use Gparted.

---

### Post by viralmeme on 2010-08-13
> **armandointer said:**
> please help me!
Boot from the CD and run [Qparted]("http://gparted.sourceforge.net/screenshots.php") then post the results here.

---

