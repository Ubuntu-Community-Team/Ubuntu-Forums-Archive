---
title: "How to determine LVM group and name from a mount point?"
date: 2010-09-02
forum: General Help
---

### Post by ygoe on 2010-09-02
Hi,

I'd like to determine the volume group and volume name for a logical volume that is currently mounted to a given mount point. All I see in the output from mount and df is a syntax like /dev/mapper/hostname-root, but I would prefer the naming like /dev/hostname/root to ultimately extract the parts "hostname" and "root" from it. That's what other folks seem to do, but it doesn't work on Ubuntu 10.4 because of the different naming. And the lvs command doesn't give me mount points or such.

---

