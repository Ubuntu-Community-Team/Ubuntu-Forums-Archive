---
title: "URGENT: Hard drive keeps failing, borks system, please help!"
date: 2010-05-03
forum: General Help
---

### Post by anandamide on 2010-05-03
Hi folks

Well this is a puzzler. I can't remember doing anything different / installing anything on my system, but a couple of days ago I started getting error messages about my Linux partition being a read-only filesystem. 

Puzzled, I did a hard-reboot (soft didn't work).

This failed, with the same complaint (read only filesystem). 

I booted from a livecd, ran gparted and checked / fixed errors.

This worked, but around ten mins into a normal session the same error appears. I go through the same procedure, and again it works for about 10 mins.

Here's the output from dmesg when I first try to mount the hard drive (sda5) from the liveCD session (before fixing with gparted):

```
[  424.504915] journal_bmap: journal block not found at offset 11276 on sda5
[  424.504921] JBD: bad block at offset 11276
[  424.504929] journal_bmap: journal block not found at offset 11439 on sda5
[  424.504931] JBD: bad block at offset 11439
[  424.504937] JBD: recovery failed
[  424.504940] EXT3-fs: error loading journal.
``` 

I'm running 9.10.

Any ideas?

---

### Post by dino99 on 2010-05-03
sda5 is complaining: check if its not full

making room:
- install gconf-cleaner and run it (yes to all)

sudo dpkg --configure -a
sudo apt-get update
sudo apt-get install -f

if still trouble: force a fsck on next boot ( sudo shutdown -F -r now ) or sudo touch /forcefsck

---

### Post by anandamide on 2010-05-03
Thanks for the response.

sda5 has just over 40 gigs free. Unfortunately I don't know how to force an fsck on reboot (and not sure it would work; entering a recovery shell brings up an ash prompt which doesn't understand to command).

After just going through the same cycle of shutdown, livecd and filesystem repair, I've got the following output from fsck:

```
ubuntu@ubuntu:~$ sudo fsck /dev/sda5
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
/dev/sda5: recovering journal
Clearing orphaned inode 49313 (uid=1000, gid=1003, mode=0100600, size=0)
Clearing orphaned inode 88623 (uid=1000, gid=1003, mode=0100644, size=76248)
/dev/sda5: clean, 560076/5392160 files, 10848890/21942774 blocks
```

BTW the shutdown option you gave did work.

---

### Post by dino99 on 2010-05-03
> **anandamide said:**
> Thanks for the response.

sda5 has just over 40 gigs free. Unfortunately I don't know how to force an fsck on reboot (and not sure it would work; entering a recovery shell brings up an ash prompt which doesn't understand to command).

After just going through the same cycle of shutdown, livecd and filesystem repair, I've got the following output from fsck:

```
ubuntu@ubuntu:~$ sudo fsck /dev/sda5
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
/dev/sda5: recovering journal
Clearing orphaned inode 49313 (uid=1000, gid=1003, mode=0100600, size=0)
Clearing orphaned inode 88623 (uid=1000, gid=1003, mode=0100644, size=76248)
/dev/sda5: clean, 560076/5392160 files, 10848890/21942774 blocks
```

BTW the shutdown option you gave did work.

should be ok now  :D

---

### Post by anandamide on 2010-05-03
Hmm - I'm afraid not. Again, works for all of ten minutes, then borks.

---

### Post by john newbuntu on 2010-05-03
Check your HDD's health with disk utility (System->admin->disk utility). Click on the drive, choose smart data and run extended tests.
If you know your disk's manufacturer (Samsung, Hitachi etc), go to their website, download disk checking tools and run them to reconfirm the results.

---

