---
title: "FAT32 partition randomly becomes read-only"
date: 2011-08-29
forum: General Help
---

### Post by morrna on 2011-08-29
I'm having a maddening problem with a FAT32 partition on my laptop.  When I start it up it runs fine at first, then all of a sudden I get messages like this:
```
rm: cannot remove `anyfile.txt': Read-only file system
```

This has never happened before today.  The really bizarre thing is that things work fine when the system first starts, and I haven't pinpointed what the trigger is yet.

In case it matters, I'm running 10.10 Meerkat.  Here's the line for the filesystem in my fstab:
```
/dev/sda7       /home/morrisng/shared   vfat    users,rw,dmask=022,fmask=022,uid=morrisng,gid=morrisng  0       0

```

It's a FAT32 partition so that I can have a workspace that's accessible from both Ubuntu and Windows 7 (I dual boot).  Could this be part of the problem?  I really don't know where to look for the error, so any help on things to try or look for is appreciated.

---

### Post by searchfgold6789 on 2011-08-29
It sounds like a problem with the disk or filesystem to me. Try checking the file system, and the SMART status of the drive.

---

### Post by morrna on 2011-08-30
Thanks for the ideas.  I did do fsck from a live cd, and that didn't seem to make any changes.  I didn't know about the SMART status, though, I'll have to look up more about that.

---

### Post by pqwoerituytrueiwoq on 2011-08-30
from windows run 
chkdsk X: /f
X= drive letter for file system

---

