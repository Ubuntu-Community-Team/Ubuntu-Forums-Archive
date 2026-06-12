---
title: "Kernel incremental building"
date: 2010-01-01
forum: General Help
---

### Post by ghostknife on 2010-01-01
I've been making some changes to the kernel to fix a problem I'm experiencing. Though I have to keep rebuilding everything from scratch, which wastes time.

I use the following 2 commands
fakeroot debian/rules clean
CONCURRENCY_LEVEL=2 AUTOBUILD=1 NOEXTRAS=1 fakeroot debian/rules binary-generic

The first cleans, then 2nd builds.

If I skip the first, it just rebuilds the modules from the object files. No compiling happens, so any changes I made since the previous build are not included in the new kernel image/modules.

How can I do an incremental build?

---

### Post by ghostknife on 2010-01-01
I only noticed now that there is a better forum for this. If a moderator can move this, thanks.

---

