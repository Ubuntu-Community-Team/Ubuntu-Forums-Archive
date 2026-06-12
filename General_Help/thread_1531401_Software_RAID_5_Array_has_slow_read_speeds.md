---
title: "Software RAID 5 Array has slow read speeds"
date: 2010-07-14
forum: General Help
---

### Post by cj.surrusco on 2010-07-14
I set up software RAID 5 on three 7200rpm Seagate Barracudas (2x80GB, 1x40GB) with 40 GB partitions on the beginning of all three disks.

Now, when I do benchmarks using the Disk Utility I get about 52 MB/s read speed on the array. This seems kinda slow considering the average read speed on each individual drive is about 48 MB/s. 

Also, boot up takes about 30 seconds, which is the same as when I had Ubuntu installed on just one of the 'cudas, without RAID. 

Now, I am I missing something? Shouldn't the read speed be more that twice as fast since it can read from all three disks?

Any insight on this situation would be greatly appreciated.

Thanks in advance,

cj.surrusco

---

### Post by cj.surrusco on 2010-07-21
I have not found out why the RAID array was so slow, but adding a fourth hard drive with about the same specs bumped the read speed up to almost 150 MB/s.

I wouldn't really call it a solution to the problem, but it is fast enough now with the additional drive attached.

---

