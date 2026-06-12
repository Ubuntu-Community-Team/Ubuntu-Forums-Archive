---
title: "completely remove raid1 array"
date: 2012-02-05
forum: General Help
---

### Post by buffchick on 2012-02-05
I'm trying to completely delete a software raid 1 array and yet, it keeps coming back. my /etc/mdadm.conf has nothing in it anymore and there's no mount point in fstab. I zeroed the superblocks but it keeps showing back up after a reboot. How do I get rid of it? I want to start over with two partitions instead of just one.

---

### Post by bakegoodz on 2012-02-06
Are you sure you got the superblock? Try this:

mdadm --stop /dev/md0
mdadm --zero-superblock /dev/sdaX (on every partition in the raid)

You could also purge the package then software process wouldn't even to create the raid.

 apt-get purge mdadm

---

### Post by buffchick on 2012-02-06
Yep. That's exactly what I did. Here's my history.

 1992  sudo mdadm --detail /dev/md0
 1993  sudo mdadm --zero-superblock /dev/sdb1
 1994  sudo mdadm --zero-superblock /dev/sdc1
 1995  sudo vi /etc/mdadm/mdadm.conf

and I need to keep the package as I want to build a new array with 2 partitions instead of one.

---

### Post by buffchick on 2012-02-06
got it with this...

sudo mdadm --misc --zero-superblock --force /dev/sdb

---

### Post by bakegoodz on 2012-02-19
Interesting. Was your raid made up of raw drives instead of partitions?

---

