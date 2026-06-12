---
title: "Ubuntu 11.04 Boot up Problem"
date: 2011-08-04
forum: General Help
---

### Post by werdnazner on 2011-08-04
I can't boot my natty. When I choose ubuntu between windows 7 and ubuntu it just lead me to a command line like interface (grub>).
The last time I opened ubuntu was when I updated it but the update went well.
I don't know what to do. Please I need help, all my important files are in ubuntu. Thanks

---

### Post by galvatron408 on 2011-08-04
oh yea, sounds like you booted up just fine. The next step is to tell grub where your kernel and init ram disk are. The last time I fixed this problem, I ran a tool called "grub-mkconfig"

from the man page - grub-mkconfig - generate a GRUB configuration file

> **werdnazner said:**
> I can't boot my natty. When I choose ubuntu between windows 7 and ubuntu it just lead me to a command line like interface (grub>).
The last time I opened ubuntu was when I updated it but the update went well.
I don't know what to do. Please I need help, all my important files are in ubuntu. Thanks

---

### Post by werdnazner on 2011-08-04
how will I get to the man page? sorry not really used to Ubuntu grub editing

---

### Post by galvatron408 on 2011-08-06
just run that command

grub-mkconfig

it will search for all your bootable partitions and do its magic!

---

