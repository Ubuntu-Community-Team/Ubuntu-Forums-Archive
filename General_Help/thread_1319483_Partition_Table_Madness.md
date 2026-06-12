---
title: "Partition Table Madness"
date: 2009-11-08
forum: General Help
---

### Post by oybon on 2009-11-08
to cut a long story short, the partition table appears to have a problem; BUT; is still working.

using gparted I have been moving some partitions around to generate more usable space. All fine thus far and working.

Then I deleted a redundant partition, and added a new partition on another section. All of this done in ubuntu except the addition as I wanted a none standard NTFS partition and this seemed the way to go. Bad Idea.

Enter Grub Hell.

No problem, just revert to xp MBR and re-install grub2.

Ok so now I have both OS's working and am typing from ubuntu. Gparted though now thinks the whole drive is not partitioned, in both live cd and live environment. Palimpset disk Utility sees the partitions, but thinks /. is an empty Extended Partition!

The attached image is what i see.

---

