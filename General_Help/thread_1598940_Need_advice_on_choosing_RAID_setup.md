---
title: "Need advice on choosing RAID setup"
date: 2010-10-17
forum: General Help
---

### Post by peap on 2010-10-17
I will be setting up a headless file & web server with low-medium use at home hosting all my video/audio/photos/documents/important stuff.

I will be using 2x1GBit linked (802.3ad) NICs and I want my HDD setup to be up to par with the NICs when it comes to read/write speed.
I will be using 8x2TB 5900rpm drives (or possibly 6 of those plus 2 faster drives) and Ubuntu software RAID.

What are your thoughts on my two alternatives below? Should I consider any other setups?

1. All 8 drives in a RAID 10 array holding the root file system and all data served to the LAN/WAN. 8TB in total.

2. 6 drives in a RAID 6 array holding all the data and two faster drives in a RAID 1 array hosting the root file system. 10TB in total.

Is the first alternative just plain overkill?
I'm afraid the RAID 6 array will suffer from very slow writing speeds but after hours of googling I can't seem to find any exact numbers on the RAID 6 write penalty using ubuntu software raid. 

As price is a factor I will not be able to go for 8 "faster" drives nor hardware RAID.

---

### Post by peap on 2010-10-17
No thoughts on this?

---

