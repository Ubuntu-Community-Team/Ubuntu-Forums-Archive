---
title: "Corrupted my ext4 partition"
date: 2010-06-28
forum: General Help
---

### Post by xtjacob on 2010-06-28
Hello everyone, I was resizing my ext4 partition and I cancelled it while it was at the reading stage think it was only reading it and nothing else, but now it is corrupt. When I run 'fsck -n /dev/sda5' I get the error: ```
fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sda5

```
Is there anyway I can fix this, at least enough to read from it?

---

### Post by CharlesA on 2010-06-28
Does it even let you mount the device?

If you can't mount it, then I hope you have a good recent backup.

Rule of thumb when messing with partitions is always backup before you do so, since if anything goes wrong, you'll more than likely lose data.

---

### Post by xtjacob on 2010-06-28
Nope, I don't have any backups of this computer.

---

### Post by CharlesA on 2010-06-28
You could try using something like testdisk, but I have a feeling that you aren't going to be able to get the data back. Worth a shot, tho. :)

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by oldfred on 2010-06-29
Slightly different fsck commands to run from liveCD.

From liveCD so everything is unmounted
sudo e2fsck -C0 -p -f -v /dev/sdb1
if errors:
sudo e2fsck -f -y -v /dev/sdb1

[http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)

---

