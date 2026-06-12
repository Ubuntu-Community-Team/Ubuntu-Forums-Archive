---
title: "Error Compile Amaya"
date: 2010-04-03
forum: General Help
---

### Post by mahsom on 2010-04-03
Hello

when run make , I do receive this Error :
```

make[1]: Entering directory `/home/mahsom/Amaya11.3.1/Amaya/linux/tools'
make[2]: Entering directory `/home/mahsom/Amaya11.3.1/Amaya/linux/tools/mkdep'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/mahsom/Amaya11.3.1/Amaya/linux/tools/mkdep'
make[2]: Entering directory `/home/mahsom/Amaya11.3.1/Amaya/linux/tools/cextract-1.7'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/mahsom/Amaya11.3.1/Amaya/linux/tools/cextract-1.7'
make[1]: Leaving directory `/home/mahsom/Amaya11.3.1/Amaya/linux/tools'
make[1]: Entering directory `/home/mahsom/Amaya11.3.1/Amaya/linux/Mesa'
make[2]: Entering directory `/home/mahsom/Amaya11.3.1/Amaya/linux/Mesa/src'
Making sources for linux-x86-static
make[3]: Entering directory `/home/mahsom/Amaya11.3.1/Amaya/linux/Mesa/src/mesa'
make[4]: Entering directory `/home/mahsom/Amaya11.3.1/Amaya/linux/Mesa/src/mesa'
make[5]: Entering directory `/home/mahsom/Amaya11.3.1/Amaya/linux/Mesa/src/mesa/x86'
make[5]: Nothing to be done for `default'.
make[5]: Leaving directory `/home/mahsom/Amaya11.3.1/Amaya/linux/Mesa/src/mesa/x86'
make[4]: Leaving directory `/home/mahsom/Amaya11.3.1/Amaya/linux/Mesa/src/mesa'
make[3]: Leaving directory `/home/mahsom/Amaya11.3.1/Amaya/linux/Mesa/src/mesa'
make[3]: Entering directory `/home/mahsom/Amaya11.3.1/Amaya/linux/Mesa/src/glu'
make[4]: Entering directory `/home/mahsom/Amaya11.3.1/Amaya/linux/Mesa/src/glu/sgi'
make[5]: Entering directory `/home/mahsom/Amaya11.3.1/Amaya/linux/Mesa/src/glu/sgi'
make[5]: `../../../lib/libGLU.a' is up to date.
make[5]: Leaving directory `/home/mahsom/Amaya11.3.1/Amaya/linux/Mesa/src/glu/sgi'
make[4]: Leaving directory `/home/mahsom/Amaya11.3.1/Amaya/linux/Mesa/src/glu/sgi'
make[3]: Leaving directory `/home/mahsom/Amaya11.3.1/Amaya/linux/Mesa/src/glu'
make[3]: Entering directory `/home/mahsom/Amaya11.3.1/Amaya/linux/Mesa/src/glw'
make[3]: Nothing to be done for `default'.
make[3]: Leaving directory `/home/mahsom/Amaya11.3.1/Amaya/linux/Mesa/src/glw'
make[2]: Leaving directory `/home/mahsom/Amaya11.3.1/Amaya/linux/Mesa/src'
make[2]: Entering directory `/home/mahsom/Amaya11.3.1/Amaya/linux/Mesa/progs'
Making programs for linux-x86-static
make[2]: Leaving directory `/home/mahsom/Amaya11.3.1/Amaya/linux/Mesa/progs'
make[1]: Leaving directory `/home/mahsom/Amaya11.3.1/Amaya/linux/Mesa'
make[1]: Entering directory `/home/mahsom/Amaya11.3.1/Amaya/linux/wxWidgets_RELEASE'
(if test -d utils/wxrc ; then cd utils/wxrc && make all ; fi)
make[1]: Leaving directory `/home/mahsom/Amaya11.3.1/Amaya/linux/wxWidgets_RELEASE'
make -C libwww
make[1]: Entering directory `/home/mahsom/Amaya11.3.1/Amaya/linux/libwww'
make[1]: *** No targets specified and no makefile found.  Stop.
make[1]: Leaving directory `/home/mahsom/Amaya11.3.1/Amaya/linux/libwww'
make: *** [libwww] Error 2
```

I use ubuntu 9.04 .
Thank you ...

---

### Post by gmargo on 2010-04-03
I was able to compile and install the latest Amaya on both 8.04 Hardy and 9.04 Jaunty following these directions: [http://www.w3.org/Amaya/User/Autoconf.html](http://www.w3.org/Amaya/User/Autoconf.html).  Perhaps some stage of the configure step did not complete?

---

