---
title: "Ubuntu 10.10 2.6.35-28 kernel does not assemble md devices correctly."
date: 2011-06-12
forum: General Help
---

### Post by sheldonl on 2011-06-12
I'm on Ubuntu 10.10, when I tried to boot with the 2.6.35-28 kernel, for some reason on boot md tries to assemble my devices incorrectly, using the whole devices rather than the partitions. The software raid device starts, but then LVM cannot find the disk group.

e.g. Here is the output from dmesg on the 2.6.35-27 kernel, which does work properly:

 md/raid:md0: device sdf**1** operational as raid disk 1
 md/raid:md0: device sde**1** operational as raid disk 0
 md/raid:md0: device sdd**1** operational as raid disk 2
 md/raid:md0: allocated 3179kB
 md/raid:md0: raid level 5 active with 3 out of 3 devices, algorithm 2
 RAID conf printout:
  --- level:5 rd:3 wd:3
  disk 0, o:1, dev:sde**1**
  disk 1, o:1, dev:sdf**1**
  disk 2, o:1, dev:sdd**1**
 md0: detected capacity change from 0 to 2000407494656
  **md0: unknown partition table**

Here is the output form 2.6.35-28 which does **not** work properly:

md/raid:md0: device sdd operational as raid disk 2
 md/raid:md0: device sdf operational as raid disk 1
 md/raid:md0: device sde operational as raid disk 0
 md/raid:md0: allocated 3179kB
 md/raid:md0: raid level 5 active with 3 out of 3 devices, algorithm 2
 RAID conf printout:
  --- level:5 rd:3 wd:3
  disk 0, o:1, dev:sde
  disk 1, o:1, dev:sdf
  disk 2, o:1, dev:sdd
 md0: detected capacity change from 0 to 2000407494656
  **md0: p1**

My md0 device should not have a p1 partition on it!

Anyone else experience this problem?

---

