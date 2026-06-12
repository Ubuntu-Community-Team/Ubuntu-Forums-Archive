---
title: "Created one partition, but it's not there"
date: 2012-03-31
forum: General Help
---

### Post by ridetheteapot on 2012-03-31
Hey sorry for the bad title, I couldn't think of a short description for my problem.
I just went to partition a new HDD with palimpsest (easily worst name ever imo) thinking that it would do the right thing.

After it finished ubuntu automounted the new partition (ext4/only one on disk) and I started to use it.
Now I see that either palimp did not create a partition table (or borked it), the device is mounted as /dev/sdc (no number) and has no type.

All I can think is that I never asked palimp to make a new mbr and this was the result. I can still use (mount/unmount/file ops) the partition and palimp still sees it, but no fdisk type tools see anything.

I have not yet done my due diligence but I just figured I would post here first to see if I could get a quick answer (cheater). I am guessing I need to create an mbr and tell it where my partition is (whole disk so no problem there).

This machine is ubuntu 10.10, palimp is 2.30.1

---

### Post by HiImTye on 2012-03-31
use GParted from a liveCD/USB

---

### Post by ridetheteapot on 2012-03-31
soz forgot to say can't gparted or f*disk

EDIT: don't need to use livecd or something, i can just unmount it, its not a system partition. I reread suggestion, and am curious what do you propose i do with gparted?

At this point i am pretty sure the only problem is no mbr (partition table is listed as type loop in parted -- parted is working on the drive).

---

### Post by Morbius1 on 2012-03-31
You get no output from:
```
sudo fdisk -l
```

How about this one:
```
sudo blkid -c /dev/null
```

---

### Post by ridetheteapot on 2012-03-31
yea blkid will give me an output
```
/dev/sdc: LABEL="bigting" UUID="fb3040f7-0e81-4583-a755-9d68cb4a0379" TYPE="ext4"
```

fdisk:
```
Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table
```

cfdisk:
```
FATAL ERROR: No partition table.
```

parted:
```
Model: ST1500DL 003-9VT16L (scsi)
Disk /dev/sdc: 1500GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  1500GB  1500GB  ext4

```

Although cfdisk doesn't play nice, I think I could create an mbr with it without messing up my partition, but I don't want to mess anything up further without being sure.

---

### Post by dandnsmith on 2012-03-31
At this point the thing is to save whatever you have of value on that filesystem. Then delete the filesystem and set up the HDD 'properly' using fdisk or (preferably) gparted.
You can then put back your saved files, and operate with that HDD normally.

---

### Post by ridetheteapot on 2012-03-31
I am just going to keep at it, this problem is a special annoyance. This is the only ubuntu box I have left - mostly is not used, and I didn't want file ops bothering my other machines for hours and hours.
Decided to use "disk utility" cause it was there :) and I wanted to take advantage of ubuntu simplicity. Just went ahead and clicked away (dumb) and got this issue. I got what I deserved I guess.

Anyway to have ubuntu's nice UI come back and bite me like that just gets me. I would have been 10 times better off doing it the way I always have rather than the easy way lol.

I will either fix this partition to play nice or I will clobber my last ubuntu install with arch as revenge. pacman -Rdd ubuntu.

_________

could not fix it. Could never figure out if moving the start of this weird partition would break it, so i didn't, but without moving it I cant write a new partition label with out wiping out some of the old data. I will just use your advice derek, then kill gnome/ubuntu to make myself feel better ;-P

---

