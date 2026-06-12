---
title: "Expand Raid 5 Array"
date: 2010-08-15
forum: General Help
---

### Post by ptmuldoon on 2010-08-15
I think I understand how to do this, but want to make ask to make sure before screwing things up.

I have an existing 4 x 1TB drive Raid 5 array.  I'm looking to expand that soon adding another 2 1 TB drives to the array.

The WIKI [here](http://en.wikipedia.org/wiki/Mdadm) talks of growing an md1 array.  Since my array is on md0, I think to add the 5th drive I would do the following?

mdadm --add /dev/md0 /dev/sxy1
mdadm --grow /dev/md0 -—raid-devices=5

I also believe I need to partition that drive first to a Linux Raid partition as well?   And than to also format that partition to my existing raid file format of ext4?

---

