---
title: "which filesystem? rsync to external hard drive"
date: 2009-12-05
forum: General Help
---

### Post by rowbird on 2009-12-05
Hi, I was just wondering, I have 3 ext3 computers that need to be backed up with rsync to an external hard drive. Should I format my external to ext2, 3, or 4? any recommendations? Thanks

---

### Post by ibuclaw on 2009-12-05
Any filesystem will do, really - it won't make much difference.
In a Nutshell:
ext2 = 2nd Extended Filesystem
ext3 = ext2 + Journal
ext4 = ext3 + Some extra features and somewhat geared more towards performance.

I've never really used ext2 in production, except for /boot partitions where I know data is written and generally doesn't change much after that.
With ext3, I've only ever had a filesystem crash once after 2 years. Took some fsck'ing, but I don't think (as far as I am aware) I lost any data from that.
With ext4, haven't used it long enough to experience anything majorly bad with it.

All you best be concerned about is the health of the physical disks themselves.

Regards
Iain

---

