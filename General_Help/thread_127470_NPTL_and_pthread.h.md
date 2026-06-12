---
title: "NPTL and pthread.h"
date: 2006-02-09
forum: General Help
---

### Post by jivy on 2006-02-09
My kernel uses the NPTL implementation of pthreads, but the /usr/include/pthread.h file is actually a LinuxThreads implementation. The real NPTL version is in /usr/include/nptl. This seems kinda funky to me, since getconf clearly says I am using NPTL.
```
$ getconf GNU_LIBPTHREAD_VERSION
NPTL 2.3.5
```
Shouldn't the standard pthread.h file/location have the actual implementation my system uses? What can I do to change it so that my default locations (the libraries as well) have the NPTL versions rather than LinuxThreads?

Sorry if this seems like a dumb question... I'm still pretty new to Ubuntu/Linux.

---

### Post by lolindrath on 2008-01-17
Hi jivy,

To make sure the NPTL version of pthreads is included make sure you put -L/usr/lib/nptl and -I/usr/include/nptl in your compile/link flags. That'll make sure the correct version gets in there.

--Andy

---

