---
title: "Too much HDD I/O overhead?"
date: 2009-08-19
forum: General Help
---

### Post by touchlikefire on 2009-08-19
Will the following slow down my PC performance?

I have an LVM with 3 physical devices, a single encrypted volume on top, with another LVM and 5 logical volumes on top of that.

---

### Post by touchlikefire on 2009-08-19
My initial, amatuer test seems to indicate that all is well:
[list]
[*] 3 GB xfer from external hdd to sda2 - normal partition, non encrypted, no lvm - had a speed of 21 Mbps
[*] 3 GB xfer from external hdd to /dev/mapper/opencrypt-home - lvm on dmcrypt on lvm - had an initial speed of 45 Mbps, ending @ 26 Mbps
[/list]

A subsequent test with a 30GB file:
[list]
[*] sda2: 22 Mbps
[*] /dev/mapper/opencrypt-home: 18.8 Mbps
[/list]

Lastly, a 100MB file:
[list]
[*]sda2 is instant
[*]/dev/mapper/opencrypt-home takes about 3 seconds
[/list]

I would feel better if someone would give some advice on this issue and explain to me if my partitioning scheme is negatively affecting my SATA2 disk performance.

---

