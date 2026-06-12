---
title: "Server mirroring questions?"
date: 2006-02-21
forum: General Help
---

### Post by General Moskovich on 2006-02-21
I'm going to have two computers (both running breezy but with different hardware) that I would like to mirror certain (data) directories each night. 

Right now I have a python script that I wrote that tars everything up and uses scp to send it over the backup server. This works well but I was just wondering if there was anything better?

How do you all maintain a primary server and switch to another server during failure with minimal downtime?

Thanks!

---

### Post by schilcha on 2006-02-21
[QUOTE=General Moskovich]I'm going to have two computers (both running breezy but with different hardware) that I would like to mirror certain (data) directories each night. 
[/QUOTE]

Sounds like "rsync" can help you. It was designed to mirror websites -- I'm using it to mirror my home-dir to a backup-machine.

[QUOTE=General Moskovich]How do you all maintain a primary server and switch to another server during failure with minimal downtime?
[/QUOTE]
Well, I ususally... hm, you just have to... basically, I don't have any clue

---

### Post by KnottyMan on 2006-02-21
DRBD ([http://www.drbd.org/](http://www.drbd.org/)) will mirror two block devices.  We have this setup at work and it's great.  Think network RAID1.

Identical machines, one is "primary".  The OS partitions are seperate so if we upgrade something on one, we have to do both (or should).  Swap is seperate : )  But the data  volume (sda3) is mirrored with the other machine.  We have gigE loopbacked between the two and it'll sync at 70Mbytes/s.  Write on primary, second later the same write happens over on secondary.

If you delete a file on one, it'll delete it on the other one!

The secondary's DRBD file system is not mounted as you can't unless you use GFS.

---

