---
title: "How to get disks to standby?"
date: 2010-11-29
forum: General Help
---

### Post by stefangr1 on 2010-11-29
I have a network server with 4 harddisks. To save energy, I'd like to spin them down when they're not used.

If I specify "hdparm -S 24 /dev/sda", however, nothing happens... (after 2 minutes).

What am I doing wrong...

PS: the disks I'm trying to spin down do not have the OS or a swap partition (don't have one) on them.

---

### Post by mikewhatever on 2010-11-29
I think you should add the '-B' switch.

_from man hdparm_
> -B     Query/set  Advanced  Power Management feature, if the drive supports it. A low value means aggressive power management and a high value means better performance.  **Possible settings range from values  1  through  127 (which  permit  spin-down), and values 128 through 254 (which do not permit spin-down)**.  The highest degree of power management is attained with a setting of 1, and the highest I/O performance with a setting of 254. A  value  of  255 tells hdparm to disable Advanced Power Management altogether on the drive (not all drives support disabling it, but most do).


Something like the following should do it,

hdparm -B X -S 24 /dev/sda,

where X ranges from 1 to 127.

---

