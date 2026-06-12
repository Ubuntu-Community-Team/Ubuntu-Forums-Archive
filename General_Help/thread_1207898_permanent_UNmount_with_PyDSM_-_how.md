---
title: "permanent UNmount with PyDSM - how?"
date: 2009-07-08
forum: General Help
---

### Post by AlanRick on 2009-07-08
I installed PySDM to permanently (at boot) mount a windows data-only partition (sd2) and got it working a beautifully. PySDM is a great utility :cool:.

Trouble is I accidentally mounted another partition (sd1) permanently so I'd like to correct that using PySDM.

Trouble is, sd1 no longer appears in the PySDM partition tree when I expand sda. I guess this is because it is permanently mounted.
 
How can I undo this?

Alan

---

### Post by rbc on 2009-07-08
I probably will not be able to help, but the smarter folks who will be able to are going to want the results of these two commands. Type then, separately, into terminal and post back with the results:
sudo fdisk -l
mount | grep /dev

---

### Post by AlanRick on 2009-07-09
Thanks rpc.
I solved the immediate problem by editing /etc/fstab directly.


But I'm still puzzled by the missing branches in PyDSM.

Here goes for the experts....
BTW: I simplified for the first post. It's actually sda1,sda2 and sda4 that are missing from the tree.


```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3c5f3c5e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2805    22531131    7  HPFS/NTFS
/dev/sda2            2806       12367    76806765    7  HPFS/NTFS
/dev/sda3           12368       13896    12281692+   c  W95 FAT32 (LBA)
/dev/sda4           13897       19457    44668732+   f  W95 Ext'd (LBA)
/dev/sda5           13897       14593     5598621    b  W95 FAT32
/dev/sda6           14594       14602       72261    b  W95 FAT32
/dev/sda7           14603       19283    37600101   83  Linux
/dev/sda8           19284       19457     1397623+  82  Linux swap / Solaris


```

```

/dev/sda7 on / type ext3 (rw,relatime,errors=remount-ro)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
/dev/sda2 on /media/sda2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

```

off-topic. I guess the permanent-mount is global for all users and I use permissions to restrict access. right?
*edit* Wrong I guess since it's a FAT drive. Hmmm  - back to the question about whether I can mount a drive with read access for some and write for others.
Alan

---

