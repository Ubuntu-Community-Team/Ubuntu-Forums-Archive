---
title: "Does it make difference in which order a swap, root and home partition are created?"
date: 2011-01-12
forum: General Help
---

### Post by Rytron on 2011-01-12
Hi.

Does it make a difference in which order a swap, root and home partition are created when installing Ubuntu with manual partitioning?

Where would a boot partition come in to this? Is a boot partition really needed?

---

### Post by WorMzy on 2011-01-12
No, partition order is not important. And no, a /boot partition is not required; if you want one, I believe it can go anywhere, just like the other partitions.

---

### Post by tgalati4 on 2011-01-12
You would move the /boot partition on a machine that has trouble booting from certain kinds of disks.  Normally /boot is placed on the / (root) partition.  But if have really new disks (like SATA) on an older machine that can only recognize IDE/PATA drives, then you would put /boot on the older IDE drive so the machine can boot.  Once booted, the machine could then use the newer drives.

I can't think of an instance when the order would matter, but there are edge cases.  You can have multiple swap partitions across drives.  Linux will find them and add them to total swap.

There may be slight performance advantages putting /boot and / ahead of /home and /swap, but those speed differences would be hard to quantify without a specific/unchanging workload.

---

