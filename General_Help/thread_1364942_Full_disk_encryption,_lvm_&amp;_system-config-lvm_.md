---
title: "Full disk encryption, lvm &amp; system-config-lvm - 9.10"
date: 2009-12-26
forum: General Help
---

### Post by tubbygweilo on 2009-12-26
I have installed 9.10 with full disk encryption and lvm via the alt install cd followed by System-config-lvm from the repositories it all looks well and good, and indeed works as advertised. 

Now for the but according to the information supplied via the repository  > System-config-lvm provides a graphical interface to the LVM tools (and related
utilities, including fsck and resize2fs) which is good for non-emergency
storage administration. It enables you to manage your logical volume and
filesystem configuration with a few mouse clicks, and it prevents potentially-
disasterous command-line mistakes such as reducing a logical volume size before
reducing the filesystem contained within that volume.

(One word of warning: system-config-lvm does not recognize RAID elements as
being in use, and therefore lists them as "Unitnitialized Entities". If you are
using a LVM-on-RAID configuration, system-config-lvm will let you wipe out RAID
elements by making them into PVs. Be careful!)

with the last few lines of information > Canonical does not provide updates for system-config-lvm. Some updates may be provided by the Ubuntu community.

So should I be worried about this?
Should I be using another method to manage my disk?

Many thanks for any ideas and help that can be offered.

---

