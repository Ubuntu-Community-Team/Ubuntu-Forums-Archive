---
title: "RAID 5 issue following reboot"
date: 2009-10-26
forum: General Help
---

### Post by wordian1 on 2009-10-26
Successfully set up a raid 5 array with mdadm on 3 identical sata drives each having a single partition. (sda1,sdb1,sdc1)

All was fine until I did a reboot. The array now fails to reassemble.

Investigating, this appears to be because the partitions do not appear as /dev/sda1 etc nor are listed in /proc/partitions.

However fdisk informs that the partitions do indeed exist.

So the question obviously is why wouldnt the partitions be under /dev and how can I get them to be?

---

### Post by barbz127 on 2009-10-26
did you create and save the mdadm config after you setup the raid?

Paul

---

### Post by wordian1 on 2009-10-26
yes I did. 

I dont believe mdadm.conf to be the issue as it appears to try to reassemble the array but cant because its looking for /dev/sda1 /dev/sdb1 /dev/sdc1 which are all missing.

---

### Post by barbz127 on 2009-10-26
odd question cause i havent played with mdadm yet (tomorrow) it doesnt need to be mounted in the fstab or anything do they?

---

### Post by DeMus on 2009-10-26
> **barbz127 said:**
> odd question cause i havent played with mdadm yet (tomorrow) it doesnt need to be mounted in the fstab or anything do they?

I use a RAID 0 configuration and my fstab file looks like this:
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/md0 during installation
UUID=622db721-b768-4909-a404-046acc630925 /               ext4    relatime,errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=a82313a3-6fdd-43a9-8411-dd63c62675ea /boot           ext4    relatime        0       2
# /home was on /dev/md1 during installation
UUID=f737b2f8-d2f4-4e01-8c92-41efc9512425 /home           ext4    relatime        0       2
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

There is no sda2 and 3 and also no sdb2 and 3, just md0 and md1.
I have a sda1 partition for /boot since it can not be part of the RAID.
Do you have similar lines in your fstab file?

---

### Post by wordian1 on 2009-10-26
Yes mine looks pretty similar - ie I have an entry for /dev/md0

---

### Post by DeMus on 2009-10-26
> **wordian1 said:**
> Yes mine looks pretty similar - ie I have an entry for /dev/md0

How did you build the RAID? I used the alternate Ubuntu disk and when it came to the partitioning part I created all my partitions:
sda1, sda2, sda3, sdb1, sdb2 and sdb3.
sda1 is used for /boot
sdb1 is a dummy partition to make the disks look the same
sda2 and sdb2 form md0 for /
sda3 and sdb3 form md1 for /home
With this my RAID is build and I could install the OS. Afterwards I can simply boot into it, there is no need for rebuilding the array. It's there already.
What did you do differently?

---

