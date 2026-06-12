---
title: "about installing ubuntu"
date: 2010-08-28
forum: General Help
---

### Post by rahulshrirs on 2010-08-28
I have tried installaing ubuntu on two laptops with windows7 already installed and i want dual booting.
  But I want option **_GUIDED RESIZE_** to use in this installation instead of manually partition.but when i tried on one laptop the option guided resize was being shown but on the other dell laptop there was no such option like GUIDED RESIZE. so i am confused why it is happening so ..
please guide me.

---

### Post by ajgreeny on 2010-08-28
Dell machines with win7 sometimes already have 4 partitions on the disk out of the box, which means you can not add any more.

Can you run the Ubuntu live CD on that machine and report the output of ```
sudo fdisk -l
```that's a lower case L at the end.  Also it may be helpful to run gparted from the live CD and attach a screenshot to your reply.

---

