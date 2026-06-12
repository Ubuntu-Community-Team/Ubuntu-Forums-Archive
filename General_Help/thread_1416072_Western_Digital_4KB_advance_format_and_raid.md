---
title: "Western Digital 4KB advance format and raid"
date: 2010-02-25
forum: General Help
---

### Post by lohertz on 2010-02-25
There's a whole lot of talk about Western Digital's EAR series hard drives. These disk use 4096B logical and physical sector.  Issues arise with misalignment and such with the filesystem starting on LBA 63 whereas the 4KB sector starts on 64(?).

I'm looking at setting up a raid 0 on an Intel D945GCLF2 Atom board and using a paid of the WD 15EAR Green Drives for data storage.  The OS will be on a separate drive.

I'm a real newbie to this stuff, but willing to learn.  Any help, guide, tutorial would be much appreciated

---

### Post by dabl on 2010-02-25
I'm not an expert, but I saw this the other day: [http://www.osnews.com/story/22872/Linux_Not_Fully_Prepared_for_4096-Byte_Sector_Hard_Drives](http://www.osnews.com/story/22872/Linux_Not_Fully_Prepared_for_4096-Byte_Sector_Hard_Drives)

I think I also gathered that the version of GParted in *buntu 9.10 does not allow for the needed optimization. But I believe the newer version does -- that's the one you want.  Maybe the Parted Magic or GParted Live CD would provide it.  If you can get it partitioned and formatted appropriately, Linux will run fine.

EDIT:  Here's more on GParted:  [http://parted.alioth.debian.org/cgi-bin/trac.cgi/ticket/251](http://parted.alioth.debian.org/cgi-bin/trac.cgi/ticket/251)

---

