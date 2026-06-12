---
title: "resize partition"
date: 2009-12-03
forum: General Help
---

### Post by Mr Nemo on 2009-12-03
I would like to add memory to both the linux partition and the swap partition although I can't figure out how to do it. I installed gparted but it wont let me resize the partitions, and if I use bootit NG it wont let me add to the partition.

---

### Post by jbrown96 on 2009-12-03
You cannot alter partitions that are currently mounted, and your linux and swap paritions are always mounted when the system is running. You can boot the liveCD (or a gparted liveCD, which you can download), and then you should be able to resize the partitions. 

the LiveCD might automatically mount your swap, so you may need to manually deactivate it. You can tell if it is mounted in Gparted; it will have an icon with a set of keys next to it. Run ```
sudo swapoff -a
``` to turn off swap.

---

### Post by Mr Nemo on 2009-12-04
Thanks a bunch. I guess Bootit NG doesn't work well with linux?

---

### Post by jbrown96 on 2009-12-04
I have no idea. I've never heard of it. If it's designed for Windows, then probably not. It probably doesn't understand Linux file systems.

---

