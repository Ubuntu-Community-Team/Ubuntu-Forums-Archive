---
title: "CompactFlash mkfs frustration"
date: 2009-11-27
forum: General Help
---

### Post by craigni on 2009-11-27
Hi Gurus,

Ubuntu 9.04: I plug in a compact flash into the USB connected reader.  It mounts automagically.

$ cat /etc/fstab
...
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
...

I try to make an ext2 filesystem on it

$ sudo mkfs -t ext2 -v /dev/fd0
mke2fs 1.41.4 (27-Jan-2009)
fs_types for mke2fs.conf resolution: 'ext2', 'floppy'
/dev/fd0: Read-only file system while setting up superblock

Any idea what's wrong and how to fix?

Many TIA,
Craig

---

