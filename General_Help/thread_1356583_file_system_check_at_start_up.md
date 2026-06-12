---
title: "file system check at start up"
date: 2009-12-16
forum: General Help
---

### Post by tapas_mishra on 2009-12-16
I am getting a message to check file system when ever the system starts it asks to give root password to drop to maintenance shell but then I am not clear with what should I do in there 
here is the log of /var/log/fsck/checkfs

```

Log of fsck -C -R -A -a
Wed Dec 16 19:38:38 2009

fsck 1.41.4 (27-Jan-2009)
/dev/sda10: clean, 51/52208 files, 52636/104391 blocks
/dev/sda11 contains a file system with errors, check forced.
/dev/sda11: Unattached inode 149913


/dev/sda11: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
        (i.e., without -a or -p options)
fsck died with exit status 4

Wed Dec 16 19:39:52 2009

```

---

### Post by iponeverything on 2009-12-16
Give the root password when prompted then run the fsck.

If it is ext3 the command line will look like this:

```
fsck.ext3 -y /dev/sda11

```

---

### Post by tapas_mishra on 2009-12-17
Ok it is working.

---

