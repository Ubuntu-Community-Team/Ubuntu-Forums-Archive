---
title: "Software raid not assembing (device busy)"
date: 2009-08-30
forum: General Help
---

### Post by Redalert Commander on 2009-08-30
Hi,

I'm trying out the Karmic Alpha 4, but running into some problems, mostly fixed them, but I'm not sure if this one is related to just Karmic.

My system has 4 drives:
sda: 3 partitions: debian lenny(ext3), windows(ntfs), swap area(swap)
sdb: 1 linux raid partition (ext3)
sdc: 1 linux raid partition (ext3)
sdd: 2 partitions: 1 doing /boot for karmic (ext3) and 1 / for karmic (ext4)

The raid array (mirror using sdb1 and sdc1) was constructed when I was running Ubuntu Hardy, after upgrading to Jaunty, later switching to Debian Lenny, no problems occurred (the installer activated the array for me).
Now I want to access the array from karmic as well.
The alternate installer detected that there was an array, but I couldn't find an option to use it, I figured I'd fix this after installation.

Now, when I wanted to assemble the array (after installing mdadm) I got the following error (might not be in that order, but that's what it said):
```
$ sudo mdadm --assemble /dev/md0 /dev/sdb1 /dev/sdc1
Aborted assemble: /dev/sdb1 has no superblock
/dev/sdb1: resource or device busy
```

I looked around for possible causes, but I didn't found anything useful (motherboard fake raid is already disabled).
The array works perfectly fine in Debian Lenny.

---

### Post by Redalert Commander on 2009-08-30
My bad.. forgot to remove the dmraid utility.

---

