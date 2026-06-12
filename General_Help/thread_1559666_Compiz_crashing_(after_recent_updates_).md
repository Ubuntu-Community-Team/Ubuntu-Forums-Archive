---
title: "Compiz crashing (after recent updates ?)"
date: 2010-08-23
forum: General Help
---

### Post by vom on 2010-08-23
Running Lucid (x64) - Nvidia gfx / nvidia binary drivers.  I have not experienced this since I installed in April (when Lucid was released).  Since then, desktop has been rock solid, full desktop effects, video playing etc.

It seems that after one of the recent batches of updates (I know there was at least one kernel upgrade) compiz is bombing out about once a day.  It segfaults, and I'm not doing anything specific to trigger it - there is no apparent pattern to it.  I manually restart it by typing 'compiz' in a shell.

[30755.197122] compiz[1726]: segfault at 10 ip 00007ff0a2b78b71 sp 00007fff6cf3c038 error 4 in libGLcore.so.195.36.24[7ff0a1bea000+1458000]

I'm all up to date on packages.  So nvidia/kernel/etc are whatever the latest in Lucid are.

---

