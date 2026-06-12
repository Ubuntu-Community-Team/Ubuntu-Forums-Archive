---
title: "LVM / LUKS encrypted System - how to shrink volume ?"
date: 2011-11-16
forum: General Help
---

### Post by thyriel on 2011-11-16
Hi,

i have installed Xubuntu (11.10) on a Laptop with full System encryption and LVM.
Badly i gave the /home partition all of the free space during installation, but now id need to get some GB free for a testing environment.

So i have tried to shrink the /home partition with system-config-lvm but that produced an error that it cannot unmount /home

Next i created a Live USB Stick, installed lvm2 and system-config-lvm (cryptsetup was already installed) and tried to shrink the partition there.
Seemed all to work fine but on next boot an error came up that the /home partition has errors and needs to be fixed. But fsck discontinued with Error Code 4.

I then booted back to Live USB System, changed the partition size back to maximum and it worked again.


So how can i shrink the /home partition or doesnt that work on System partitions ?

---

### Post by thyriel on 2011-11-16
found it... i forgot to shrink the volume with resize2fs before shrinking it in LVM

---

