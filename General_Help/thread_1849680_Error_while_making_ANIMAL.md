---
title: "Error while making ANIMAL"
date: 2011-09-25
forum: General Help
---

### Post by anshulfy on 2011-09-25
Hi, I was trying to install Animal, required for Scilab image processing tool.  I am getting error while running MAKE. Please help me.


```
Making all in animal
make[1]: Entering directory `/home/anshul/Desktop/animal-0.15.2/animal'
make  all-am
make[2]: Entering directory `/home/anshul/Desktop/animal-0.15.2/animal'
if /bin/bash ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I. -I.. -I..  -I/usr/local/include/ImageMagick   -g -O2 -W -Wall -Wno-implicit-int -MT distmaps.lo -MD -MP -MF ".deps/distmaps.Tpo" -c -o distmaps.lo distmaps.c; \
    then mv -f ".deps/distmaps.Tpo" ".deps/distmaps.Plo"; else rm -f ".deps/distmaps.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I. -I.. -I.. -I/usr/local/include/ImageMagick -g -O2 -W -Wall -Wno-implicit-int -MT distmaps.lo -MD -MP -MF .deps/distmaps.Tpo -c distmaps.c  -fPIC -DPIC -o .libs/distmaps.o
distmaps.c: In function ‘edt_meijster2000’:
distmaps.c:852: error: nested function ‘edt_meijster_2D_from_1D’ declared but never defined
make[2]: *** [distmaps.lo] Error 1
make[2]: Leaving directory `/home/anshul/Desktop/animal-0.15.2/animal'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/anshul/Desktop/animal-0.15.2/animal'
make: *** [all-recursive] Error 1

```

Thanks in advance.
--
Anshul

---

### Post by patryk77 on 2011-09-25
This error message is actually complaining about an error in the source code, nothing to do with Ubuntu per se.

Your best bet would be to report this to the authors of Animal, especially if they have a Bug tracker.

---

### Post by anshulfy on 2011-09-25
Hi, Thanks for reply. I already wrote to the authors.  :)

---

### Post by kali26 on 2012-01-20
did you run ./configure?

---

