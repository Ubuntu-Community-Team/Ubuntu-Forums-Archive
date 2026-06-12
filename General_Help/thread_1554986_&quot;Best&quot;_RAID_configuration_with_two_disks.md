---
title: "&quot;Best&quot; RAID configuration with two disks"
date: 2010-08-17
forum: General Help
---

### Post by trotur on 2010-08-17
Hello everyone!

I have two similar 1 TB hard disks and I'm planning to configure them using RAID. I want to back up reliably all my personal files so I'm going to use RAID1 for /home.

As the system files aren't irreplaceable, I was thinking to use RAID0 for the root directory. My question is: will this give me any performance boost? As far as I know, using either RAID0 or RAID1 would double read speeds and thus in both configurations boot-up time (for example) would be equally fast. Is this true in practice? If both RAID0 and RAID1 have equal read speeds, I'm planning to use RAID0 only for /tmp and swap.

Another thing that I was wondering is that if I'm using RAID0 for / and another disk fails, will there be some difficulties to recover my home folder that was mirrored in RAID1? If I'm using RAID0 only for /tmp, am I able to recover whole system without reinstalling Ubuntu?

---

### Post by DeMus on 2010-08-17
> **trotur said:**
> Hello everyone!

I have two similar 1 TB hard disks and I'm planning to configure them using RAID. I want to back up reliably all my personal files so I'm going to use RAID1 for /home.

As the system files aren't irreplaceable, I was thinking to use RAID0 for the root directory. My question is: will this give me any performance boost? As far as I know, using either RAID0 or RAID1 would double read speeds and thus in both configurations boot-up time (for example) would be equally fast. Is this true in practice? If both RAID0 and RAID1 have equal read speeds, I'm planning to use RAID0 only for /tmp and swap.

Another thing that I was wondering is that if I'm using RAID0 for / and another disk fails, will there be some difficulties to recover my home folder that was mirrored in RAID1? If I'm using RAID0 only for /tmp, am I able to recover whole system without reinstalling Ubuntu?

RAID 0 gives you extra speed but NO security.
RAID 1 gives you security but NO extra speed.

RAID 0 gives you the full 2TB (2 times 1 TB),
RAID 1 gives you 1TB, but doubles it (original and back-up)

---

### Post by trotur on 2010-08-17
> **DeMus said:**
> RAID 0 gives you extra speed but NO security.
RAID 1 gives you security but NO extra speed.

RAID 0 gives you the full 2TB (2 times 1 TB),
RAID 1 gives you 1TB, but doubles it (original and back-up)

Thanks for a fast reply.

Wikipedia states that in RAID 1 "[increased read performance occurs when using a multi-threaded operating system that supports split seeks]("http://en.wikipedia.org/wiki/RAID")". Is this true when using Linux software raid?

I think 1 TB is enough for me (at the moment), so I'm not worried about losing other 1 TB for mirroring. I'm seeking configuration that backs up my personal data (so RAID 1 for /home).

Some performance increase in other things would be a nice bonus so RAID 0 might be a viable option for the root directory. But I think that Ubuntu mostly reads files at boot-up so if RAID 1 would give me equal read speed, it might be better to use it (whence system recovery in the case of disk failure would be easier).

---

### Post by DeMus on 2010-08-17
> **trotur said:**
> Thanks for a fast reply.

Wikipedia states that in RAID 1 "[increased read performance occurs when using a multi-threaded operating system that supports split seeks]("http://en.wikipedia.org/wiki/RAID")".

Well, I didn't know that and to be honest I doubt it. What happens with RAID 1 is that data is simultaneously written to both disks. When it is possible to gain speed this way, the same profit could be made by using a "normal" disk, since data is written the same way to disk, only at the same time it is also written to the other disk. How do you gain speed then?

---

### Post by trotur on 2010-08-17
> **DeMus said:**
> Well, I didn't know that and to be honest I doubt it. What happens with RAID 1 is that data is simultaneously written to both disks. When it is possible to gain speed this way, the same profit could be made by using a "normal" disk, since data is written the same way to disk, only at the same time it is also written to the other disk. How do you gain speed then?

Write speed may only be reduced in RAID 1 (reduction may happen if other disk is slower than another). But read speed may be doubled if software is wise enough to read half of the data from the first disk and simultaneously other half from the second disk.

Question remains whether software raid in Linux is that wise.

---

### Post by Quackers on 2010-08-17
As I understand it, in raid1 data is only being read from the first disc so speed is unaffected. The second disc is effectively a backup of the first disc and is not consulted when reading data. Any written data is being written once to each disc in entirety (so written twice at the same time).
In raid0 data is being written and read simultaneously (half to each disc) so speed is increased. But if one disc fails ALL data is lost.
If you want to run raid0 AND raid1 I would imagine you would need 2 raid controllers. With only one raid controller you can only choose either raid0 OR raid1 - not both.

---

### Post by realzippy on 2010-08-17
*Question remains whether software raid in Linux is that wise*

Seems to be :
[I]
"RAID1 can be just as fast as RAID0 as for reading, because it could read in the very same way as RAID0's do. Better yet, since all disks contain all data, there is no requirement anymore to read from a specific disk; as both disks contain the same data striping can be done more efficiently.

So, RAID1 should be faster than RAID0 for random read, and at least the same as for sequential read. Unfortunately, only UNIX RAID drivers like geom_mirror implement things like load balancing and round robin algoritms on the RAID1 layer.

Even Areca hardware RAID doesn't profit alot from RAID1. And all onboard-RAID do not employ any optimizations for RAID1, causing it to slowdown to the speed of a single disk. Perhaps Intel ICHxR drivers will be a little better, but i doubt they can profit from RAID1 potential as the GEOM storage layer does in the FreeBSD operating system.

So short answer: no, Windows does not offer any advanced storage technology, like Linux/BSD do. "[/I]

from:
[http://www.tomshardware.co.uk/forum/250390-14-does-raid-increase-read-speed]("http://www.tomshardware.co.uk/forum/250390-14-does-raid-increase-read-speed")

---

### Post by Quackers on 2010-08-17
I don't think "striping" is used in any way in raid1. It is a raid0 method.

---

### Post by dcstar on 2010-08-18
> **DeMus said:**
> RAID 0 gives you extra speed but NO security.
.........

Wrong - "RAID 0" HALVES the statistical reliability of the combined drive and guarantees that you lose ALL your data if either drive fails.

"RAID 0" is actually the opposite of RAID as it has nothing whatsoever to do with redundancy and should never be used in any discussion where any sort of increased reliability is the desired outcome.

---

### Post by mixmaster on 2010-08-18
99% of the time you will not notice the speed difference between raid0, raid1 and jbod.  If you have a failure on boot and you are on a raid0 filesystem you will waste more time fixing it that you will save in a century of gains from the use of RAID0.

If you need max security go to RAID1 for everything.  If you need capacity install as 2 independent disks and make sure all vital data exists on filesystems on both disks.

---

### Post by trotur on 2010-08-20
Thanks for the comments.

For two disks there seems to be two different mirroring schemes in Linux software RAID.

Standard RAID1: "[Read performance is good, especially if you have multiple readers or seek-intensive workloads. The RAID code employs a rather good read-balancing algorithm, that will simply let the disk whose heads are closest to the wanted disk position perform the read operation.]("http://nst.sourceforge.net/nst/docs/user/ch14.html")"

RAID10, "far" layout: "[This is designed for striping performance of a mirrored array; sequential reads can be striped, as in RAID-0, random reads are somewhat faster.]("http://en.wikipedia.org/wiki/Non-standard_RAID_levels#Linux_MD_RAID_10")"

---

### Post by Slonda828 on 2010-08-20
Personally, I would RAID one those drives. I'm lazy, and if one of those drives gives up the ghost, you can just plug a new one in and watch the RAID controller do its magic. Besides, on drives that big, you are not going to, in my personal experience, notice a whole heck of a lot of performance gain with a RAID 0 and if one drive craps out then you just lost all your data. 
 
I administer about 20-some servers with RAIDs on them, and nobody generally uses RAID 0.

---

### Post by trotur on 2010-08-20
> **Slonda828 said:**
> Personally, I would RAID one those drives. I'm lazy, and if one of those drives gives up the ghost, you can just plug a new one in and watch the RAID controller do its magic. Besides, on drives that big, you are not going to, in my personal experience, notice a whole heck of a lot of performance gain with a RAID 0 and if one drive craps out then you just lost all your data. 
 
I administer about 20-some servers with RAIDs on them, and nobody generally uses RAID 0.

I agree with that it may be the best option to put RAID1 for the whole drive and keep things simple and reliable.

---

