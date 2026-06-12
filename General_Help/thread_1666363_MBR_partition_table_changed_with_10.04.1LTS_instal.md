---
title: "MBR partition table changed with 10.04.1LTS install"
date: 2011-01-13
forum: General Help
---

### Post by GMHilltop on 2011-01-13
I have never seen this before wit any previous versions of ubuntu - wondering if anyone else has seen it or can explain it.
 
 The break down of the partition table is being viewed with Ranish  Partition v2.43  It's old program, but it has been really handy.
 
 What is happening is:
 
 Prior to the install of ubuntu on the 3rd Primary partition, you'll see  that the 4th partition (which has a couple of logical partitions in it)  starts at:
 (14,380 - 0 - 1) ===> Cylinder - Head - Sector
 
 After the installation of Ubuntu 10.04.1 LTS it shows a Non-conventional start point of:
 (14,380 - 0 - 62) =====> Cylinder - Head - Sector.
 
 An unused is left between the 3rd and 4th Primary partition.
 
 This is not a big deal - just unusual (IMO)
 
 With the same partition layout (pre install) It doesn't matter if I  install ubuntu on the 1st, 2nd, or 3rd primary partition.  The 4th one  ALWAYS gets changed this way.
 
 Does anyone have any Idea why this is happening?  Is it a Bug?

---

### Post by GMHilltop on 2011-01-13
Sorry forgot the attachments.

---

### Post by srs5694 on 2011-01-13
It looks to me like something in the Ubuntu installer is changing the start of the extended partition to match start point of the first logical partition in the extended partition. (The extended partition must begin at least one sector before the first logical partition it contains.) I'd be reluctant to call this a bug, since it's not an illegal change and it's conceivable that the program's author had a reason to make the change -- either a specific reason for it to be done this way or as a side effect of the way the data structures are manipulated in memory. That said, it could conceivably have undesirable side effects down the road if some other partitioning software doesn't like the new layout.

As a side note, I'll point out that cylinder/head/sector (CHS) numbers are no longer used by modern software, since the MBR data structures max out at 1,024 cylinders, 63 sectors, and 255 heads, for a maximum disk size of 7.8 GiB (1024 x 63 x 255 x 512 bytes = 7.8 GiB). The software you're using is clearly translating the LBA values (which max out at 2^32 sectors, or 2 TiB) to CHS values. IMHO, in today's world this is pointless and perhaps a bit confusing; it's better to just deal with LBA directly rather than present the illusion that the reported CHS values are directly represented on the disk structures.

---

