---
title: "software raid issue"
date: 2012-06-02
forum: General Help
---

### Post by vernonh76 on 2012-06-02
I have 3 1tb hard drives.  I configured using gparted and mdadm a 1GB partition on all three drives as Raid 1.  I am going to use this for my /boot with grub installed.  I then proceeded to make a partition of the rest of the drive and had used mdadm to make a raid 5 partition of them.  That all worked fine and the disk utility sees the raid 5 partition and the raid 1 partition.  Now I need to go to gparted to format my swap and / and /home partitions on the /dev/md1 raid 5 portion of the drive and it doesn't see it, just md0 sda1 sda2 sda3.  Any ideas.  I am needing to use gparted as this is a newer drive and any of the other utilities I use to format with cause misalignment issues.

---

