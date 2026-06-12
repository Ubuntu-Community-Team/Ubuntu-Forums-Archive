---
title: "Incorrect File System space reported by System Monitor"
date: 2011-04-03
forum: General Help
---

### Post by gdi2k on 2011-04-03
In System Monitor, on the File Systems tab, the "Total", "Available" and "Used" columns don't seem to add up, and the "Used" percentage doesn't seem correct either. 

My config: 
/dev/sda1 = 80 GB SSD drive, / partition. 
/dev/sdb1 = 50 GB FAT32 partition of an external 500 GB USB hard disk. 
/dev/sdb2 = remainder of the 500 GB USB hard disk encrypted using luks. 

Screenshot: 
[IMG]http://farm6.static.flickr.com/5134/5584253274_d63f691ecd_b.jpg[/IMG]

The /dev/sda1 figures don't really add up well, but they're close at least (how you get "50% Used" from any of those figures I don't know!).

However, for /dev/sdb2, they're miles off: 
"Free" = 146.2 GiB
"Total" = 409.7 GiB
"Available" = 125.4 GiB
"Used" = 263.5 GiB

Used + Available = 388.9 GiB, which is 20.8 GiB short of the stated 409.7 GiB total. Where did my GiBs go? 

df shows: 

```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             82969176  39955816  38798680  51% /
none                   1964284       528   1963756   1% /dev
none                   1974048     17648   1956400   1% /dev/shm
none                   1974048       228   1973820   1% /var/run
none                   1974048         0   1974048   0% /var/lock
/home/gdi2k/.Private  82969176  39955816  38798680  51% /home/gdi2k
/dev/sdb1             51174112        16  51174096   1% /media/50G-Win
/dev/mapper/udisks-luks-uuid-59e1ee00-8169-45a6-91da-3f7e2a6982d5-uid1000
                     429642500 276298220 131519628  68% /media/ee1450a9-7b4e-4c34-ba3d-ec392c69528e
```

Maybe it's something to do with the luks encryption?

---

### Post by mcduck on 2011-04-03
5% of space on Ext filesystems are by default reserved for root user only, so that isn't included in the amount of space available to your normal user.

For example your root partition:

38,2GB (used) + 36,9GB (available) + 0,05*79,1GB (reserved) = 79,055GB (total)

---

### Post by maverick555 on 2011-04-03
You may want to take a look at the difference between GB an GiB.Search google.

---

### Post by dcstar on 2011-04-03
> **mcduck said:**
> 5% of space on Ext filesystems are by default reserved for root user only, so that isn't included in the amount of space available to your normal user.
..........

That space is only available to the EXT filesystem for journaling etc., not the "root user".

---

### Post by mcduck on 2011-04-03
> **dcstar said:**
> That space is only available to the EXT filesystem for journaling etc., not the "root user".

No, the space used for journaling comes in addition to the reserved space.

The reserved blocks indeed are simply reserved for users (and services) with root permissions, to prevent normal users from filling the file system to the point where it's not possible any more to create new files on it (which would cause all kinds of problems and also result in the system not being to able to boot at all, as that requires creating some files).

You can even check that by comparing the amount of available space reported as normal user and as root user, and also configure the root-only reserved space with the tune2fs command. It's perfectly safe to set the amount to zero on any non-system partitions.

---

