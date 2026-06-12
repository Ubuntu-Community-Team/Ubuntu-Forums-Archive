---
title: "compile lapack++ code"
date: 2009-07-20
forum: General Help
---

### Post by vielmaj on 2009-07-20
I installed Lapack++ version 2.5.3 and everything installed just fine.  I get this message after I run make install.

Libraries have been installed in:
   /usr/local/lib

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.

Now I try to run a simple code like below, trying to include one of the libraries.

#include <gmc.h>

int main() {

   return 0;

}

and I get the following error

lapacktest.cpp:1:17: error: gmc.h: No such file or directory

Could someone help me out please?

Jason

---

