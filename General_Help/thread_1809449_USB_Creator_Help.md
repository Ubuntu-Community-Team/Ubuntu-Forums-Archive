---
title: "USB Creator Help"
date: 2011-07-21
forum: General Help
---

### Post by waveOSBeta on 2011-07-21
I'm trying to make my 256GB eSATA drive bootable and persistent with Ubuntu 11.04. The issue is, the drive doesn't show up in the USB creator. Does anybody know why?

---

### Post by waveOSBeta on 2011-07-21
Anybody?

---

### Post by garvinrick4 on 2011-07-21
> I'm trying to make my 256GB eSATA drive bootable and persistent with  Ubuntu 11.04. The issue is, the drive doesn't show up in the USB  creator. Does anybody know why?

It is not a flash drive it is a HDD. Regular install with grub in sdb if only HDD and USB HDD installed. You are using sdb to INSTALL not sda. USB creator maxes out at 4 gig persistence is a fat
format thing.

---

