---
title: "Can anyone provide me with ext4.ko for kernel 2.5.31.6 (x86_64)?"
date: 2011-02-26
forum: General Help
---

### Post by Cygon on 2011-02-26
Hi!

I'm trying to install a server I just rented, but the only option I have is to go through the rescue system (running Ubuntu kernel 2.6.31.6 x86_64).

To my dismay, the rescue system's kernel doesn't have ext4 built in nor does it contain a loadable module for ext4. Thus my question - could anyone running above kernel version (and, most importantly, in x86_64 flavor) lend me his ext4.ko (from /lib/modules/2.6.31.6-live/kernel/fs/) somewhere?

Otherwise I'll be forced to remain with ext3 or maybe ext4 without extents.

Thanks!

---

### Post by An Sanct on 2011-02-26
Couldn't you get it from synaptic?
packages: *e2fslibs* and *e2fsprogs*

> The ext2, ext3 and ext4 file systems are successors of the original ext

---

