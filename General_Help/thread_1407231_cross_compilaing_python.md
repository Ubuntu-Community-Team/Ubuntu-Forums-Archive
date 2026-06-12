---
title: "cross compilaing python"
date: 2010-02-15
forum: General Help
---

### Post by shariefbe on 2010-02-15
Hello,
   I am trying to cross compile python for my ARM board. In that i am getting some error. How to overcome from that?
```

  Modules/_sre.o  Modules/_codecsmodule.o  Modules/zipimport.o  Modules/symtablemodule.o  Modules/xxsubtype.o
arm-none-linux-gnueabi-ranlib libpython2.6.a
arm-none-linux-gnueabi-gcc  -Xlinker -export-dynamic -o python \
			Modules/python.o \
			libpython2.6.a -lpthread -ldl  -lpthread -lutil   -lm  
libpython2.6.a(posixmodule.o): In function `posix_tmpnam':
/mnt/omap/sources/Python-2.6.4/./Modules/posixmodule.c:7180: warning: the use of `tmpnam_r' is dangerous, better use `mkstemp'
libpython2.6.a(posixmodule.o): In function `posix_tempnam':
/mnt/omap/sources/Python-2.6.4/./Modules/posixmodule.c:7135: warning: the use of `tempnam' is dangerous, better use `mkstemp'
./python: 1: Syntax error: word unexpected (expecting ")")
make: *** [sharedmods] Error 2

```
Please help me

---

