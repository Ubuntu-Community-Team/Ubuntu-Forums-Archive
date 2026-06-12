---
title: "Can't insert fuse.ko module"
date: 2010-10-13
forum: General Help
---

### Post by Koraq on 2010-10-13
I am trying to use the copyfs fuse based file system.

When I try to mount a copyfs file system it complains that no fuse module is loaded:

sudo copyfs-mount /home/davour/Hack/src /home/davour/Hack/src/vs
/home/davour/Hack/src
FATAL: Module fuse not found.
Could not load fuse kernel module !
davour@tsathoggua:~$

Looking for one I found this one:
/lib/modules/2.6.31-21-generic/kernel/fs/fuse/cuse.ko

Trying to load that one with insmod wont make copyfs happy.

I found a fuse.ko module in the package user-mode-linux, but it ends up in this weird directory:
/usr/lib/uml/modules/2.6.22-rc5/kernel/fs/fuse/fuse.ko

and when I try to insmod that one I get the error:
insmod: error inserting '/usr/lib/uml/modules/2.6.22-rc5/kernel/fs/fuse/fuse.ko': -1 Invalid module format

Which might not be that surprising, considering it looks like it was built for a different kernel than mine.

uname -r
2.6.31-22-generic

1) Where do I find a matching fuse.fo??

2) Why is this not included in the libfuse package?

2a) If fuse is part if generic, why is copyfs looking for fuse.ko??

Anyone?

---

### Post by Koraq on 2010-10-14
bump!

---

