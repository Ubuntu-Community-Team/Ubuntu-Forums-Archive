---
title: "Live CD crash"
date: 2006-03-13
forum: General Help
---

### Post by slightly72 on 2006-03-13
Hi,

I'm considering installing Ubuntu on a Sharp Actius UM32W laptop (Pentium 3 1GHz, 512Mb RAM, 40Mb hdd), so I've tried the live CD first. Everything seems to go through fine until the loader switches to a graphical interface and tries to perform "Checking all filesystems", at which point it switches back to text mode and displays:

/etc/rcS.d/S30checkfs.sh: line 57: 19559 Segmentation Fault    fsck $spinner -T -R -A $fix $force

* fsck faile. Please repair manually
* CONTROL-D will exit from this shell and continue system startup


At this point, CTRL-D does not do anything and the only option is to power it down.

A few questions:
- Anyone has an idea how I can get around this (boot parameters maybe?).
- Is the live CD crashing any indication on the success of installing Ubuntu as a resident OS? I still haven't partitioned the hdd, and still undecided whether I should use VMware based linux loading or going native. I have checked linux-on-laptops, and aparently RedHat 9.0/FC 1 could be installed on this laptop. Anyone has any experience with Ubuntu on this laptop?

Thanks.

PS. If this is the wrong forum for this kind of post, I appologize; I'm new to this Ubuntu community.

---

