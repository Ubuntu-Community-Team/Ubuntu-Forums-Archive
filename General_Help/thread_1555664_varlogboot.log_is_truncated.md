---
title: "/var/log/boot.log is truncated"
date: 2010-08-18
forum: General Help
---

### Post by NHclimber on 2010-08-18
I'm trying to track down a problem with udev so I turned on udev logging and rebuilt the initramfs.

Unfortunately since plymouth buffers the boot messages and flushes them to disk later, I'm only getting about 32K worth of log (the last 32K).

Does anyone have ideas for getting the complete log?  Also, at least one console message isn't being captured - any ideas why not?

---

### Post by NHclimber on 2010-08-19
Yep - the plymouth logger has a fixed maximum buffer of 32k that it decapitates on overflow.  I had to fix the source.

---

