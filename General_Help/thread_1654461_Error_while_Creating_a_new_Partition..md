---
title: "Error while Creating a new Partition."
date: 2010-12-28
forum: General Help
---

### Post by kershocker on 2010-12-28
I'm trying to install XP Sp 3 on my comp which is running Ubuntu atm. But when I tried to create a partition after I clicked "Apply" I get this error :

GParted 0.6.2
 Libparted 2.3
    **Create Primary Partition #1 (ntfs, 74.50 GiB) on /dev/sda**  00:00:01    ( ERROR )             create empty partition  00:00:01    ( ERROR )       libparted messages    ( INFO )             *Partition(s) 1, 5 on /dev/sda have been written, but we have been  unable to inform the kernel of the change, probably because it/they are  in use.  As a result, the old partition(s) will remain in use.  You  should reboot now before making further changes.*          ========================================

---

### Post by TeoBigusGeekus on 2010-12-28
Are you using a live cd to create your partitions?

---

### Post by srs5694 on 2010-12-28
Despite the fact that the message uses the word "ERROR" (twice), it's not really an error; it's just that the kernel is using the old partition table and so won't accept the new one. Do as the message suggests: Reboot the computer. The kernel will then use the new partition table and you can proceed with creating a new filesystem on the new partition.

A caveat: If you made changes that altered the device number of any Linux partition, it's possible you'll need to adjust your /etc/fstab file and/or your boot loader configuration in order to successfully reboot. Stock Ubuntu installations no longer use such identifiers, so you'll probably be OK unless you've changed things yourself.

---

