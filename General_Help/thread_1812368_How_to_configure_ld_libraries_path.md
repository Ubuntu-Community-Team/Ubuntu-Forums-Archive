---
title: "How to configure ld libraries path?"
date: 2011-07-26
forum: General Help
---

### Post by twizol on 2011-07-26
Hi people, 

I'm trying to compile some c++ files.  (g++ version 4.5)
But i still get these errors... :
```
[...]
/usr/local/bin/ld: cannot find crtbegin.o: No such file or directory
/usr/local/bin/ld: cannot find -lstdc++
/usr/local/bin/ld: cannot find -lm
/usr/local/bin/ld: cannot find -lgcc_s
/usr/local/bin/ld: cannot find -lgcc
/usr/local/bin/ld: cannot find -lc
/usr/local/bin/ld: cannot find -lgcc_s
/usr/local/bin/ld: cannot find -lgcc
/usr/local/bin/ld: cannot find crtend.o: No such file or directory
[...]

```But it turns out these elements are located in :
/usr/lib/i386-linux-gnu/gcc/i686-linux-gnu/4.5

I've tried to add this path to $LD_LIBRARY_PATH (and even $LIBRARY_PATH, don't know the difference). 

And here is content of /etc/ld.so.conf.d/i686-linux-gnu.conf:
```
# Multiarch support
/lib/i386-linux-gnu
/usr/lib/i386-linux-gnu
/lib/i686-linux-gnu
/usr/lib/i686-linux-gnu
```Does anybody know how could i fix this ? 
Thanks a lot

---

### Post by Gyokuro on 2011-07-26
How have you installed your compiler? It seems your compiler installation is somehow broken. Can you try:

sudo apt-get install build-essential

---

### Post by twizol on 2011-07-26
Thanks for you answer.

build-essential is already installed, and my compiler is native from natty installation.

---

