---
title: "Partition name changes every reboot, causing boot problems"
date: 2010-06-19
forum: General Help
---

### Post by ccabal on 2010-06-19
I've had this strange issue for a while, and it took me a while to figure out what was happening. It happened on Ubuntu 8.*, went away on Ubuntu 9.* but unfortunately is back on Ubuntu 10.04 LTS.

The problem is that every time I reboot, the partition names get shuffled around.  Specifically, from /proc/partitions/:
major minor  #blocks  name

   8        0  244198584 sda
   8        1  244196001 sda1
   8       16   29316672 sdb
   8       17   11550703 sdb1
   8       18   15735667 sdb2
   8       19    2024190 sdb3

You can see I have 2 disk drives. One is a 250G disk, /dev/sda, on which sda1 has an ext3 filesystem, and has my '/usr/home' directory.
My other disk a 30Gb disk, /dev/sdb/  has 2 major partitions, sdb2 which is my linux '/'  and '/usr'

The problem I am having is that on a reboot, sometimes it assigns my 250Gb disk partition that contains my home directory, as /dev/sdb1, and at other times it gets assigned as /dev/sda1.
So every reboot I need to go into a recovery shell, and swap the 2 lines in /etc/fstab/

#/dev/sdb1       /home           ext3     
/dev/sda1       /home           ext3     

What a pain. Hopefully there is a way to work around this issue... Is this a "feature"  or a "bug"?

Thanks for any tips.

---

### Post by TeoBigusGeekus on 2010-06-19
I don't know what causes the problem, but you could try to reference your drives by uuid in your fstab file.
Run 
```
sudo blkid
```
in terminal, and replace the /dev/sdb1 and /dev/sda1 references with 
UUID=
Example (my fstab):
```
UUID=5e81ffa7-9bf4-4ef7-a6c0-bb89aa5e4e1d swap swap defaults 0 0
UUID=297ff4d0-e14b-41a4-8631-0b6e4cbe154b / ext4 defaults 0 1
UUID=f883ba31-ad86-4d90-9287-60956ac94684 /home ext4 defaults 0 1
UUID=5cb509b8-44d5-4bd8-af04-18bcd47c510f /media/disk ext4 relatime 0 2
UUID=971f1ba5-cfe3-4c6b-b0a0-ea3318769ba4 /media/disk-1 ext4 relatime 0 2
```

---

### Post by WorMzy on 2010-06-19
I second the UUID recommendation. UUIDs are fixed identifiers, they won't change unless you modify the partition in question (I think), or force a new UUID to be generated. Very handy for specifying mounts.

---

### Post by ccabal on 2010-06-19
Thanks guys, I will try that. That sound like exactly what I need.

---

