---
title: "Troublegrowing LVM on RAID1"
date: 2011-05-18
forum: General Help
---

### Post by rsteinmetz70112 on 2011-05-18
Ubunt 10.04 LTS. I installned new hard drives in a RAID1 array with LVM volumes on it. I want to grow the arry and expand one of volumes to use the additional space. 

I installed the new hard drives one at a time and resynced the array. Both drives show a large amount of unused space. 

I thought the next step would be to grow /dev/md0 so I booted into a live CD, installed mdadm and lvm2. everything seems correct.

# mdadm --grow /dev/md0 --size=max

The command runs without an error but nothing happens.

I must be doing something wrong.

---

### Post by rsteinmetz70112 on 2011-05-19
I've tried a using absolute values with grow and nothing happens. mdadm repost no space on device.

I've tried rewriting the superblock to get it to recognize the new device size and nothing seems to happen. Here is a portion of the detail.

> /dev/md0:
        Version : 00.90
  Creation Time : Sat Mar 10 23:43:50 2007
     Raid Level : raid1
     Array Size : 312568576 (298.09 GiB 320.07 GB)
  Used Dev Size : 312568576 (298.09 GiB 320.07 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent


I've also tried using the lvm tools and they indicate the device is full. 

I'm sure need to expand the md0 device but I'm not sure how to do that.

---

