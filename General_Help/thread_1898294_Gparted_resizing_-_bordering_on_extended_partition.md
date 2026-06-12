---
title: "Gparted resizing - bordering on extended partition"
date: 2011-12-21
forum: General Help
---

### Post by cookiecruncher on 2011-12-21
Hi all
I have 2 primary partitions, namely (sda1 100MB) system reserved (sda2 100GB) Windows7 bordering on an extended partition of 125GB which is divided into 5 partitions, sda5 (swap 1GB) sda6 (root 20GB ext4), sda7 (free 20GB), sda8 (data 90GB ext3) and sda9 (free 20GB).
I'd like to reinstall my linux stuff (swap and root) into sda7 or sda9 and make available the current swap and root partitions to expand the windows 7 partition.

Is this possible?

Would it be better to backup the data, delete the entire extended partition, enlarge the Win7 partition, and then reinstall/restore everything? Will this work?

---

### Post by Mark Phelps on 2011-12-21
ANY, repeat, ANY partitioning work you want done with any of the Win7 partitions should be done using Windows apps, not Linux apps.  The Win7 Disk Management utility will let you resize the Win7 partitions, even the "C" drive -- but it doesn't have a lot of features.

For more features, download and burn a CD of the Partition Wizard Boot CD.  That's a Windows app that will safely do partitioning on the Win7 partitions.

---

### Post by dandnsmith on 2011-12-21
> **cookiecruncher said:**
> Hi all
I have 2 primary partitions, namely (sda1 100MB) system reserved (sda2 100GB) Windows7 bordering on an extended partition of 125GB which is divided into 5 partitions, sda5 (swap 1GB) sda6 (root 20GB ext4), sda7 (free 20GB), sda8 (data 90GB ext3) and sda9 (free 20GB).
I'd like to reinstall my linux stuff (swap and root) into sda7 or sda9 and make available the current swap and root partitions to expand the windows 7 partition.

Is this possible?

Would it be better to backup the data, delete the entire extended partition, enlarge the Win7 partition, and then reinstall/restore everything? Will this work?

The first step is to delete the sda5 and sda6 partitions in gparted, and then resize the extended partition to exclude the deleted space (also in gparted).
Next you use the Win7 tools to extend the win7 space to include the spare.

HTH

---

