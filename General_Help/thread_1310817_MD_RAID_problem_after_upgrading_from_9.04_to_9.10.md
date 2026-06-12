---
title: "MD RAID problem after upgrading from 9.04 to 9.10"
date: 2009-11-02
forum: General Help
---

### Post by swordfishRU on 2009-11-02
Hi all!

After upgrading from 9.04 to 9.10 MD raid said me, that its status is degraded.
I analysed logs and saw strange situation - MD raid added /dev/block/252:1 device instead of two /dev/sda1 and /dev/sdb1.
But /dev/block/252:1 device is dmraid's raid that never used before!
Now there aren't /dev/sda1 and /dev/sdb1 devices is system.
How can I restore my raid now?

[IMG]http://i.imagehost.org/0928/1_40.png[/IMG]

Attached (log.zip):
dev.txt    = ls /dev/ 
devbl.txt  = ls /dev/block/
dmesg      = dmesg
dmraid.txt = dmraid -r
fstab      = fstab
lsmod      = lsmod
lsall.txt  = ls -all /dev/block/252*
mdadm.txt  = mdadm --detail /dev/md1

---

### Post by swordfishRU on 2009-11-10
So, I solved this problem.
I added "nodmraid" option for kernel and after (successful ;) ) booting I restored my raid system using mdadm.

---

