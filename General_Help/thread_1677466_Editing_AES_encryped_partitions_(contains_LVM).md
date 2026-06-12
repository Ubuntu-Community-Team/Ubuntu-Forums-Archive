---
title: "Editing AES encryped partitions (contains LVM)"
date: 2011-01-28
forum: General Help
---

### Post by jamiejrg on 2011-01-28
Good evening forum,

Just wondering if anyone can offer some insight into my situation. I need to increase the size of the physical partition containing /boot because update manager is complaining that it's to small. I'll take it from ~91MB to around 200MB just to be safe. The process will involve resizing an encrypted physical partition that contains an LVM. I need to know the process of events to get the job done. For starters my specs.

Ubuntu 10.04 Lucid
Kernel 2.6.32-26-generic
Ubuntu is the only OS on the disk

Disk has 2 physical partitions. Starting from the front of the physical disk:
1) /boot ~91MB - unencrypted (because it has to be)
2) Rest of the disk with an encrypted (AES-256) containing an LVM with 2 disks.

Process:
Since I'll be resizing the partition containing the rest of the system files I'll need to do the job from a live CD. I'm not comfortable enough resizing partitions with CLI. How exactly do I deal with the encrypted partition though? Will Gparted recognize it and allow me to do any resizing without any other arguments?

---

