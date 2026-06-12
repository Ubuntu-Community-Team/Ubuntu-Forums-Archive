---
title: "space on clean HDD reported as used"
date: 2011-02-22
forum: General Help
---

### Post by buffchick on 2011-02-22
So I just installed two brand new 1TB drives. Setup raid 1 with EXT4. It's resyncing now but I did df -h and it shows:

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/md1              917G  200M  871G   1% /mnt/backup
```My questions are:
 1) why does it show 917G instead of 1000G (even with manufacturer reporting differences is it really going to be 83 gigs?
 2) why does it say only 871G are available? WTF is that about?
 3) What's with the 1% usage? The only thing showing on the drives is the standard fsck lost+found folder.

Did I mention I just pulled these drives out of the static bags and installed them?

---

### Post by surfer on 2011-02-22
read [this thread]("http://ubuntuforums.org/showthread.php?t=1398812").

---

### Post by buffchick on 2011-03-01
that was totally it! THANK YOU!

---

