---
title: "Gparted error can;t format in any type!"
date: 2011-01-17
forum: General Help
---

### Post by checoimg on 2011-01-17
GParted 0.5.1
 Libparted 2.2
    **Create Primary Partition #1 (ntfs, 50.00 GiB) on /dev/sda**  00:00:01    ( ERROR )             create empty partition  00:00:00    ( ERROR )       libparted messages    ( INFO )             *Unable to satisfy all constraints on the partition.*          ========================================

---

### Post by efflandt on 2011-01-17
Gparted may not work if any partitions on that drive are mounted.  If you are running from that drive, and do not have another drive to boot from, you may need to do that from live CD or USB (and sudo swapoff any swap partition being used on that drive).

---

### Post by srs5694 on 2011-01-17
I don't think this message has anything to do with mounted partitions. I haven't investigated this message in detail, but my impression is that it occurs because of artificial constraints on partitions' sizes and locations, such as old-style alignment to (fictitious) cylinder boundaries or new-style alignment to 1 MiB boundaries, particularly when mixing alignment styles. I'm guessing that there's a rounding error that's causing GParted to try to create partitions that overlap.

There should be either a check-box to align partitions to cylinder boundaries or a selector button to choose the alignment style (to cylinder boundaries, to 1 MiB boundaries, or not at all) in one of the dialog boxes in the procedure. Change to another option or disable the alignment altogether and the problem should go away. If it doesn't, try creating your partition with a small gap before and/or after it.

If even that doesn't help, or if you want to use every available sector of disk space, you could use fdisk to create your new partition (launch it as "sudo fdisk -cu /dev/sda"), then reboot and use mkfs or GParted to create a filesystem in the new partition. (Rebooting shouldn't be necessary if the disk doesn't have any mounted filesystems or swap space -- say, if you're running from an emergency disc.)

---

