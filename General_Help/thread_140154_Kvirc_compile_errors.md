---
title: "Kvirc compile errors"
date: 2006-03-05
forum: General Help
---

### Post by Sai on 2006-03-05
I tried to compile kvirc 3.2.0 from sources and got this error:
```
make[4]: Entering directory `/home/sai/temp/compile/kvirc-3.2.0/src/kvirc/build'
if g++ -DHAVE_CONFIG_H -I. -I. -I../../../src  -I/home/sai/temp/compile/kvirc-3.2.0/src/kvilib/include/ -I/home/sai/temp/compile/kvirc-3.2.0/src/kvirc/include/ -I/usr/include/qt3 -I/usr/include -I/usr/include -I/usr/include/kde -D_REENTRANT -DREENTRANT -DGLOBAL_KVIRC_DIR=\"/usr/local/share/kvirc/3.2.0\"   -g -O2 -MT kvi_action.o -MD -MP -MF ".deps/kvi_action.Tpo" \
  -c -o kvi_action.o `test -f '../kernel/kvi_action.cpp' || echo './'`../kernel/kvi_action.cpp; \
then mv -f ".deps/kvi_action.Tpo" ".deps/kvi_action.Po"; \
else rm -f ".deps/kvi_action.Tpo"; exit 1; \
fi
/home/sai/temp/compile/kvirc-3.2.0/src/kvirc/include/kvi_console.h:108: error: &#8216;KviIrcSocketMonitor&#8217; has not been declared
/home/sai/temp/compile/kvirc-3.2.0/src/kvirc/include/kvi_console.h:109: error: &#8216;KviIrcSocketMonitor&#8217; has not been declared
make[4]: *** [kvi_action.o] &#1054;&#1096;&#1080;&#1073;&#1082;&#1072; 1
make[4]: Leaving directory `/home/sai/temp/compile/kvirc-3.2.0/src/kvirc/build'
make[3]: *** [all-recursive] &#1054;&#1096;&#1080;&#1073;&#1082;&#1072; 1
make[3]: Leaving directory `/home/sai/temp/compile/kvirc-3.2.0/src/kvirc'
make[2]: *** [all-recursive] &#1054;&#1096;&#1080;&#1073;&#1082;&#1072; 1
make[2]: Leaving directory `/home/sai/temp/compile/kvirc-3.2.0/src'
make[1]: *** [all] &#1054;&#1096;&#1080;&#1073;&#1082;&#1072; 2
make[1]: Leaving directory `/home/sai/temp/compile/kvirc-3.2.0/src'
make: *** [all-recursive] &#1054;&#1096;&#1080;&#1073;&#1082;&#1072; 1
```
i'm not a programmer and don't know what error it is. I tried to use some gcc versions (3.4 and 4.0) but error was the same. The way i compile it is:
```
cd /path/to/sources/
./configure --enable-debug #i get error no matter what option i set there
make kvirc

```
I don't get any error during configure.
What can i do to fix this error and compile kvirc?
Thanks for any help.

---

### Post by Sai on 2006-03-07
Please anyone, help me somehow.

---

### Post by Sai on 2006-03-12
Problem solved by compiling sources from cvs.

---

