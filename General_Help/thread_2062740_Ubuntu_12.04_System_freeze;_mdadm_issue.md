---
title: "Ubuntu 12.04: System freeze; mdadm issue?"
date: 2012-09-25
forum: General Help
---

### Post by codemaster on 2012-09-25
So I've been having this wonky issue lately; it seems that my new Ubuntu 12.04 install freezes and it may be mdadm related.

My install is as follows:
4x750 GB drives, each partitioned the same: ext2 partition, swap partition, ext4 partition; the ext2 and ext4 are then RAID5'd together to have a single ext2 and ext4 partition, mounted on /boot and / respectively.

This usually works fine and dandy, but randomly freezes the entire system. I then reboot to usually find 2 drives randomly out of the array and have to force them back in and let it resync which is a huge pain.

I've looked around for a bit and noticed a few others have reported issues with mdadm freezes in 12.04 and many commented that using a new kernel fixed their issue... so I upgraded my kernel to 3.5.4, which did reduce the number of freezes, but they still occur regardless.

Was curious if anyone happened to know what may be going on and know of any good solutions?

Thanks! :)

**Edit**:
Here's my *uname -a*:
```
Linux cyrus 3.5.4-030504-generic #201209142010 SMP Sat Sep 15 00:11:50 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
```

and my mdadm status:
```

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md1 : active raid5 sdg2[3] sdf2[2] sde2[1] sdd2[0]
      11002368 blocks super 1.2 level 5, 512k chunk, algorithm 2 [4/4] [UUUU]

md2 : active raid5 sdg3[3] sdf3[2] sde3[1] sdd3[4]
      2185873920 blocks super 1.2 level 5, 512k chunk, algorithm 2 [4/4] [UUUU]
      [>....................]  resync =  1.4% (10771688/728624640) finish=154.4min speed=77486K/sec

md0 : active raid5 sdg1[3] sdf1[2] sde1[1] sdd1[0]
      437760 blocks super 1.2 level 5, 512k chunk, algorithm 2 [4/4] [UUUU]

unused devices: <none>

```

---

### Post by SaturnusDJ on 2012-09-26
Start by checking S.M.A.R.T. of the drives.

E.g.
```
smartctl -a /dev/sd[d-g]
```

One more thing:
It's said to be that it's better to not have /boot at a RAID5 array. RAID1 is preferred.

---

### Post by codemaster on 2012-09-27
I checked the SMART status of each of my disks and that actually helped immensely! It seems the SMART status passed for each one, but commented about overheating. Confused, I took a look inside my case and, sure enough, it looks like the case fan near the drives died out.

I've placed an order for a new fan and I think this will fix my issue. My belief is that my drives were getting way too hot, shutting down for safety, and thus degrading the array :)

Thanks for your help!

---

