---
title: "webcleaner - jsprf.c:644: error: incompatible types ..."
date: 2010-09-28
forum: General Help
---

### Post by erngab on 2010-09-28
Webcleaner filtering HTTP proxy
when I - ./configure --enable-shared && make
I'm stuck

> c -o jsprf.lo jsprf.c; \
        then mv -f ".deps/jsprf.Tpo" ".deps/jsprf.Plo"; else rm -f ".deps/jsprf.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I.. -I.. -DEXPORT_JS_API -DXP_UNIX -g -O2 -Wall -pedantic -std=c99 -D_BSD_SOURCE -MT jsprf.lo -MD -MP -MF .deps/jsprf.Tpo -c jsprf.c  -fPIC -DPIC -o .libs/jsprf.o
jsprf.c: In function 'BuildArgArray':
jsprf.c:644: error: incompatible types when assigning to type 'va_list' from type 'struct __va_list_tag *'
make[4]: *** [jsprf.lo] Error 1
make[4]: Leaving directory `/media/sdb5/Ernest/erngab/Desktop Linux/SECURITY/webcleaner-2.41/libjs'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/media/sdb5/Ernest/erngab/Desktop Linux/SECURITY/webcleaner-2.41/libjs'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/media/sdb5/Ernest/erngab/Desktop Linux/SECURITY/webcleaner-2.41/libjs'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/media/sdb5/Ernest/erngab/Desktop Linux/SECURITY/webcleaner-2.41'
make: *** [all] Error 2I do not know how to proceed, [COLOR=#000000]any help will be good.[/COLOR]

---

