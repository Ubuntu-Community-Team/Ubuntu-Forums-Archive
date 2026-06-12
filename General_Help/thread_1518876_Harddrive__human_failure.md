---
title: "Harddrive / human failure"
date: 2010-06-27
forum: General Help
---

### Post by elsdyr on 2010-06-27
Hi everybody, I need some advise. I'm posting here, because I didn't see any of the categories fit.

So the story goes as this:

I was installing two new Seagate disks at 1.5 TB each, setting up some mirroring software RAID, so I (at last) could back up all my stuff from my main harddrive (160 GB) and some spare disks. Every thing went fine, and I ended up with a copy of my /home on the RAID device, and a renamed original on the main disk (mv /home /home2). System was running fine.

But then

One of the Seagate disks started the well known *click-of-death". I went to the support forums, and other places through Google, and found, that Seagate had made some new disks with an enormous failing rate. Disks of which I had bought two. Great. But no biggie, because I had the original data on the main disk, and the disks still worked though they were now  very slow.

I copied the stuff from the sparedisks back to the sparedisks, and before I made the RTM, I would wipe the disks, so noone would be able to get hold of my private data. I found the shred command and checked everything. So I started it on the /dev/sdb1 and /dev/sdc1 which all the time have been my raid partitions. And it looked alright - many hours to go, and I left the computer.

While I was away I became a bit paranoid, and went back, stopped the shred-command (at 14% on both disks) to check, that I'd made a backup of the data on the spare disks, by rebooting and installing and verifying data was on them too. Everything was fine, so I rebooted again and disconnected the spare disks. Started Ubuntu and the run the shred command once again and left once again.

When I came back, I saw one of the was 14% done but the other 76%  .... how could that b.... OH NOES! For some reason my main disk had suddenly become /dev/sdb instead of the one my RAID device - for the only time in at least 20 reboots.

So what I got is:
160 GB with 76% random data from 1 pass out of 3
2 * 1.5 TB mirrored disks 14% random data from 1 pass out of 3

```

root@ubuntu:~# fdisk -l
[...]
Disk /dev/sda doesn't contain a valid partition table
```Trying with the RAID disks gives the same result.

**What are my options?**

I suppose my best chance are, that the data is stored in remaining 86% of the RAID devices, but how do I access them in this situation?

Since Shred pr. default runs 3 passes, does that mean, that someone *probably* can recover my data since it has only run (under) 1 pass? Who are these people, and how much would it at least cost me?

Any respond is appreciated. Thank you for reading.



tl;dr
Learn to make backups before you install backup solutions.

---

### Post by dabl on 2010-06-27
You aren't trying to use the onboard SATA RAID controller on your motherboard, are you?  Unless it came with a Linux driver, that won't work.  I haven't ever set up a "dmraid" software RAID set in Linux, so I can't help with that.  But, for the hard disk that lost its partition table, you should be able to use GParted and make a new one.  "Device" > "New Partition Table".

---

### Post by elsdyr on 2010-06-28
Thanks for the quick answer!

No, I was using software raid through mdadm, and it worked like a charm -- for one day.

Does writing a new partition table not make a clean filesystem without references to my old files?

---

### Post by dabl on 2010-06-29
> **elsdyr said:**
> 

Does writing a new partition table not make a clean filesystem without references to my old files?

Writing a new partition table is a low-level operation, analogous to MS-DOS "FDISK".  It does not make a filesystem, it merely prepares the hard drive to handle/translate partitioning operations, and then on to the filesystem(s), should one be installed on a partition.

So, the sequence of operations, moving from lowest to highest level, is:

- partition table creation  (destroys any prior partition information)
- partition creation (destroys any prior partition or filesystem information)
- filesystem creation (destroys any prior data information)
- save a file on the filesystem

As you can see, there's no user data involved, until the highest level operation.  Any of the lower-level operations will nuke your data, so it should be safely backed up elsewhere before you execute any of these operations.

---

