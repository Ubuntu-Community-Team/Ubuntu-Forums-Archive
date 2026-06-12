---
title: "Make error?"
date: 2006-02-24
forum: General Help
---

### Post by Nightmare JG on 2006-02-24
Whenever I try to complile anything, I get an error like this one:

```

make[2]: *** [libkxdocker.la] Error 1
make[2]: Leaving directory `/home/jacy/Desktop/kxdocker-1.0.0a/kxdocker-1.0.0a/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/jacy/Desktop/kxdocker-1.0.0a/kxdocker-1.0.0a'
make: *** [all] Error 2

```

Any help?

---

### Post by cyberb0b on 2006-02-24
Please copy and paste a few lines above what you posted.  The output you posted doesn't contain the actual error message.

---

### Post by Nightmare JG on 2006-02-24
Well, here's the whole thing:

```
jacy@ubuntu:~/Desktop/kxdocker-1.0.0a/kxdocker-1.0.0a$ make
make  all-recursive
make[1]: Entering directory `/home/jacy/Desktop/kxdocker-1.0.0a/kxdocker-1.0.0a'
Making all in doc
make[2]: Entering directory `/home/jacy/Desktop/kxdocker-1.0.0a/kxdocker-1.0.0a/doc'
Making all in .
make[3]: Entering directory `/home/jacy/Desktop/kxdocker-1.0.0a/kxdocker-1.0.0a/doc'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/jacy/Desktop/kxdocker-1.0.0a/kxdocker-1.0.0a/doc'
Making all in en
make[3]: Entering directory `/home/jacy/Desktop/kxdocker-1.0.0a/kxdocker-1.0.0a/doc/en'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/jacy/Desktop/kxdocker-1.0.0a/kxdocker-1.0.0a/doc/en'
make[2]: Leaving directory `/home/jacy/Desktop/kxdocker-1.0.0a/kxdocker-1.0.0a/doc'
Making all in po
make[2]: Entering directory `/home/jacy/Desktop/kxdocker-1.0.0a/kxdocker-1.0.0a/po'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/jacy/Desktop/kxdocker-1.0.0a/kxdocker-1.0.0a/po'
Making all in src
make[2]: Entering directory `/home/jacy/Desktop/kxdocker-1.0.0a/kxdocker-1.0.0a/src'
/bin/sh ../libtool --silent --mode=link --tag=CXX g++  -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -O2 -Wformat-security -Wmissing-format-attribute -Wno-non-virtual-dtor -fno-exceptions -fno-check-new -fno-common    -o libkxdocker.la -rpath /usr/lib -version-info 0:40:0 -R /usr/lib -R /usr/lib -R /usr/share/qt3/lib -R /usr/X11R6/lib -L/usr/lib -L/usr/share/qt3/lib -L/usr/X11R6/lib    xeconfiguration.lo xeobject.lo xeroot.lo xeworld.lo gpluginpainter.lo gpluginsdk.lo gpluginsdkcfgwnd.lo xeplugin_xmlconf.lo xgdocker.lo xgicon.lo xeplugin_guilogger.lo xematrix.lo xeplugin_gepillow.lo taskmanager.lo -lkdeui -lkio
grep: /lib/libacl.la: No such file or directory
/bin/sed: can't read /lib/libacl.la: No such file or directory
libtool: link: `/lib/libacl.la' is not a valid libtool archive
make[2]: *** [libkxdocker.la] Error 1
make[2]: Leaving directory `/home/jacy/Desktop/kxdocker-1.0.0a/kxdocker-1.0.0a/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/jacy/Desktop/kxdocker-1.0.0a/kxdocker-1.0.0a'
make: *** [all] Error 2

```

[EDIT: I fixed it! I just had to install libacl1-dev and libattr1-dev, then make worked great!]

---

