---
title: "Help with LUKS 11.04 Alternate CD"
date: 2011-05-01
forum: General Help
---

### Post by steevven1 on 2011-05-01
So I set up Ubuntu 11.04 from the "alternate" CD and chose "Guided - use entire disk and set up encrypted LVM" during installation, but when the time came to choose a size for my encrypted partition, I chose 560 GB on my 640 GB hard drive, with the intention of creating another partition on the disk later.

Now that I have my computer all set up, I want to create this new partition. I want it to take up the entire remainder of the disk, and I don't really care whether it is covered under the LUKS encryption or not. I guess if it was equally easy, I would prefer it to be, but it does not actually matter.

My usual way of creating partitions (never had a LUKS volume before) is with GParted, but I can't seem to get anything to happen in there (shows only one partition, appears to be my entire drive...I read somewhere that GParted and LUKS do not play nice).

How can I create this new partiton? I want it to be FAT32 by the way, and have its own device label (ie /dev/sda4 or something). Thank you!

EDIT: I actually need the new FAT32 partition to be completely outside of LVM/LUKS, like a normal partition on the drive. Is this possible? Thanks!

---

### Post by MountainX on 2011-05-01
Are you familiar with "sudo fdisk -l"? Be careful with fdisk if you aren't experienced.

LVM offers a number of commands that will help you figure out where everything is and how much space is available. Some helpful commands are:

pvscan
pvs
vgscan
vgs
lvscan
lvs

You can also run the command "blkid"

Good luck.

---

### Post by steevven1 on 2011-05-01
Thanks. From "pvscan," I get:

```
  PV /dev/dm-0   VG steven   lvm2 [595.93 GiB / 74.39 GiB free]
  Total: 1 [595.93 GiB] / in use: 1 [595.93 GiB] / in no VG: 0 [0   ]
```

All the other commands you suggested seem to give me redundant information, just telling me that I have a 517 GB /root partition and a 3 GB /swap1 partition. All I want to do is take that 74 GB of free space and create a new FAT32 partition on it that will be accessible like any normal partition to any and all programs, etc.

Now that I think about it, I would really like to have my new, 74 GB FAT32 partition be outside the whole LVM/LUKS thing partition, unencrypted on the drive. Is there a way to do this? I imagine it involves shrinking the LVM area down so it has no "free" space left and then creating a partition in the usual way with GParted, etc. Any help is appreciated.

---

### Post by MountainX on 2011-05-01
Do you want to run a script to generate all the info about your disk? That output would probably help me give you some advice. I can't promise I know enough to tell you exactly how to solve your problem, but I can at least point you to the script.

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

Run this script (there's lots of help on running it in these forums). Paste the output here.

If I can't help, the script output will let someone else help you better. But I'll take a look and try to help after you paste the output.

---

