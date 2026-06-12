---
title: "USB Startup Disk Problem"
date: 2009-12-05
forum: General Help
---

### Post by MiniStephan on 2009-12-05
I'm working with Karmic off of a USB Startup Disk (as indicated), and I updated linux-generic and the related packages, and now I'm getting a fatal error on boot up.  Is there any way I can fix the errors (revert to the old packages) whether in or out of the startup disk?  I'm working off a Karmic live CD right now.

---

### Post by MiniStephan on 2009-12-05
To be more specific, the error is "FATAL: Could not load /lib/modules/2.6.31-15-generic/modules.dep: No such file or directory"

---

### Post by MiniStephan on 2009-12-05
Bump.  Please help!

---

### Post by teward on 2009-12-05
Did you make sure you installed that package file for the 2.6.31-15-generic kernel?

Also, you don't get instant responses on these forums, unlike a chat room.  When you post, just wait for a response.  People like me have ways of finding posts we can help with.

---

### Post by wilee-nilee on 2009-12-05
Also how big is the thumb and how big did you set the persistent area of the thumb.

---

### Post by MiniStephan on 2009-12-05
> Also, you don't get instant responses on these forums, unlike a chat room. When you post, just wait for a response. People like me have ways of finding posts we can help with.

I'm sorry, I just can't leave the house until I access a file that's in there, and I'm rather impatient.  Please forgive me.

I installed the three packages that were held back from apt-get upgrade, linux-generic, linux-image-generic, and linux-headers (I believe those were the three).  If you know how I could get into the filesystem to replace the files, that would be helpful, but I'm sure it's not that easy.

I allocated about 15 GB on my USB HDD to the Startup Disk.

---

