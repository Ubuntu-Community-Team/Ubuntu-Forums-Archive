---
title: "Raid 0 vs separate disk for /home performance"
date: 2011-10-22
forum: General Help
---

### Post by e79 on 2011-10-22
Let's say I have 2 x 500GB hard disk, both running at 7200 rpm and having 32Mb of cache. Performance wise, what would be the best configuration between:

1. Raid 0, stripping data across both disks.

2. Separate disk for /home.

I must add few things :

The rig would be running test virtual machines 24/7 (not mission critical, no production machines), would be used to play games and download/seed torrent (Linux ISO mostly) and lastly, I don't care about redundancy as I would regularly back it up.

I'm curious about people's opinion on this subject.

Regards,

e79

---

### Post by e79 on 2011-10-24
Bump.

---

### Post by ratcheer on 2011-10-24
RAID 0 helps the most for very large files that must be read a lot at once. Then, chunks of the file can be read from one disk, then the other, etc, speeding up the entire process. In a large database processing environment, I have used some very wide stripesets of 35 or more disk drives. Of course, the disk controllers must also support this kind of operation, in some cases even requiring special multipathing software.

This is probably more than you need to know. The main thing is, if you require large files to be read in their entirety (or in large part) as quickly as possible, consider disk striping. Also, if you need to write large files, quickly, the same applies.

Tim

---

### Post by dcstar on 2011-10-25
> **e79 said:**
> Let's say I have 2 x 500GB hard disk, both running at 7200 rpm and having 32Mb of cache. Performance wise, what would be the best configuration between:

1. Raid 0, stripping data across both disks.

2. Separate disk for /home.

I must add few things :

The rig would be running test virtual machines 24/7 (not mission critical, no production machines), would be used to play games and download/seed torrent (Linux ISO mostly) and lastly, I don't care about redundancy as I would regularly back it up.

I'm curious about people's opinion on this subject.


"RAID 0" is the exact opposite of RAID, it statistically doubles the risk of data loss as if either disk dies, you lose the lot.

My "opinion" is that anyone using RAID 0 has rocks in their head unless they readily acknowledge that any data on one of these things is of such low value to them that they don't really care about it much at all.

---

### Post by Drenriza on 2011-10-25
> **dcstar said:**
> "RAID 0" is the exact opposite of RAID, it statistically doubles the risk of data loss as if either disk dies, you lose the lot.

My "opinion" is that anyone using RAID 0 has rocks in their head unless they readily acknowledge that any data on one of these things is of such low value to them that they don't really care about it much at all.

Just take backups? I have no problem using RAID 0 myself. But of course i would backup the disks and use high quality disks. Since if one "dies", you "loose" everything.

---

### Post by ratcheer on 2011-10-25
If reliability is required, always use RAID 10 instead of RAID 0. That is how I ran my databases. Of course, it requires twice as many disks.

Tim

---

### Post by e79 on 2011-10-25
Thanks for your input everyone, it is most appreciated !

  > **dcstar said:**
> 11390928My "opinion" is that anyone using RAID 0 has rocks in their head unless they readily acknowledge that any data on one of these things is of such low value to them that they don't really care about it much at all.

I do have rocks in me head, but as I do regular  backups (clones, sync etc), I don't really care, I can restore my system within minutes.

---

