---
title: "missing hard drive space after a resize(grow)"
date: 2010-03-30
forum: General Help
---

### Post by lsbe on 2010-03-30
I have no idea what happened, I deleted a 20GB ntfs partition and since it was next to my ext4 partition I grew my ubuntu part. onto that giving me 54GB or so:
[IMG]http://makesmypphard.info/proof.png[/IMG]
yet looking at df -h i get:
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              32G   13G   17G  44% /
none                  996M  288K  995M   1% /dev
none                 1002M  2.0M 1000M   1% /dev/shm
none                 1002M  336K 1002M   1% /var/run
none                 1002M     0 1002M   0% /var/lock
none                 1002M     0 1002M   0% /lib/init/rw
/dev/sda2              88G   80G  8.0G  91% /media/Windows Drive
/dev/sdb1             3.8G  428M  3.4G  12% /media/Sandisk

can anyone help reclaim my lost 20 gigs ;_;?

---

### Post by srs5694 on 2010-03-30
It looks like the *partition* was resized, but not the *filesystem* it contains. At a text-mode prompt, type:

```

sudo resize2fs /dev/sda1

```

I recommend rebooting into an emergency CD to do this. In theory, it should work while the filesystem is mounted, but I've run across one or two problem reports about attempts to do it that way.

---

