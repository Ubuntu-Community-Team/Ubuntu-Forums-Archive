---
title: "Please help! Stuck with RAID5 setup"
date: 2011-06-28
forum: General Help
---

### Post by stringsonfire on 2011-06-28
Hi

I have an HP MicroServer with an OS drive and 4 2TB drives. The 4 2TBs I've been trying to make into a RAID5 array, which I then plan on sharing on the network. I've read loads about RAID5 on linux, and have been trying this for ages, but I can't figure it out! The array took 780 minutes to build, not sure if that's normal? Then it was identified as md127, but I thought it should have been md0. Once I set up the filesystem, it mounted, but with no permissions, even logged in as root, and I couldn't use it. Also, it had a really long name made up of seemingly random letters and numbers. So I deleted it and tried again and have ben playing about but I just can't make it work! Here are the steps I followed, compiled from various guides, in order:

CREATE RAID ARRAY

sudo mdadm --create --verbose /dev/md0 --level=5 --chunk=64 --raid-devices=4 /dev/sd[bcde]1

VIEW PROGRESS

sudo watch cat /proc/mdstat

CREATE THE mdadm.conf FILE

sudo echo "DEVICE partitions" > /etc/mdadm/mdadm.conf

sudo mdadm --detail --scan >> /etc/mdadm/mdadm.conf

TO CREATE FILESYSTEM

mkfs.ext4 -b 4096 -E stride=16,stripe-width=48 /dev/md0

TO INDEX:

tune2fs -O dir_index /dev/md0

e2fsck -D /dev/md0

Thanks for your help!

---

