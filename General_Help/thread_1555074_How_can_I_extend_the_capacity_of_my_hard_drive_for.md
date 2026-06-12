---
title: "How can I extend the capacity of my hard drive for ubuntu"
date: 2010-08-17
forum: General Help
---

### Post by ali780 on 2010-08-17
Hi,

I have window 7 and Ubuntu 10.04 on my laptop.
As you know if I extend the capacity of my ubuntu partion in window, I will lose ubuntu and I should reinstall it.
I want to know if there is a way for extending my ubuntu partition from 20  Gb to 30 Gb without loosing ubuntu and windows?

Thank you for help

---

### Post by ajgreeny on 2010-08-17
If this is a proper dual boot, not wubi, you can do it by first defragging windows a couple of times, then using windows own disk management utility to shrink the windows partition, or partitions, leaving empty space to the left side of the ubuntu partition.  Note the ubuntu partition will not be fully detected in windows and will be called "unknown partition" or something similar.

Now boot to the ubuntu live CD/USB and run gparted to enlarge the ubuntu partition into the space now available.

This assumes you have a simple partition layout, but if you want us to do a quick check of how partitions are laid out on your disk at the moment, run gparted either from your ubuntu install or from the live CD and post a screenshot of that back here.

---

### Post by earthpigg on 2010-08-17
hi,

ajgreeny's advice looks good to me. the only thing i will add is that it is always *strongly advised* to have solid backups on hand ***before*** doing any type of partition modifications.

---

### Post by ajgreeny on 2010-08-18
Agreed, but I took that as read.  No-one should ever do any partitioning activities or editing on a system without good backups of all that is important to you.

---

