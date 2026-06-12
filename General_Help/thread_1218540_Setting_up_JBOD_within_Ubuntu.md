---
title: "Setting up JBOD within Ubuntu"
date: 2009-07-20
forum: General Help
---

### Post by buee on 2009-07-20
Is there a way to set up JBOD within Ubuntu?

I have Ubuntu installed on an 80GB SATA partition and have 8TB additional in a RAID5 mounted in /media.  I would like to destroy that RAID and set up JBOD and would prefer to do it within Ubuntu.  I noticed there is no JBOD option when installing Ubuntu so I'm wondering if it's possible.

---

### Post by fjgaude on 2009-07-21
JBOD, that's just a partition to Ubuntu... install to a partition made during the install process.

---

### Post by buee on 2009-07-21
Where would I locate that?  The only options I see as far as partitions go are software RAID, LVM, Ext4, etc.  The only options I see for RAID is RAID0, RAID1, RAID5, RAID10, but no JBOD.

---

### Post by beadrifle on 2010-04-17
bump. 

I want to set up an Ubuntu server running 9.10 (or 10.04 shortly) with a JBOD to run a squid cache server. I'm looking at something like two 80gb SATA drives to make up a JBOD. How's this done?

---

### Post by Jay_Rock on 2010-04-19
RAID0 can be your JBOD

/dev/sda = 80GB
/dev/sdb = 80GB
/dev/sdc = 80GB
/dev/sdd = 80GB
/dev/sde = 80GB
/dev/sdf = 80GB

mdadm --create /dev/md0 --level=0 --raid-devices=2 /dev/sd[abcdef]
cat /proc/mdstat
mkfs -t ext4 /dev/md0
mount -t ext /dev/md0 /media
df -hT

Now you have about 720GB mounted on /media

---

### Post by htnprm on 2010-09-27
Just a point to make re: "RAID0 can be your JBOD", this will create an array with N x S where N is the number of disks and S is the smallest disk size. JBOD would have the advantage of using all the disks, regardless of the size of the disks (Which is what I am trying to achieve).

---

