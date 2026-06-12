---
title: "Updated: Now can't link to libboost"
date: 2011-02-25
forum: General Help
---

### Post by Lyuokdea on 2011-02-25
I updated a few months ago to 10.04, and now a program (which used to work) can't link to the libboost libraries anymore, I get:

```

/usr/bin/ld: cannot find -lboost_filesystem
collect2: ld returned 1 exit status

```

The error seems to come from acinclude.m4, where it has:

```

  BOOST_LIBS="-L$BOOST_HOME/lib -lboost_filesystem"
  AC_SUBST(BOOST_LIBS)
  AC_DEFINE([HAVE_BOOST], 1)

```

The libboost file systems do seem to exist in /usr/lib:

```

-rw-r--r-- 1 root root  83K 2010-04-01 21:05 libboost_filesystem.so.1.40.0
-rw-r--r-- 1 root root  47K 2009-03-26 19:28 libboost_iostreams-mt.so.1.37.0
-rw-r--r-- 1 root root 313K 2010-04-01 21:05 libboost_program_options.so.1.40.0
-rw-r--r-- 1 root root 970K 2010-04-01 21:05 libboost_regex.so.1.40.0
-rw-r--r-- 1 root root  15K 2010-04-01 21:05 libboost_system.so.1.40.0

```

I have tried adding some symbolic links in this directory to fix the problem, to no avail, I have tried removing the call to -lboost-filesystem in acinclude.m4 - but that just lead to different errors.

Any help would be appreciated,

Lyuokdea

---

