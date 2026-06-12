---
title: "Logical volume sorting individual files"
date: 2011-06-05
forum: General Help
---

### Post by HaWk162 on 2011-06-05
Hey everyone,

So I just had a quick question on logical volumes and such with ubuntu. I've been looking into setting up a storage array of 4 2tb hard drives for media storage in my house but have ran into a wall with with sort of array i should use, whether it be setting up a full raid system (raid 5 or 10 most likely) or using LVM for stripping. The one thing with LVM however, is that there is no parity or redundancy built into it in case 1 hard drive fails. I was wondering if it was possible to create something similar to that of LVM stripping, but instead the logical volume is sorted into whole individual files, not stripping them across the array. That way, if one drive fails, sure, i lose the contents of the one drive, but the rest of the content isn't lost and I have no loss of space because there is no inherent parity.

Any input would be most appreciated

Thanks
HaWk162

---

### Post by srs5694 on 2011-06-06
The traditional way to do as you suggest is to use RAID instead of or in addition to LVM. (If in addition to, you'd set up RAID and then use LVM on the RAID volume(s) you create.)

You might consider looking at the -m (--mirrors) option to lvcreate, though. I've never used this option, but based on its man page description, it sounds like it sets up the equivalent of a RAID 1 mirror.

---

