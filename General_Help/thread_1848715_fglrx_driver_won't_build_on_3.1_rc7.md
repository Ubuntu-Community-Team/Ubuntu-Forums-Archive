---
title: "fglrx driver won't build on 3.1 rc7"
date: 2011-09-23
forum: General Help
---

### Post by Atamisk on 2011-09-23
Stop, wait! i know this kernel isn't officially supported, but i'm just askin'. No Launchpad report has been (or will be) filed.

As a personal little project to understand linux better, i was trying to compile the upstream latest kernel from Linus's repo to try and run it. The kernel seems to want to work, but fglrx won't build on it, and the kernel panics without it. In the log files for fglrx it complains about a missing smp_lock.h. I found some solutions online for this issue with bleeding-edge kernels (comment out the include statement in the offending file, copy a version of the missing file from the next-most-recent kernel, etc.), but this doesn't seem to work, and it still fails to build. 

Any Ideas?

Thanks, 
-Aaron

---

### Post by Atamisk on 2011-09-23
Bump?

---

### Post by Mark Phelps on 2011-09-23
If you're "just asking" -- then QUIT bumping!  The rule around here is no more often than once every 24 hours.  So, show some patience.

---

### Post by sumski on 2011-09-23
Arch's patch:

```
--- 10.10/common/lib/modules/fglrx/build_mod/2.6.x/Makefile    2010-09-22 09:15:33.000000000 +0200
+++ 10.10/common/lib/modules/fglrx/build_mod/2.6.x/Makefile    2010-10-01 17:57:21.057820899 +0200
@@ -66,6 +66,7 @@
                 -DFGL_GART_RESERVED_SLOT \
                 -DFGL_LINUX253P1_VMA_API \
                 -DPAGE_ATTR_FIX=$(PAGE_ATTR_FIX) \
+                -DCOMPAT_ALLOC_USER_SPACE=$(COMPAT_ALLOC_USER_SPACE) \
 
 ifeq ($(KERNELRELEASE),)
 # on first call from remote location we get into this path
```

Try with this, maintainer of fglrx package for Arch always uses newest kernel's so this could help

---

### Post by Atamisk on 2011-09-23
The Mainline source from AMD's website installed without issue. Still troubleshooting the kernel panic though =/

Thanks, 
--Aaron

---

