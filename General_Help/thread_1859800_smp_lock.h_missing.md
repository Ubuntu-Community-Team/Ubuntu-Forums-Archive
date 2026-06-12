---
title: "smp_lock.h missing"
date: 2011-10-14
forum: General Help
---

### Post by nightfever on 2011-10-14
I'm trying to compile alsa and I'm getting this error

seq_clientmgr.c:27:28: fatal error: linux/smp_lock.h: No such file or directory
compilation terminated.

I found out that this file is missing from newer kernel versions.
One solution would be to get the file from an older kernel source (which I did). But I don't know where to put it.
Any help?

---

