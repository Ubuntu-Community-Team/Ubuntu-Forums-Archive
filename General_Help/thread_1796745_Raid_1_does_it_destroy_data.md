---
title: "Raid 1: does it destroy data?"
date: 2011-07-04
forum: General Help
---

### Post by CyberPingU on 2011-07-04
Hello,
my question is quite simple and at the same time should even sound weird for people that is used to use raids... but here we go!
I have got 2 hard disks that do match in space. I'd like to use mdadm to create a raid 1, the mirror one. Since I don't want to format / erase / delete what's in my primary hard disk (/dev/sda, 3 partitions), how can I replicate its content into /dev/sdb and mirror it with the raid tool?
Does something like this work?

- install madam
- fdisk /dev/sdb and replicate sda's partitions (using as filesystem "fd");
- sudo  mdadm --create --verbose /dev/md0 --level=mirror --raid-devices=2 /dev/sda1 /dev/sdb1
- sudo  mdadm --create --verbose /dev/md1 --level=mirror --raid-devices=2 /dev/sda2 /dev/sdb2
sudo  mdadm --create --verbose /dev/md2 --level=mirror --raid-devices=2 /dev/sda3 /dev/sdb3

... and proceed...?

Do you have any page to point, with the right documentation to achieve a replication of the hard disk without a format of the source disk?
Thanks in advance

---

### Post by Jouke74 on 2011-07-04
Before messing with Raid tools I strongly suggest you backup your important data first :-) Different raid controllers and tools require different things, including a reformat (often).

---

### Post by CyberPingU on 2011-07-04
Well, of course, but I would like some "howto" that would let me help through the "possibly not destructive" process =)

---

### Post by dcstar on 2011-07-04
> **CyberPingU said:**
> Hello,
my question is quite simple and at the same time should even sound weird for people that is used to use raids... but here we go!
I have got 2 hard disks that do match in space. I'd like to use mdadm to create a raid 1, the mirror one. Since I don't want to format / erase / delete what's in my primary hard disk (/dev/sda, 3 partitions), how can I replicate its content into /dev/sdb and mirror it with the raid tool?
..........
Do you have any page to point, with the right documentation to achieve a replication of the hard disk without a format of the source disk?
Thanks in advance

[https://wiki.archlinux.org/index.php/Convert_a_single_drive_system_to_RAID](https://wiki.archlinux.org/index.php/Convert_a_single_drive_system_to_RAID)

---

