---
title: "Recover Files from ReadyNAS LVM2 Partition"
date: 2009-07-07
forum: General Help
---

### Post by kitpierce on 2009-07-07
I am trying to recover some data from a SATA drive that was part of a ReadyNAS RAID array.  The ReadyNAS failed and tried to rebuild itself, but I have pulled the hard drive before the reformat started.  I have the SATA drive plugged into a 9.04 install and am able to see the drive using GParted - it is listed as /dev/sdb and I think the partition I am interested in is /dev/sdb5 shown as lvm2 within the extended partition of /dev/sdb3.  I am looking to mount the drive so I can pull selected files off to a USB hard drive, but have tried various mount commands (see below) with varying error messages.

mount -t cifs /dev/sdb5 /home/kit/port
mount -t ext3 /dev/sdb5 /home/kit/port
mount -t ext2 /dev/sdb5 /home/kit/port
mount -t auto /dev/sdb5 /home/kit/port

Is there any way to mount the partition in question?

---

