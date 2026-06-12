---
title: "Filesystem Quandries...!"
date: 2010-09-10
forum: General Help
---

### Post by Psychobiker on 2010-09-10
Hi all,

I'm a long-time fan of Ubuntu, and have it running on a media-serer type box for music/DVD etc. 
Now, I have also a MacBook (10.6) to which I had connected a hard drive formatted to HFS (When I bought it, I had no idea about journaling!) which is journaled. OK, so i managed to remove the journaling from within OSX, but now OSX refuses to a) repair or b) mount the damned thing.

However, within Linux, it will mount fine (Read only) and gPartEd will show up the very large HFS+ partition perfectly - but there are two smaller partitions (ext3) and a little unallocated space. I presume this was once occupied solely by some other sector of HFS used by OSX to...do something.

Forgive me if I'm wrong, but I think the safest way forward with this slightly upset partition table would be to buy another HDD, transfer the data from the readable HFS+ portion and reformat the original drive in NON journaled HFS+, which can then be read/written from both OSes?

I'm worried to go re-writing the segments with gparted...and it seems too big a risk just for the ability to mount it in OSX.

L

---

