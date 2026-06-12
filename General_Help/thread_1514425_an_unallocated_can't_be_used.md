---
title: "an unallocated can't be used?"
date: 2010-06-21
forum: General Help
---

### Post by luofeiyu on 2010-06-21
please my attachment ,there is an an unallocated can't be used?

---

### Post by S.R on 2010-06-21
Max of 4 primaries. Go extended. [http://ubuntuforums.org/showthread.php?t=638283](http://ubuntuforums.org/showthread.php?t=638283)

---

### Post by yetiman64 on 2010-06-21
S.R. is correct, try resizing your current extended partition to fill the unallocated space. Then inside the resized extended partition add what you want.

Just note you won't be able to put a bootable Windows install in here, but a bootable Linux partition or **any** storage partitions will be OK. Letting us know what it's needed for may help you some more.

If you can't unmount a logical partition or turn off the swap partition (right click the swap partition and choose "swapoff") within the extended partition may stop you resizing it. If this happens, then you may want to consider downloading the bootable gparted iso and making a bootable gparted cd. Link for gparted iso [_here_]("http://sourceforge.net/projects/gparted/files/gparted-live-stable/0.5.2-9/gparted-live-0.5.2-9.iso/download"). Gparted site [_here_]("http://gparted.sourceforge.net/").

**Please note**: any partition work/resizing etc. can possibly cause data loss. It is advisable to do full back ups to external media for your own data security, **before** attempting.

---

