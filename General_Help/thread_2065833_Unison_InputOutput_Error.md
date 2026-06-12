---
title: "Unison Input/Output Error"
date: 2012-10-03
forum: General Help
---

### Post by ndstate on 2012-10-03
Hello,

When I try to sync my remote server with unison I get the following error:

Uncaught exception Sys_error("Input/output error")

I have the same version of unison on both the server and my computer.  I was able to connect before, but I started getting this issue after I had to restart my laptop while unison was running - because unity froze.

I have purged and reinstalled unison on both the server and my laptop. Any ideas?

Thansk

---

### Post by 2F4U on 2012-10-03
Seems as if something is corrupt, maybe one of the files Unison keeps to track changes. Did you also remove the hidden .unison folders and Unison's log files on both machines? If that is not the solution, did you check your disks for errors?

---

### Post by ndstate on 2012-10-12
It randomly started working after uninstalling and installing a few times.  Thanks.

---

