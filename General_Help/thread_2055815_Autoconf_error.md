---
title: "Autoconf error"
date: 2012-09-10
forum: General Help
---

### Post by Statia on 2012-09-10
I am trying to build libdivecomputer.
According to instructions on the Subsurface project page:

[http://subsurface.hohndel.org/building/](http://subsurface.hohndel.org/building/)

I run ```
autoreconf --install
```It gives these errors:

```
Can't exec "libtoolize": No such file or directory at /usr/bin/autoreconf2.50 line 196.
Use of uninitialized value in pattern match (m//) at /usr/bin/autoreconf2.50 line 196.
src/Makefile.am:4: Libtool library used but `LIBTOOL' is undefined
src/Makefile.am:4:   The usual way to define `LIBTOOL' is to add `LT_INIT'
src/Makefile.am:4:   to `configure.ac' and run `aclocal' and `autoconf' again.
src/Makefile.am:4:   If `LT_INIT' is in `configure.ac', make sure
src/Makefile.am:4:   its definition is in aclocal's search path.
autoreconf2.50: automake failed with exit status: 1
```I have autoconf installed and tried a second time with autoconf2.13, but same result.
Anyone an idea what's missing or what needs to be fixed?

---

### Post by Statia on 2012-09-10
Fixed it. Turns out libtool needed to be installed.

---

