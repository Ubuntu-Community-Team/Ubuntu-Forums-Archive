---
title: "libtool: Version mismatch error"
date: 2010-09-04
forum: General Help
---

### Post by Saprissa on 2010-09-04
I'm in need of some assistance. I'm trying to install lcms2 and I get this error.

```
/bin/bash ../libtool --tag=CC   --mode=compile gcc -std=gnu99 -DPACKAGE_NAME=\"lcms2\" -DPACKAGE_TARNAME=\"lcms2\" -DPACKAGE_VERSION=\"2.0\" -DPACKAGE_STRING=\"lcms2\ 2.0\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE_URL=\"\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -DLT_OBJDIR=\".libs/\" -DHasJPEG=1 -DHasZLIB=1 -DHasTIFF=1 -DHAVE_TIFFCONF_H=1 -I. -I../include -I../include    -g -O2 -MT cmscnvrt.lo -MD -MP -MF .deps/cmscnvrt.Tpo -c -o cmscnvrt.lo cmscnvrt.c
[B]libtool: Version mismatch error.  This is libtool 2.2.7a, but the
libtool: definition of this LT_INIT comes from libtool 2.2.6b.
libtool: You should recreate aclocal.m4 with macros from libtool 2.2.7a
libtool: and run autoconf again.[/B]
make[1]: *** [cmscnvrt.lo] Error 63

```

I'm clueless about how to "recreate aclocal.m4 with libtool 2.2.6b".

Anyone have any good advice?

---

### Post by Saprissa on 2010-09-04
> **Saprissa said:**
> I'm in need of some assistance. I'm trying to install lcms2 and I get this error.

```
/bin/bash ../libtool --tag=CC   --mode=compile gcc -std=gnu99 -DPACKAGE_NAME=\"lcms2\" -DPACKAGE_TARNAME=\"lcms2\" -DPACKAGE_VERSION=\"2.0\" -DPACKAGE_STRING=\"lcms2\ 2.0\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE_URL=\"\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -DLT_OBJDIR=\".libs/\" -DHasJPEG=1 -DHasZLIB=1 -DHasTIFF=1 -DHAVE_TIFFCONF_H=1 -I. -I../include -I../include    -g -O2 -MT cmscnvrt.lo -MD -MP -MF .deps/cmscnvrt.Tpo -c -o cmscnvrt.lo cmscnvrt.c
[B]libtool: Version mismatch error.  This is libtool 2.2.7a, but the
libtool: definition of this LT_INIT comes from libtool 2.2.6b.
libtool: You should recreate aclocal.m4 with macros from libtool 2.2.7a
libtool: and run autoconf again.[/B]
make[1]: *** [cmscnvrt.lo] Error 63

```

I'm clueless about how to "recreate aclocal.m4 with libtool 2.2.6b".

Anyone have any good advice?


I should have said I'm clueless how to recreate aclocal.m4 with libtool 2.2.7b

See how clueless?

---

### Post by Saprissa on 2010-09-05
Gratuitous kick...

---

### Post by elpraga on 2011-03-23
I had the same problem. Finally I managed to fix it. Download and libtool-2.2.8 and compile it with --prefix=/opt. Install it. After doing so, change all references to libtool in all Makefiles to the new one. Then I managed to compile it.

---

