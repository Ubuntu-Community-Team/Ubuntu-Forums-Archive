---
title: "koffice installation from source"
date: 2006-05-23
forum: General Help
---

### Post by MBMESSAOUD on 2006-05-23
Hi 

I am triying to install koffice from source so I downloaded
koffice-1.5.0.tar.bz2 
during compilation I got this error

/bin/sh ../../../../libtool --silent --tag=CXX --mode=link g++  -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -O2 -Wformat-security -Wmissing-format-attribute -Wno-non-virtual-dtor -fno-exceptions -fno-check-new -fno-common -DQT_CLEAN_NAMESPACE -DQT_NO_ASCII_CAST -DQT_NO_STL -DQT_NO_COMPAT -DQT_NO_TRANSLATION -DHAVE_KNEWSTUFF    -o libhtmlimport.la -rpath /usr/lib/kde3 -L/usr/lib -L/usr/share/qt3/lib -L/usr/X11R6/lib    -module -avoid-version -no-undefined -Wl,--no-undefined -Wl,--allow-shlib-undefined htmlimport.lo khtmlreader.lo kwdwriter.lo -lkhtml ../../../../lib/kofficeui/libkofficeui.la ../../../../lib/kofficecore/libkofficecore.la ../../../../lib/store/libkstore.la ../../../../lib/kotext/libkotext.la
/usr/bin/ld: cannot find -lpcreposix
collect2: ld returned 1 exit status
make[5]: *** [libhtmlimport.la] Error 1
make[5]: Leaving directory `/home/mokhtar/tmp/koffice-1.5.0/filters/kword/html/import'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/mokhtar/tmp/koffice-1.5.0/filters/kword/html'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/mokhtar/tmp/koffice-1.5.0/filters/kword'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/mokhtar/tmp/koffice-1.5.0/filters'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/mokhtar/tmp/koffice-1.5.0'
make: *** [all] Error 2


I have /usr/lib/libpcreposix.so.3.11.0 installed by packages libpcre3

Have you any idea about to resolve this problem?

---

### Post by NoUse on 2006-05-23
Any reason you need to do it from source?

There are ubuntu apt repos at:
[http://kubuntu.org/announcements/koffice-15.php](http://kubuntu.org/announcements/koffice-15.php)

---

### Post by MBMESSAOUD on 2006-05-24
I need to run kexi with  kexi-mdb-driver
to display M$ Access MDB file

kexi-mdb-driver is not available at [http://packages.ubuntu.com/breezy/kde/kexi](http://packages.ubuntu.com/breezy/kde/kexi)

kexi-mdb-driver is available as source packages [http://www.kexi-project.org/wiki/wikiview/index.php?MDBDriver](http://www.kexi-project.org/wiki/wikiview/index.php?MDBDriver)

So I need o compile koffice to use kexi with MDB

---

### Post by NoUse on 2006-05-24
When you are compiling software you need to install the -dev package.  So install libpcre3-dev.

Also, this mdb driver is in the dapper repos by default so when that comes out you wont need to compile Koffice I don't think.

---

