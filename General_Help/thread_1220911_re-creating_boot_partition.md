---
title: "re-creating boot partition"
date: 2009-07-23
forum: General Help
---

### Post by shumi12321 on 2009-07-23
I had to delete my boot partition in order to install winXP on my linux machine as second os.

I succesfully installed XP on last partition on my hard drive (it wasn't easy), but now i have the problem with re-creating my boot partition.

Here is a list of drives printed by fdisk:
```
Device        Boot    Start    End        Blocks    Id    System
/dev/sda1        14    7662    ...        83    Linux
/dev/sda2        7663    16634    ...        5    Extended
/dev/sda3        9321    9396    ...        82    Linux swap / Solaris
/dev/sda4    *    18179    20023    ...        7    HPFS/NTFS
/dev/sda5        7663    9320    ...        83    Linux
/dev/sda6        9397    11487    ...        83    Linux
/dev/sda7        11488    11997    ...        83    Linux
/dev/sda8        11998    12397    ...        83    Linux
/dev/sda9        12380    12634    ...        83    Linux
/dev/sda10        12635    12685    ...        83    Linux
/dev/sda11        12686    13153    ...        83    Linux
/dev/sda12        13154    16634    ...        83    Linux
```when I try to create a new partition in rescue mode with fdisk, i get an error "No free sectors available" :(

Any ideas?

---

