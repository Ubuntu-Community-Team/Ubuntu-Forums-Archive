---
title: "copied kubuntu to new partition but now boots to old partition"
date: 2011-06-14
forum: General Help
---

### Post by walter_j on 2011-06-14
I'm trying to copy kubuntu from a old disk to a partition on a new hard disk. I used the command:

cp -apx /mnt/source /mnt/dest

I also edited fstab and changed the uuid to the correct partition, rebuild grub, and rebooted. When booting the kubuntu in the new partition, the sysytem still refers to the old partition (which is much smaller). ie: df displays the old partition. Is there another config file that has to be edited?

---

### Post by walter_j on 2011-06-14
never mind. solved this by deleting the grub.cfg  in the new partition, then rebuilt grub from the partition that boots grub (mbr?)

---

