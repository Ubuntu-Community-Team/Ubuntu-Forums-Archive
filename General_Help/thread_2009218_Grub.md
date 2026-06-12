---
title: "Grub"
date: 2012-06-24
forum: General Help
---

### Post by ddeathly on 2012-06-24
Hey people, i have a windows 7 laptop,i installed ubuntu 12 then later installed backtrack 5,i want to remove ubuntu, so if i delete the partition will it remove grub? as i have backtrack5 wich i belive comes with GRUB?
thanks

---

### Post by DeMus on 2012-06-24
It depends where you installed Grub. When you installed Ubuntu, did you choose to install Grub on SDA? (or B, or whatever disk you were using)
This would mean it is in the MBR (Master Boot Record) of the disk, outside the partition you used for Ubuntu, which is maybe SDA2 or SDA3.
When you installed Backtrack, where did you install Grub? Again on the MBR of the disk? If so, you can delete the Ubuntu partition, and afterwards run Grub-update from within Backtrack to remove the Ubuntu entries.

---

