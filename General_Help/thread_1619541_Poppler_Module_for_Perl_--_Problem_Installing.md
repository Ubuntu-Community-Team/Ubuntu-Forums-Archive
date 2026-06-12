---
title: "Poppler Module for Perl -- Problem Installing"
date: 2010-11-11
forum: General Help
---

### Post by flbiggs on 2010-11-11
I have been trying to install the Poppler Module for Perl, and make is throwing the following error:

[INDENT]cc -c  -pthread -D_REENTRANT -I/usr/include/poppler/glib -I/usr/include/poppler -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/cairo -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gio-unix-2.0/ -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12   -D_REENTRANT -D_GNU_SOURCE -DDEBIAN -fno-strict-aliasing -pipe -fstack-protector -I/usr/local/include -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -O2 -g   -DVERSION=\"0.03\" -DXS_VERSION=\"0.03\" -fPIC "-I/usr/lib/perl/5.10/CORE"   Poppler.c
cc -c  -pthread -D_REENTRANT -I/usr/include/poppler/glib -I/usr/include/poppler -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/cairo -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gio-unix-2.0/ -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12   -D_REENTRANT -D_GNU_SOURCE -DDEBIAN -fno-strict-aliasing -pipe -fstack-protector -I/usr/local/include -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -O2 -g   -DVERSION=\"0.03\" -DXS_VERSION=\"0.03\" -fPIC "-I/usr/lib/perl/5.10/CORE"   Goo.c
cc: Goo.c: No such file or directory
cc: no input files
make: *** [Goo.o] Error 1[/INDENT]

In case it matters, in generating the make file during the initial install step, the output of perl Makefile.PL includes the following:

[INDENT]Unrecognized argument in LIBS ignored: '-pthread'[/INDENT]

The readme lists cairo, poppler and glib as dependencies. I have cairo, poppler and glib packages installed (and development packages).  I have install cairo and glib modules from CPAN.  I regularly use cairo and gtk from perl without problems.  

I am at a loss as to what this Goo.c error is.  Any ideas?  Is any more information needed?  Thanks

---

### Post by luigi_mb on 2010-11-12
> **flbiggs said:**
> I have been trying to install the Poppler Module for Perl, and make is throwing the following error:

[INDENT]cc -c  -pthread -D_REENTRANT -I/usr/include/poppler/glib -I/usr/include/poppler -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/cairo -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gio-unix-2.0/ -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12   -D_REENTRANT -D_GNU_SOURCE -DDEBIAN -fno-strict-aliasing -pipe -fstack-protector -I/usr/local/include -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -O2 -g   -DVERSION=\"0.03\" -DXS_VERSION=\"0.03\" -fPIC "-I/usr/lib/perl/5.10/CORE"   Poppler.c
cc -c  -pthread -D_REENTRANT -I/usr/include/poppler/glib -I/usr/include/poppler -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/cairo -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gio-unix-2.0/ -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12   -D_REENTRANT -D_GNU_SOURCE -DDEBIAN -fno-strict-aliasing -pipe -fstack-protector -I/usr/local/include -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -O2 -g   -DVERSION=\"0.03\" -DXS_VERSION=\"0.03\" -fPIC "-I/usr/lib/perl/5.10/CORE"   Goo.c
cc: Goo.c: No such file or directory
cc: no input files
make: *** [Goo.o] Error 1[/INDENT]

In case it matters, in generating the make file during the initial install step, the output of perl Makefile.PL includes the following:

[INDENT]Unrecognized argument in LIBS ignored: '-pthread'[/INDENT]

The readme lists cairo, poppler and glib as dependencies. I have cairo, poppler and glib packages installed (and development packages).  I have install cairo and glib modules from CPAN.  I regularly use cairo and gtk from perl without problems.  

I am at a loss as to what this Goo.c error is.  Any ideas?  Is any more information needed?  Thanks

Search in Synaptic for "goo" and "libgoo".

/luigi

---

