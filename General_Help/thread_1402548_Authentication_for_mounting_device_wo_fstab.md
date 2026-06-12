---
title: "Authentication for mounting device w/o fstab"
date: 2010-02-09
forum: General Help
---

### Post by GamePad64 on 2010-02-09
Hi, I use Ubuntu 9.04
I have a problem.

I have a file, containing ext2 file system ( mke2fs -F ~/fs.ext2 )
Is it possible to mount this file by user (not root) without editing fstab and from terminal?

P.S. Using /dev/loopN is not what I need. Maybe, it's possible to use FUSE, is it?

---

### Post by Leppie on 2010-02-09
yes, you can mount filesystems if added to the fuse group:
```
sudo adduser <username> fuse
```

---

