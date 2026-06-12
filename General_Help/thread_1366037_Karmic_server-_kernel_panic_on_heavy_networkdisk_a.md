---
title: "Karmic server- kernel panic on heavy network/disk activity"
date: 2009-12-28
forum: General Help
---

### Post by klinquist on 2009-12-28
I'm experiencing something very similar to this:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/147464?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/147464?comments=all)

New install of Ubuntu server 9.10.  As soon as I start copying large files to the machine (or just formatting a USB drive did it once too), I get a kernel panic within 5-30 seconds.  No keyboard input or anything, I get a screen of trace codes.    Seems to happen more, but not only, when VMWare server is running.  When the system is mostly idle, it'll run for days no problem.

Any troubleshooting ideas?

---

### Post by 3rdalbum on 2009-12-28
Check your memory, this sounds like a memory-related problem I used to have. Especially if it happens more often when you're running a program that reserves a big chunk of RAM.

---

### Post by klinquist on 2009-12-28
> **3rdalbum said:**
> Check your memory, this sounds like a memory-related problem I used to have. Especially if it happens more often when you're running a program that reserves a big chunk of RAM.


Thanks, I was thinking that.  I'll run Memtest86 overnight and see what happens.

---

### Post by klinquist on 2009-12-28
Update:

Ran memtest86... first 9 passes were OK... then after 6 hrs, it detected errors and locked up.  Said that my last DIMM had errors.

Replaced it, copying large files to the server, no problems!!

---

