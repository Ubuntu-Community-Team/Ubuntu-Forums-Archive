---
title: "Software raid: worth it?"
date: 2010-08-15
forum: General Help
---

### Post by antar on 2010-08-15
So I'm about to build myself a new computer (Newegg and Microcenter are wonderful things). It's going to have one of those 6-core AMD 3.2 GHz processors and 2x 1TB drives.

The reason for the 2x drives is not because I particularly need 2TB of storage (that's what my externals are for), but because I want a backup drive in case one of them fails.

Now the question is whether I mean backup as in rsync or backup as in RAID 1, implemented in software. I understand that Software RAID implementations make use of the CPU. My question is if anyone can tell me, if I have a 6-core setup, am I going to particularly NOTICE the lost CPU cycles? What kind of CPU usage will I be seeing if I implement Software RAID?

As always, thanks.

---

### Post by cascade9 on 2010-08-17
2 x 1TB drives for 2TB would be RAID0, so you would get no backup at all. You would want RAID1 for 1TB, or better yet 3 x 512GB/1TB drives for 1TB/2TB. 

You wouldnt notice the extra CPU use with a CPU like that, but you might notice the higher latency with RAID0/1/5 or the slightly slower than standard transfer rates (compared to a single drive of the same type) on RAID1.

---

### Post by antar on 2010-08-17
Thanks for the advice.

---

