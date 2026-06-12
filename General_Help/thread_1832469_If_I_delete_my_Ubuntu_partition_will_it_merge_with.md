---
title: "If I delete my Ubuntu partition will it merge with my other unallocated partition?"
date: 2011-08-24
forum: General Help
---

### Post by Shvesley on 2011-08-24
I just deleted Windows 7 and I now have 98 GB of unallocated space. I want to delete my remaining partition (Ubuntu) so I can re install Ubuntu 64 bit as my main partition. If I delete my Ubuntu partition will the unallocated space merge with my old windows 7 partition or will I be stuck with 2 unallocated partitions?

---

### Post by 8jwong14 on 2011-08-24
> **Shvesley said:**
> I just deleted Windows 7 and I now have 98 GB of unallocated space. I want to delete my remaining partition (Ubuntu) so I can re install Ubuntu 64 bit as my main partition. If I delete my Ubuntu partition will the unallocated space merge with my old windows 7 partition or will I be stuck with 2 unallocated partitions?

When I read the title, I'll admit I got a bit nervous.  I believe that the unallocated space will merge.  Are you using GParted by the way?

---

### Post by dave01945 on 2011-08-24
yeah unallocated space will merge but if there is still a partition it will not or if there is a partition in the middle of the 2 unallocated pieces they will not merge

---

### Post by oldfred on 2011-08-24
It is best to delete partitions and create the partitions you want in advance. Then you have control over sizes. A smaller system partition and larger /home is slightly better as the drive does not have to search as far for the most used files.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

### Post by coffeecat on 2011-08-24
Unallocated space is unallocated space. If you delete two partitions which are adjacent, you don't get two lumps of unallocated space; you simply get one big lump of unallocated space. Unallocated space doesn't merge in the sense of merge being a process - it's just unallocated space. And there's no such thing as an unallocated partition. You can have an empty partition without a filesystem, but that's just a partition that hasn't been formatted; it's not unallocated space.

However, if you have two lumps of unallocated space separated by a partition, then you have - well - two lumps of unallocated space.

The best way to see what is going on at each stage of the process is to look at what the Gparted window displays. That shows graphically the status of your hard drive and is easier to follow than any words.

---

### Post by Shvesley on 2011-08-24
Gparted looks like this....

/dev/sda1      /dev/sda2        unallocated      /dev/sda4 
 43.95          100 mb            98.92          /dev/sda5
 Ubuntu      SystemReserve      Used2Be Win7      6.09 gb
                                                 Linux-Swap

I want to delete /dev/sda1 and then re install Ubuntu 11.04 64 bit on all of the allocated space.

---

### Post by Shvesley on 2011-08-24
Sry for the weird formatting on the last post

/dev/sda1 43.95 gb Ubuntu       

/dev/sda2 100mb SystemReservem

unallocated 98.92 gb Used toBe Win7
                    
/dev/sda4 6.09 gb               
      /dev/sda5    Linux-Swap           

I want to delete /dev/sda1 and then re install Ubuntu 11.04 64 bit on all of the allocated space.

---

### Post by Shvesley on 2011-08-24
The system rerserve is in between the partitions that are going to be unallocated. Is that a problem?

---

### Post by coffeecat on 2011-08-25
> **Shvesley said:**
> The system rerserve is in between the partitions that are going to be unallocated. Is that a problem?

Not necessarily. The partition numbers do not always come in order, particularly if you have done some partitioning already. Partition sda2 could still be at the beginning of the drive, and if that's the Windows 7 SYSTEM partition, it would be unusual to have it 44GB into the drive. Also - if that is the SYSTEM partition and you have deleted the Windows 7 C: drive, you won't need it anyway.

Post one of these.

Open a terminal and post the output of:

```
sudo fdisk -lu
```

Or post a screenshot of the Gparted window. Or post both.

---

### Post by grahammechanical on 2011-08-25
Do not forget, the partitioner will let you move partitions. So, you can move sda2 100Mb Systemreserve through the unallocated space. Then if you want you can expand sda1 to take up the unallocated space.

Or, if you want, shrink sda1 to about 20-25GB which is where you will install Ubuntu with a mount point of / and create a new partition from the unallocated space which you give a mount point of /home. This puts your home folder on a separate partition which is useful in case you ever need to re-install Ubuntu. You do not loose your data or system settings.

Do not forget to give the present swap partition (sda5) the mount point of /swap otherwise the install process might create an additional swap partition leaving this one unused and taking up space.

Regards.

---

### Post by Shvesley on 2011-08-25
The Output was...


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007c434

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    92162047    46080000   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda4       299810814   312580095     6384641    5  Extended
/dev/sda5       299810816   312580095     6384640   82  Linux swap / Solaris

---

### Post by Shvesley on 2011-08-25
Can I delete sda4 and sda5 and then delete sda1 and then boot from a usb?

---

### Post by cryptotheslow on 2011-08-25
I'd be a little cautious about moving the SystemReserve partition if it's a manufacturer installed restore image or the likes. Any restore function / software may expect it to be in a particular place....  not likely, it should just use the partition label, but one never knows!

With that layout - and having made sure I'd **backed up everything I needed to keep** - I think I'd get rid of sda1, sda4 and sda5. Then reinstall using the 48GB for the / filesystem and put /home the other side of the SystemRestore partition, with just enough at the end for a swap partition (2x RAM size if you intend to hibernate).

Without knowing what's in that SystemReserve partition it's hard to advise any other approach really...   seems like an odd place for a restore partition to be - usually they are right at the start or end of the drive.

You will need to boot from the USB then select Try Ubuntu, before using GParted to remove sda1,4,5 as they will be mounted and undeletable if you boot to the install already on the drive. Simplest just to go straight to the liveUSB and do it all from there.

I'll say again - **backup everything you need** to some external media before you begin :D

---

### Post by Shvesley on 2011-08-25
SOLVED. I deleted linux-swap, and deleted sda1 during installation.

---

