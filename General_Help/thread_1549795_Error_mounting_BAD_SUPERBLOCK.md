---
title: "Error mounting BAD SUPERBLOCK"
date: 2010-08-10
forum: General Help
---

### Post by schwabdale on 2010-08-10
My computer came up with grub rescue. 
So, I booted off the CD and tried to access the hard drive. Now
the hard drive comes up "Wrong fs type, bad option, bad superblock on /dev/sda1.


What can I do... Fix the filesystem?

---

### Post by mikewhatever on 2010-08-10
Yes, a file system check is in order. While running from the live cd, open a Terminal window and use the following command:
```
sudo fsck -yv /dev/sda1
```
It should check the file system and spit some output, post that here.

---

### Post by schwabdale on 2010-08-10
> **mikewhatever said:**
> Yes, a file system check is in order. While running from the live cd, open a Terminal window and use the following command:
```
sudo fsck -yv /dev/sda1
```It should check the file system and spit some output, post that here.

Here's the output
ubuntu@ubuntu:~$ sudo fsck -yv /dev/sda1
fsck from util-linux-ng 2.17
e2fsck 1.41.10 (10-Feb-2009)
fsck.ext4: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda1
Could this be a zero-length partition?

---

### Post by schwabdale on 2010-08-10
bump

---

### Post by schwabdale on 2010-08-10
[http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)

---

