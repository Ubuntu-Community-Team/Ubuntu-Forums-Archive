---
title: "GParted info device OFF"
date: 2010-04-25
forum: General Help
---

### Post by abanderas on 2010-04-25
After reinstall windows and recover GRUB with Super Grub Disk I lost info device on GParted in Ubuntu - show only unallocated entire disk capacity! Only File Systems on the System Monitor show me all partition and also exist and works fine over Places. Well, how to make GParted to review all partitions info? Thx.

---

### Post by dcstar on 2010-04-26
> **abanderas said:**
> After reinstall windows and recover GRUB with Super Grub Disk I lost info device on GParted in Ubuntu - show only unallocated entire disk capacity! Only File Systems on the System Monitor show me all partition and also exist and works fine over Places. Well, how to make GParted to review all partitions info? Thx.

Gparted reads partition information from a different place that other things do, if this information is corrupted then the system can still work, but gparted won't.

Whatever created/recreated your partitions is the problem, and gparted cannot do anything to fix it AFAIK.

---

