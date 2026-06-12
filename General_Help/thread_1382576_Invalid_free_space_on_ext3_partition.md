---
title: "Invalid free space on ext3 partition"
date: 2010-01-16
forum: General Help
---

### Post by benow on 2010-01-16
Heyas,

I have a drive that I cannot free space on.  When I delete files, the usage goes down, but space is not freed, ie:
```
$ df -h /dev/sda1
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             459G  438G     0 100% /media/archive

```

I've tried a fsck -y /dev/sda1 and some errors were found, but the situation is not fixed.  It's an ext3 partition, and I've never seen this behaviour before.

Any suggestions, short of formatting?

---

### Post by bsh on 2010-01-16
try running this as root:
```
 du --max-depth=1 -k /media/archive | sort -nr | cut -f2 | xargs -d '\n' du -sh

```
this will tell you which folders use the most space, so you can find out where the space gone.

---

### Post by benow on 2010-01-16
No, it's not so much that the space is being used.  I know the big dirs.  If you look at the numbers above, the disk is 459G and 438G is being used, but there is 0B free, ie 21G is somewhere in nowhereland.  It's a filesystem corruption error, I'm pretty sure.  It doesn't seem to be bad blocks and there's no nasties logged in dmesg.  'e2fsck -y /dev/sda1' fails to correct the error.  I think I'm going to have to init a new drive, copy the contents over and reformat.

---

### Post by warfacegod on 2010-01-16
You have run up against the system reserve which defaults at 5%. 5% of 459 GB is right about 21 GB (22.95 in fact).

```
sudo tune2fs -m x /dev/sd
```

Make x whatever % you wish. If you don't have any OS files on the drive 0% is fine. Otherwise 1 or 2%. Add the appropriate letter to sd. Example: sdb2

---

### Post by benow on 2010-01-16
Awesome.  Been using linux for years, odd I've never seen that before.  Another trick to remember, I guess.  Thanks!

---

### Post by warfacegod on 2010-01-16
Certainly. Beware though, ext3 filesystems do not like to be filled 100%. I'd leave 2 or 3 GB free. Actually that pretty much goes for any filesystem.

---

