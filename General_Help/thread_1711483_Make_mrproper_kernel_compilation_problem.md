---
title: "Make mrproper kernel compilation problem"
date: 2011-03-21
forum: General Help
---

### Post by FuzZy2006 on 2011-03-21
I'm trying to recompile the ubuntu kernel (2.6.35-27) in order to add a patch to it (perfctr, for the solaris performance analyzer hardware counters). 
After make mrproper I get this error: 

```
/home/arthur/linux-headers-2.6.35-27/ubuntu/aufs/Makefile:3: ubuntu/aufs/magic.mk: No such file or directory
make[2]: *** No rule to make target `ubuntu/aufs/magic.mk'.  Stop.
make[1]: *** [ubuntu/aufs] Error 2
make: *** [_clean_ubuntu] Error 2

```

---

### Post by andrewthomas on 2011-03-21
make mrproper cleans the source tree.

This is why there is no such file found.  

You need to post all the steps that you have done or post a link to instructions that you are following.

---

