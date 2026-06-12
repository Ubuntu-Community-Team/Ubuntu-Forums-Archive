---
title: "Problem formatting Hard Disk"
date: 2012-03-01
forum: General Help
---

### Post by hogfan on 2012-03-01
I have prepared all 4 disks I plan to add to my mdadm array with GPARTED, creating a single primary partition on each disk as an "unformatted partition".  However, when I go to create the Array, MDADM keeps complaining that one of the disks appears to have and ext2 file system on it!  I have been unable to get rid of this after formatting that drive several times.  The drive was previously formatted ext3 but that SHOULD have gone away when I deleted the partition in GPARTED and re-created a new unformatted partition.  Here is the output from attempting to create the array:

```


$ sudo mdadm --create --verbose /dev/md0 --level=5 --raid-devices=4 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1
mdadm: metadata format 00.90 unknown, ignored.
mdadm: layout defaults to left-symmetric
mdadm: chunk size defaults to 64K
mdadm: /dev/sde1 appears to contain an ext2fs file system
    size=1297137664K  mtime=Tue Feb 28 02:57:14 2012
mdadm: size set to 1953513408K
Continue creating array? 

```

So what can I do to ensure disk SDE doesn't show any partition information?  I do not want to zero out the drive as that will take overnight and I'm already way behind on getting the the created, since it will take overnight to sync.  

I've tried using FDISK and GPARTED to remove the partion and create a new one, but something on that disk keeps telling mdadm that there is an ext2 partition there.

Any help is extremely appreciated.

-hogfan

---

### Post by dcstar on 2012-03-03
Use gparted to write a new partition table to the drive.

---

