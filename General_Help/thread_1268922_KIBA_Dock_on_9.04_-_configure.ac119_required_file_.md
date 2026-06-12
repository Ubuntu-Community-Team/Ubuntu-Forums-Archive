---
title: "KIBA Dock on 9.04 - configure.ac:119: required file `DOC_MAKEFILES.in' not found"
date: 2009-09-17
forum: General Help
---

### Post by thepossiblehuman on 2009-09-17
So I'm trying to install the Kiba dock, and when I run:

```
 ./autogen.sh 
```

It eventually bails out telling me:

```
autoreconf: running: /usr/bin/autoheader
autoreconf: running: automake --add-missing --copy --no-force
Makefile.am:8: ENABLE_GTK_DOC does not appear in AM_CONDITIONAL
configure.ac:119: required file `DOC_MAKEFILES.in' not found
autoreconf: automake failed with exit status: 1 
```

Not exactly sure where to go from here.  I've installed Kiba on 9.04 before, and while I've run into problems, I never ran into this problem.  This is what is in the configure.ac file at line 119:

```
 AC_CONFIG_FILES([kiba-dock.pc
           Makefile
           src/Makefile
           include/Makefile
           kiba-settings/Makefile
           icons/Makefile
           files/populate-dock.sh
           files/Makefile
           $DOC_MAKEFILES
           po/Makefile.in])

```

Any and all help is appreciated.  Thanks.

---

### Post by thepossiblehuman on 2009-09-17
This must have been introduced recently.  I decided to check out the svn repo's from August 1st, and I was able to install KIBA fine.

---

