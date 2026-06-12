---
title: "Few questions about swapspace &amp; hibernate"
date: 2009-09-19
forum: General Help
---

### Post by maestrobwh1 on 2009-09-19
I installed karmic on a UDMA CF card / Expresscard reader.  Works great.

I later decided for added functionality to add a swapspace slighty larger than my RAM to the internal hard drive for hibernate functionality.

I added the appropriate lines to fstab using uuid and also I added 

> resume=UUID=(uuid of swap partition) 

to /etc/initramfs-tools/conf.d/resume

then I ran 

> sudo update-initramfs -u

Then rebooted.  It made no negative impact on my system, but on resuming, it just does a regular boot.  Apport will tell me, oddly when I am clearing firefox history, that there was an issue resuming from hibernate.

**Is there something else I should do to enable hibernate, or is this possibly just a karmic issue for now?**

**Also, if I have swap off, will the hibernate function activate it if it is called?**

---

### Post by maestrobwh1 on 2009-12-22
bump

---

