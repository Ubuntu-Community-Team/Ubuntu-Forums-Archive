---
title: "accidental --strip-debug in usr, bin, sbin..."
date: 2010-07-08
forum: General Help
---

### Post by lordskid on 2010-07-08
I was following LFS 6.6, and accidentally stripped debugging symbols from my ubuntu install, will it cause any problems?

by issuing the command below...
```
 
warning pls do not execute this command if you don't know what you are doing.

/tools/bin/find /{,usr/}{bin,lib,sbin} -type f \
 -exec /tools/bin/strip --strip-debug '{}' ';'


```

---

