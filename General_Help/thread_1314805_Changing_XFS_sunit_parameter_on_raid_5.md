---
title: "Changing XFS sunit parameter on raid 5"
date: 2009-11-04
forum: General Help
---

### Post by Zeratul021 on 2009-11-04
Hi all,

I would like to ask something regarding XFS and RAID 5:

I've built raid 5 from 4 1TB devices using 256KB chunk size.
I wanted to tweak XFS on it a little so i formatted it with

```

mkfs.xfs -f -L DATA -l internal,size=128m -d agcount=30,su=256k,sw=3 /dev/md0
```

Problem is that output shows:
```

eta-data=/dev/md0               isize=256    agcount=30, agsize=24419072 blks
         =                       sectsz=4096  attr=2
data     =                       bsize=4096   blocks=732571776, imaxpct=5
         =                       sunit=64     swidth=192 blks
naming   =version 2              bsize=4096   ascii-ci=0
log      =internal log           bsize=4096   blocks=32768, version=2
         =                       sectsz=4096  sunit=1 blks, lazy-count=0
realtime =none                   extsz=786432 blocks=0, rtextents=0

```
That's not exactly sunit that I wanted (should be 512 and swidth 1536).
Even if I try to mount it with these options set to proper numbers, xfs_info still provides same output.

Any ideas or suggestions why this happens?

Regards,

Marek

---

