---
title: "partitioning"
date: 2011-09-20
forum: General Help
---

### Post by concretecork on 2011-09-20
I have just added another hard drive to my desktop. Total of two. I was wanting to set them up as raid 0 so that it would be like having one hard drive. I have found a tutorial on this with ubuntu 11.04 but the tutorial is not accurate. It says to click on manual after getting to partitioning section. there is not manual button. I tried to set it up manually but get no option for raid. How do I do this?

---

### Post by Mark Phelps on 2011-09-20
I believe the standard Desktop CD does not support RAID.  You have to use the Alternate CD.

---

### Post by srs5694 on 2011-09-20
You might want to look into Linux's [Logical Volume Manager (LVM)](http://en.wikipedia.org/wiki/Logical_Volume_Manager_%28Linux%29) instead of RAID 0, since it's a bit more flexible in some respects, particularly if your disks aren't equal in size or if you expect you'll want to be adjusting filesystem sizes in the future. This won't really help much with your immediate problem, though; the Desktop installer doesn't support LVM any better than it supports RAID. The Alternate installer, as Mark suggests, includes LVM support as well as RAID support, IIRC. Also IIRC, it's a text-mode installer, so it's not as pretty as the Desktop installer.

---

