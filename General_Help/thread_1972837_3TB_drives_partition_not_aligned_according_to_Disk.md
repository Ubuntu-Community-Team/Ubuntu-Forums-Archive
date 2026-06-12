---
title: "3TB drives partition not aligned according to Disk Utility"
date: 2012-05-03
forum: General Help
---

### Post by jamesisin on 2012-05-03
I bought a pair of 3TB SATA drives to replace a pair of 1.5TB drives in my music server.  Whether I partition it (EXT4) with GParted or Disk Utility (Palimpsest) I am told (by Disk Utility) that my partition is not aligned:

> WARNING: The partition is misaligned by 3072 bytes.  This may result in very poor performance.  Repartitioning is suggested.

Currently I have only installed one of them and there is no data on it, so now is an excellent time to resolve this matter.

What am I supposed to do?

(FYI: I used GUID.)

---

### Post by CharlesA on 2012-05-03
Try recreating the partition with gparted and it should autoalign at 4096bytes.

---

### Post by jamesisin on 2012-05-03
> **jamesisin said:**
> Whether I partition it (EXT4) with GParted or Disk Utility (Palimpsest) I am told (by Disk Utility) that my partition is not aligned:

I tried using each.

---

### Post by CharlesA on 2012-05-03
> **jamesisin said:**
> I tried using each.
Huh.

What brand/model of drive is it and what version of Ubuntu?

---

### Post by jamesisin on 2012-05-03
It's Ubuntu 10.04 64bit and a Seagate ST3000DM001.

---

### Post by jamesisin on 2012-05-03
My research tells me GParted is SUPPOSED to align correctly (for a few years now), but I've tried several times from different angles and I keep getting that same error in DU.

---

### Post by CharlesA on 2012-05-03
Try using a 12.04 livecd to run gparted. I had issues with 10.04 handling 3TB drives. I think I ended up having to use 10.10 to get the partitions right, but that was a while ago.

Try 12.04 and see what happens.

---

### Post by jamesisin on 2012-05-03
10.04 runs 0.5.1 and it looks like maybe the alignment thing was fixed in 0.7 so...

I'm booting into 12.04 now.

---

### Post by CharlesA on 2012-05-03
That should fix it up fine.

---

### Post by jamesisin on 2012-05-03
Um, yeah...

There's an Align drop-down menu.  I think this might do it.

---

### Post by jamesisin on 2012-05-03
Just what the doctor ordered.  Thanks.  And so prompt...

---

