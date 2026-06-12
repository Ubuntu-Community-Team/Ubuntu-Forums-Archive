---
title: "compiling clutter (to install gloobus preview in 10.11)"
date: 2011-10-25
forum: General Help
---

### Post by larryfroot on 2011-10-25
Hello froots.

Am having probs compiling clutter. The process spits out the warning:

> WARNING: aclocal's directory is /usr/share/aclocal, but...
         no file /usr/share/aclocal/glib-2.0.m4
         You may see fatal macro warnings below.
         If these files are installed in /some/dir, set the ACLOCAL_FLAGS 
         environment variable to "-I /some/dir", or install
         /usr/share/aclocal/glib-2.0.m4.

Sure enough it ends in:

> configure.ac:140: error: possibly undefined macro: AM_PATH_GLIB_2_0
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
configure.ac:142: error: possibly undefined macro: AC_MSG_ERROR
autoreconf: /usr/bin/autoconf failed with exit status: 1

If someone could please point me to the light I would be very grateful. Thanks!

---

