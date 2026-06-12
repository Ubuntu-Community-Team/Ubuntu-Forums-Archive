---
title: "Can not fsck even though filesystem is unmounted"
date: 2010-07-11
forum: General Help
---

### Post by ratliffm on 2010-07-11
I had some power issues recently that caused my computer to do a hard shutdown, so I would like to check some of my disks.  I unmounted the partition, but when I try to fsck, I get an error.  Maybe somebody knows what is going on?

michael@powerspec:~$ sudo umount /dev/sdb1
michael@powerspec:~$ fuser /dev/sdb1
michael@powerspec:~$ sudo fsck -t ext3 /dev/sdb1
fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
fsck.ext3: Device or resource busy while trying to open /dev/sdb1
Filesystem mounted or opened exclusively by another program?
michael@powerspec:~$ sudo mount /dev/sdb1

Thanks,
Michael

---

### Post by Bachstelze on 2010-07-11
First, please paste the output of commands on different lines with CODE tags. Second, are you relly sure the filesystem is not mounted?

---

### Post by ratliffm on 2010-07-11
Updated above post, sorry, I had JS disabled and it mangled the post.

---

### Post by bumanie on 2010-07-11
Try doing the fsck from a live ubuntu cd or a live gparted cd.

---

### Post by cmapesjr on 2010-07-11
sudo touch /forcefsck will do it on the next restart.

---

### Post by ratliffm on 2010-07-11
Thanks for the info.

The touch /forcefsck didn't seem to do anything, I assume that the boot would take longer if it did a fsck.  

However, after the reboot, I was able to fsck after an unmount.  So, I guess all I needed was a reboot.

I will make the thread as solved.

Thanks for your help.

---

