---
title: "Problem installing libgpod/gtkpod from CVS"
date: 2006-06-08
forum: General Help
---

### Post by -Leo- on 2006-06-08
Hello

I've been having problems installing libgpod, and subsequently, gtkpod from CVS.  I was able to get both packages, and the './autogen.sh' seemed to go fine, but where I run into the major problem is after I type 'make'.  I wasn't entirely sure what to copy from my terminal, so I copied the last part of the configure command, and the entire results from saying 'make'.  (Sorry if I pasted far too much)  
```

Configuration for libgpod 0.3.3 :
--------------------------------

 Host System Type .....: i686-pc-linux-gnu
 Install path .........: /usr/local
 Preprocessor .........: gcc
 Compiler .............: gcc    -Wall   -Wchar-subscripts -Wmissing-declarations  -Wmissing-prototypes   -Wnested-externs -Wpointer-arith        -Wcast-align -Ws ign-compare     -Werror -std=c89        -g -O2 -Wno-strict-aliasing -Wno-sign-co mpare -Wdeclaration-after-statement
 Linker ...............: gcc
 ArtworkDB support ....: no
 Python bindings ......: no

 Now type 'make' to build libgpod 0.3.3,
 and then 'make install' for installation.

Now type `make' to compile libgpod
leo@leo-desktop:~/libgpod$ make
make  all-recursive
make[1]: Entering directory `/home/leo/libgpod'
Making all in src
make[2]: Entering directory `/home/leo/libgpod/src'
if /bin/sh ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. - I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall     -Wall    -Wchar-s ubscripts -Wmissing-declarations -Wmissing-prototypes   -Wnested-externs -Wpoint er-arith        -Wcast-align -Wsign-compare     -Werror -std=c89        -g -O2 - Wno-strict-aliasing -Wno-sign-compare -Wdeclaration-after-statement -MT itdb_art work.lo -MD -MP -MF ".deps/itdb_artwork.Tpo" -c -o itdb_artwork.lo itdb_artwork. c; \
        then mv -f ".deps/itdb_artwork.Tpo" ".deps/itdb_artwork.Plo"; else rm -f  ".deps/itdb_artwork.Tpo"; exit 1; fi
mkdir .libs
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/in clude -Wall -Wall -Wchar-subscripts -Wmissing-declarations -Wmissing-prototypes -Wnested-externs -Wpointer-arith -Wcast-align -Wsign-compare -Werror -std=c89 -g  -O2 -Wno-strict-aliasing -Wno-sign-compare -Wdeclaration-after-statement -MT it db_artwork.lo -MD -MP -MF .deps/itdb_artwork.Tpo -c itdb_artwork.c  -fPIC -DPIC -o .libs/itdb_artwork.o
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/in clude -Wall -Wall -Wchar-subscripts -Wmissing-declarations -Wmissing-prototypes -Wnested-externs -Wpointer-arith -Wcast-align -Wsign-compare -Werror -std=c89 -g  -O2 -Wno-strict-aliasing -Wno-sign-compare -Wdeclaration-after-statement -MT it db_artwork.lo -MD -MP -MF .deps/itdb_artwork.Tpo -c itdb_artwork.c -o itdb_artwo rk.o >/dev/null 2>&1
if /bin/sh ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. - I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall     -Wall    -Wchar-s ubscripts -Wmissing-declarations -Wmissing-prototypes   -Wnested-externs -Wpoint er-arith        -Wcast-align -Wsign-compare     -Werror -std=c89        -g -O2 - Wno-strict-aliasing -Wno-sign-compare -Wdeclaration-after-statement -MT itdb_itu nesdb.lo -MD -MP -MF ".deps/itdb_itunesdb.Tpo" -c -o itdb_itunesdb.lo itdb_itune sdb.c; \
        then mv -f ".deps/itdb_itunesdb.Tpo" ".deps/itdb_itunesdb.Plo"; else rm -f ".deps/itdb_itunesdb.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/in clude -Wall -Wall -Wchar-subscripts -Wmissing-declarations -Wmissing-prototypes -Wnested-externs -Wpointer-arith -Wcast-align -Wsign-compare -Werror -std=c89 -g  -O2 -Wno-strict-aliasing -Wno-sign-compare -Wdeclaration-after-statement -MT it db_itunesdb.lo -MD -MP -MF .deps/itdb_itunesdb.Tpo -c itdb_itunesdb.c  -fPIC -DP IC -o .libs/itdb_itunesdb.o
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/in clude -Wall -Wall -Wchar-subscripts -Wmissing-declarations -Wmissing-prototypes -Wnested-externs -Wpointer-arith -Wcast-align -Wsign-compare -Werror -std=c89 -g  -O2 -Wno-strict-aliasing -Wno-sign-compare -Wdeclaration-after-statement -MT it db_itunesdb.lo -MD -MP -MF .deps/itdb_itunesdb.Tpo -c itdb_itunesdb.c -o itdb_it unesdb.o >/dev/null 2>&1
if /bin/sh ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. - I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall     -Wall    -Wchar-s ubscripts -Wmissing-declarations -Wmissing-prototypes   -Wnested-externs -Wpoint er-arith        -Wcast-align -Wsign-compare     -Werror -std=c89        -g -O2 - Wno-strict-aliasing -Wno-sign-compare -Wdeclaration-after-statement -MT itdb_pla ylist.lo -MD -MP -MF ".deps/itdb_playlist.Tpo" -c -o itdb_playlist.lo itdb_playl ist.c; \
        then mv -f ".deps/itdb_playlist.Tpo" ".deps/itdb_playlist.Plo"; else rm -f ".deps/itdb_playlist.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/in clude -Wall -Wall -Wchar-subscripts -Wmissing-declarations -Wmissing-prototypes -Wnested-externs -Wpointer-arith -Wcast-align -Wsign-compare -Werror -std=c89 -g  -O2 -Wno-strict-aliasing -Wno-sign-compare -Wdeclaration-after-statement -MT it db_playlist.lo -MD -MP -MF .deps/itdb_playlist.Tpo -c itdb_playlist.c  -fPIC -DP IC -o .libs/itdb_playlist.o
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/in clude -Wall -Wall -Wchar-subscripts -Wmissing-declarations -Wmissing-prototypes -Wnested-externs -Wpointer-arith -Wcast-align -Wsign-compare -Werror -std=c89 -g  -O2 -Wno-strict-aliasing -Wno-sign-compare -Wdeclaration-after-statement -MT it db_playlist.lo -MD -MP -MF .deps/itdb_playlist.Tpo -c itdb_playlist.c -o itdb_pl aylist.o >/dev/null 2>&1
if /bin/sh ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. - I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall     -Wall    -Wchar-s ubscripts -Wmissing-declarations -Wmissing-prototypes   -Wnested-externs -Wpoint er-arith        -Wcast-align -Wsign-compare     -Werror -std=c89        -g -O2 - Wno-strict-aliasing -Wno-sign-compare -Wdeclaration-after-statement -MT itdb_pho toalbum.lo -MD -MP -MF ".deps/itdb_photoalbum.Tpo" -c -o itdb_photoalbum.lo itdb _photoalbum.c; \
        then mv -f ".deps/itdb_photoalbum.Tpo" ".deps/itdb_photoalbum.Plo"; else  rm -f ".deps/itdb_photoalbum.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/in clude -Wall -Wall -Wchar-subscripts -Wmissing-declarations -Wmissing-prototypes -Wnested-externs -Wpointer-arith -Wcast-align -Wsign-compare -Werror -std=c89 -g  -O2 -Wno-strict-aliasing -Wno-sign-compare -Wdeclaration-after-statement -MT it db_photoalbum.lo -MD -MP -MF .deps/itdb_photoalbum.Tpo -c itdb_photoalbum.c  -fP IC -DPIC -o .libs/itdb_photoalbum.o
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/in clude -Wall -Wall -Wchar-subscripts -Wmissing-declarations -Wmissing-prototypes -Wnested-externs -Wpointer-arith -Wcast-align -Wsign-compare -Werror -std=c89 -g  -O2 -Wno-strict-aliasing -Wno-sign-compare -Wdeclaration-after-statement -MT it db_photoalbum.lo -MD -MP -MF .deps/itdb_photoalbum.Tpo -c itdb_photoalbum.c -o i tdb_photoalbum.o >/dev/null 2>&1
if /bin/sh ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. - I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall     -Wall    -Wchar-s ubscripts -Wmissing-declarations -Wmissing-prototypes   -Wnested-externs -Wpoint er-arith        -Wcast-align -Wsign-compare     -Werror -std=c89        -g -O2 - Wno-strict-aliasing -Wno-sign-compare -Wdeclaration-after-statement -MT itdb_tra ck.lo -MD -MP -MF ".deps/itdb_track.Tpo" -c -o itdb_track.lo itdb_track.c; \
        then mv -f ".deps/itdb_track.Tpo" ".deps/itdb_track.Plo"; else rm -f ".d eps/itdb_track.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/in clude -Wall -Wall -Wchar-subscripts -Wmissing-declarations -Wmissing-prototypes -Wnested-externs -Wpointer-arith -Wcast-align -Wsign-compare -Werror -std=c89 -g  -O2 -Wno-strict-aliasing -Wno-sign-compare -Wdeclaration-after-statement -MT it db_track.lo -MD -MP -MF .deps/itdb_track.Tpo -c itdb_track.c  -fPIC -DPIC -o .li bs/itdb_track.o
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/in clude -Wall -Wall -Wchar-subscripts -Wmissing-declarations -Wmissing-prototypes -Wnested-externs -Wpointer-arith -Wcast-align -Wsign-compare -Werror -std=c89 -g  -O2 -Wno-strict-aliasing -Wno-sign-compare -Wdeclaration-after-statement -MT it db_track.lo -MD -MP -MF .deps/itdb_track.Tpo -c itdb_track.c -o itdb_track.o >/d ev/null 2>&1
if /bin/sh ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. - I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall     -Wall    -Wchar-s ubscripts -Wmissing-declarations -Wmissing-prototypes   -Wnested-externs -Wpoint er-arith        -Wcast-align -Wsign-compare     -Werror -std=c89        -g -O2 - Wno-strict-aliasing -Wno-sign-compare -Wdeclaration-after-statement -MT db-artwo rk-parser.lo -MD -MP -MF ".deps/db-artwork-parser.Tpo" -c -o db-artwork-parser.l o db-artwork-parser.c; \
        then mv -f ".deps/db-artwork-parser.Tpo" ".deps/db-artwork-parser.Plo"; else rm -f ".deps/db-artwork-parser.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/in clude -Wall -Wall -Wchar-subscripts -Wmissing-declarations -Wmissing-prototypes -Wnested-externs -Wpointer-arith -Wcast-align -Wsign-compare -Werror -std=c89 -g  -O2 -Wno-strict-aliasing -Wno-sign-compare -Wdeclaration-after-statement -MT db -artwork-parser.lo -MD -MP -MF .deps/db-artwork-parser.Tpo -c db-artwork-parser. c  -fPIC -DPIC -o .libs/db-artwork-parser.o
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/in clude -Wall -Wall -Wchar-subscripts -Wmissing-declarations -Wmissing-prototypes -Wnested-externs -Wpointer-arith -Wcast-align -Wsign-compare -Werror -std=c89 -g  -O2 -Wno-strict-aliasing -Wno-sign-compare -Wdeclaration-after-statement -MT db -artwork-parser.lo -MD -MP -MF .deps/db-artwork-parser.Tpo -c db-artwork-parser. c -o db-artwork-parser.o >/dev/null 2>&1
if /bin/sh ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. - I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall     -Wall    -Wchar-s ubscripts -Wmissing-declarations -Wmissing-prototypes   -Wnested-externs -Wpoint er-arith        -Wcast-align -Wsign-compare     -Werror -std=c89        -g -O2 - Wno-strict-aliasing -Wno-sign-compare -Wdeclaration-after-statement -MT db-parse -context.lo -MD -MP -MF ".deps/db-parse-context.Tpo" -c -o db-parse-context.lo d b-parse-context.c; \
        then mv -f ".deps/db-parse-context.Tpo" ".deps/db-parse-context.Plo"; el se rm -f ".deps/db-parse-context.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/in clude -Wall -Wall -Wchar-subscripts -Wmissing-declarations -Wmissing-prototypes -Wnested-externs -Wpointer-arith -Wcast-align -Wsign-compare -Werror -std=c89 -g  -O2 -Wno-strict-aliasing -Wno-sign-compare -Wdeclaration-after-statement -MT db -parse-context.lo -MD -MP -MF .deps/db-parse-context.Tpo -c db-parse-context.c -fPIC -DPIC -o .libs/db-parse-context.o
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/in clude -Wall -Wall -Wchar-subscripts -Wmissing-declarations -Wmissing-prototypes -Wnested-externs -Wpointer-arith -Wcast-align -Wsign-compare -Werror -std=c89 -g  -O2 -Wno-strict-aliasing -Wno-sign-compare -Wdeclaration-after-statement -MT db -parse-context.lo -MD -MP -MF .deps/db-parse-context.Tpo -c db-parse-context.c - o db-parse-context.o >/dev/null 2>&1
if /bin/sh ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. - I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall     -Wall    -Wchar-s ubscripts -Wmissing-declarations -Wmissing-prototypes   -Wnested-externs -Wpoint er-arith        -Wcast-align -Wsign-compare     -Werror -std=c89        -g -O2 - Wno-strict-aliasing -Wno-sign-compare -Wdeclaration-after-statement -MT db-artwo rk-debug.lo -MD -MP -MF ".deps/db-artwork-debug.Tpo" -c -o db-artwork-debug.lo d b-artwork-debug.c; \
        then mv -f ".deps/db-artwork-debug.Tpo" ".deps/db-artwork-debug.Plo"; el se rm -f ".deps/db-artwork-debug.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/in clude -Wall -Wall -Wchar-subscripts -Wmissing-declarations -Wmissing-prototypes -Wnested-externs -Wpointer-arith -Wcast-align -Wsign-compare -Werror -std=c89 -g  -O2 -Wno-strict-aliasing -Wno-sign-compare -Wdeclaration-after-statement -MT db -artwork-debug.lo -MD -MP -MF .deps/db-artwork-debug.Tpo -c db-artwork-debug.c -fPIC -DPIC -o .libs/db-artwork-debug.o
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/in clude -Wall -Wall -Wchar-subscripts -Wmissing-declarations -Wmissing-prototypes -Wnested-externs -Wpointer-arith -Wcast-align -Wsign-compare -Werror -std=c89 -g  -O2 -Wno-strict-aliasing -Wno-sign-compare -Wdeclaration-after-statement -MT db -artwork-debug.lo -MD -MP -MF .deps/db-artwork-debug.Tpo -c db-artwork-debug.c - o db-artwork-debug.o >/dev/null 2>&1
if /bin/sh ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. - I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall     -Wall    -Wchar-s ubscripts -Wmissing-declarations -Wmissing-prototypes   -Wnested-externs -Wpoint er-arith        -Wcast-align -Wsign-compare     -Werror -std=c89        -g -O2 - Wno-strict-aliasing -Wno-sign-compare -Wdeclaration-after-statement -MT db-image -parser.lo -MD -MP -MF ".deps/db-image-parser.Tpo" -c -o db-image-parser.lo db-i mage-parser.c; \
        then mv -f ".deps/db-image-parser.Tpo" ".deps/db-image-parser.Plo"; else  rm -f ".deps/db-image-parser.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/in clude -Wall -Wall -Wchar-subscripts -Wmissing-declarations -Wmissing-prototypes -Wnested-externs -Wpointer-arith -Wcast-align -Wsign-compare -Werror -std=c89 -g  -O2 -Wno-strict-aliasing -Wno-sign-compare -Wdeclaration-after-statement -MT db -image-parser.lo -MD -MP -MF .deps/db-image-parser.Tpo -c db-image-parser.c  -fP IC -DPIC -o .libs/db-image-parser.o
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/in clude -Wall -Wall -Wchar-subscripts -Wmissing-declarations -Wmissing-prototypes -Wnested-externs -Wpointer-arith -Wcast-align -Wsign-compare -Werror -std=c89 -g  -O2 -Wno-strict-aliasing -Wno-sign-compare -Wdeclaration-after-statement -MT db -image-parser.lo -MD -MP -MF .deps/db-image-parser.Tpo -c db-image-parser.c -o d b-image-parser.o >/dev/null 2>&1
if /bin/sh ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. - I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall     -Wall    -Wchar-s ubscripts -Wmissing-declarations -Wmissing-prototypes   -Wnested-externs -Wpoint er-arith        -Wcast-align -Wsign-compare     -Werror -std=c89        -g -O2 - Wno-strict-aliasing -Wno-sign-compare -Wdeclaration-after-statement -MT db-artwo rk-writer.lo -MD -MP -MF ".deps/db-artwork-writer.Tpo" -c -o db-artwork-writer.l o db-artwork-writer.c; \
        then mv -f ".deps/db-artwork-writer.Tpo" ".deps/db-artwork-writer.Plo"; else rm -f ".deps/db-artwork-writer.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/in clude -Wall -Wall -Wchar-subscripts -Wmissing-declarations -Wmissing-prototypes -Wnested-externs -Wpointer-arith -Wcast-align -Wsign-compare -Werror -std=c89 -g  -O2 -Wno-strict-aliasing -Wno-sign-compare -Wdeclaration-after-statement -MT db -artwork-writer.lo -MD -MP -MF .deps/db-artwork-writer.Tpo -c db-artwork-writer. c  -fPIC -DPIC -o .libs/db-artwork-writer.o
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/in clude -Wall -Wall -Wchar-subscripts -Wmissing-declarations -Wmissing-prototypes -Wnested-externs -Wpointer-arith -Wcast-align -Wsign-compare -Werror -std=c89 -g  -O2 -Wno-strict-aliasing -Wno-sign-compare -Wdeclaration-after-statement -MT db -artwork-writer.lo -MD -MP -MF .deps/db-artwork-writer.Tpo -c db-artwork-writer. c -o db-artwork-writer.o >/dev/null 2>&1
if /bin/sh ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. - I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall     -Wall    -Wchar-s ubscripts -Wmissing-declarations -Wmissing-prototypes   -Wnested-externs -Wpoint er-arith        -Wcast-align -Wsign-compare     -Werror -std=c89        -g -O2 - Wno-strict-aliasing -Wno-sign-compare -Wdeclaration-after-statement -MT ithumb-w riter.lo -MD -MP -MF ".deps/ithumb-writer.Tpo" -c -o ithumb-writer.lo ithumb-wri ter.c; \
        then mv -f ".deps/ithumb-writer.Tpo" ".deps/ithumb-writer.Plo"; else rm -f ".deps/ithumb-writer.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/in clude -Wall -Wall -Wchar-subscripts -Wmissing-declarations -Wmissing-prototypes -Wnested-externs -Wpointer-arith -Wcast-align -Wsign-compare -Werror -std=c89 -g  -O2 -Wno-strict-aliasing -Wno-sign-compare -Wdeclaration-after-statement -MT it humb-writer.lo -MD -MP -MF .deps/ithumb-writer.Tpo -c ithumb-writer.c  -fPIC -DP IC -o .libs/ithumb-writer.o
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/in clude -Wall -Wall -Wchar-subscripts -Wmissing-declarations -Wmissing-prototypes -Wnested-externs -Wpointer-arith -Wcast-align -Wsign-compare -Werror -std=c89 -g  -O2 -Wno-strict-aliasing -Wno-sign-compare -Wdeclaration-after-statement -MT it humb-writer.lo -MD -MP -MF .deps/ithumb-writer.Tpo -c ithumb-writer.c -o ithumb- writer.o >/dev/null 2>&1
if /bin/sh ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. - I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall     -Wall    -Wchar-s ubscripts -Wmissing-declarations -Wmissing-prototypes   -Wnested-externs -Wpoint er-arith        -Wcast-align -Wsign-compare     -Werror -std=c89        -g -O2 - Wno-strict-aliasing -Wno-sign-compare -Wdeclaration-after-statement -MT itdb_dev ice.lo -MD -MP -MF ".deps/itdb_device.Tpo" -c -o itdb_device.lo itdb_device.c; \
        then mv -f ".deps/itdb_device.Tpo" ".deps/itdb_device.Plo"; else rm -f " .deps/itdb_device.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/in clude -Wall -Wall -Wchar-subscripts -Wmissing-declarations -Wmissing-prototypes -Wnested-externs -Wpointer-arith -Wcast-align -Wsign-compare -Werror -std=c89 -g  -O2 -Wno-strict-aliasing -Wno-sign-compare -Wdeclaration-after-statement -MT it db_device.lo -MD -MP -MF .deps/itdb_device.Tpo -c itdb_device.c  -fPIC -DPIC -o .libs/itdb_device.o
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/in clude -Wall -Wall -Wchar-subscripts -Wmissing-declarations -Wmissing-prototypes -Wnested-externs -Wpointer-arith -Wcast-align -Wsign-compare -Werror -std=c89 -g  -O2 -Wno-strict-aliasing -Wno-sign-compare -Wdeclaration-after-statement -MT it db_device.lo -MD -MP -MF .deps/itdb_device.Tpo -c itdb_device.c -o itdb_device.o  >/dev/null 2>&1
/bin/sh ../libtool --tag=CC --mode=link gcc  -Wall      -Wchar-subscripts -Wmiss ing-declarations -Wmissing-prototypes   -Wnested-externs -Wpointer-arith       - Wcast-align -Wsign-compare      -Werror -std=c89        -g -O2 -Wno-strict-alias ing -Wno-sign-compare -Wdeclaration-after-statement   -o libgpod.la -rpath /usr/ local/lib -version-info 303:0:303 -no-undefined itdb_artwork.lo itdb_itunesdb.lo  itdb_playlist.lo itdb_photoalbum.lo itdb_track.lo db-artwork-parser.lo db-parse -context.lo db-artwork-debug.lo db-image-parser.lo db-artwork-writer.lo ithumb-w riter.lo itdb_device.lo  -lgobject-2.0 -lglib-2.0
gcc -shared  .libs/itdb_artwork.o .libs/itdb_itunesdb.o .libs/itdb_playlist.o .l ibs/itdb_photoalbum.o .libs/itdb_track.o .libs/db-artwork-parser.o .libs/db-pars e-context.o .libs/db-artwork-debug.o .libs/db-image-parser.o .libs/db-artwork-wr iter.o .libs/ithumb-writer.o .libs/itdb_device.o  /usr/lib/libgobject-2.0.so /us r/lib/libglib-2.0.so  -Wl,-soname -Wl,libgpod.so.0 -o .libs/libgpod.so.0.303.0
(cd .libs && rm -f libgpod.so.0 && ln -s libgpod.so.0.303.0 libgpod.so.0)
(cd .libs && rm -f libgpod.so && ln -s libgpod.so.0.303.0 libgpod.so)
ar cru .libs/libgpod.a  itdb_artwork.o itdb_itunesdb.o itdb_playlist.o itdb_phot oalbum.o itdb_track.o db-artwork-parser.o db-parse-context.o db-artwork-debug.o db-image-parser.o db-artwork-writer.o ithumb-writer.o itdb_device.o
ranlib .libs/libgpod.a
creating libgpod.la
(cd .libs && rm -f libgpod.la && ln -s ../libgpod.la libgpod.la)
make[2]: Leaving directory `/home/leo/libgpod/src'
Making all in bindings
make[2]: Entering directory `/home/leo/libgpod/bindings'
Making all in python
make[3]: Entering directory `/home/leo/libgpod/bindings/python'
Making all in examples
make[4]: Entering directory `/home/leo/libgpod/bindings/python/examples'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/leo/libgpod/bindings/python/examples'
make[4]: Entering directory `/home/leo/libgpod/bindings/python'
make[4]: Nothing to be done for `all-am'.
make[4]: Leaving directory `/home/leo/libgpod/bindings/python'
make[3]: Leaving directory `/home/leo/libgpod/bindings/python'
make[3]: Entering directory `/home/leo/libgpod/bindings'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/leo/libgpod/bindings'
make[2]: Leaving directory `/home/leo/libgpod/bindings'
Making all in tests
make[2]: Entering directory `/home/leo/libgpod/tests'
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/ include   -Wall  -I../src -DPACKAGE_LOCALE_DIR=\""/usr/local/share/locale"\" -Wall   -Wchar-subscripts -Wmissing-declarations -Wmissing-prototypes   -Wnested -externs -Wpointer-arith        -Wcast-align -Wsign-compare     -Werror -std=c89         -g -O2 -Wno-strict-aliasing -Wno-sign-compare -Wdeclaration-after-statem ent -MT itdb_main.o -MD -MP -MF ".deps/itdb_main.Tpo" -c -o itdb_main.o itdb_mai n.c; \
        then mv -f ".deps/itdb_main.Tpo" ".deps/itdb_main.Po"; else rm -f ".deps /itdb_main.Tpo"; exit 1; fi
/bin/sh ../libtool --tag=CC --mode=link gcc  -Wall      -Wchar-subscripts -Wmiss ing-declarations -Wmissing-prototypes   -Wnested-externs -Wpointer-arith       - Wcast-align -Wsign-compare      -Werror -std=c89        -g -O2 -Wno-strict-alias ing -Wno-sign-compare -Wdeclaration-after-statement   -o test-itdb  itdb_main.o  -lgobject-2.0 -lglib-2.0    ../src/libgpod.la
mkdir .libs
gcc -Wall -Wchar-subscripts -Wmissing-declarations -Wmissing-prototypes -Wnested -externs -Wpointer-arith -Wcast-align -Wsign-compare -Werror -std=c89 -g -O2 -Wn o-strict-aliasing -Wno-sign-compare -Wdeclaration-after-statement -o .libs/test- itdb itdb_main.o  /usr/lib/libgobject-2.0.so /usr/lib/libglib-2.0.so ../src/.lib s/libgpod.so -Wl,--rpath -Wl,/usr/local/lib
creating test-itdb
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/ include   -Wall  -I../src -DPACKAGE_LOCALE_DIR=\""/usr/local/share/locale"\" -Wall   -Wchar-subscripts -Wmissing-declarations -Wmissing-prototypes   -Wnested -externs -Wpointer-arith        -Wcast-align -Wsign-compare     -Werror -std=c89         -g -O2 -Wno-strict-aliasing -Wno-sign-compare -Wdeclaration-after-statem ent -MT test-ls.o -MD -MP -MF ".deps/test-ls.Tpo" -c -o test-ls.o test-ls.c; \
        then mv -f ".deps/test-ls.Tpo" ".deps/test-ls.Po"; else rm -f ".deps/tes t-ls.Tpo"; exit 1; fi
/bin/sh ../libtool --tag=CC --mode=link gcc  -Wall      -Wchar-subscripts -Wmiss ing-declarations -Wmissing-prototypes   -Wnested-externs -Wpointer-arith       - Wcast-align -Wsign-compare      -Werror -std=c89        -g -O2 -Wno-strict-alias ing -Wno-sign-compare -Wdeclaration-after-statement   -o test-ls  test-ls.o  -lg object-2.0 -lglib-2.0    ../src/libgpod.la
gcc -Wall -Wchar-subscripts -Wmissing-declarations -Wmissing-prototypes -Wnested -externs -Wpointer-arith -Wcast-align -Wsign-compare -Werror -std=c89 -g -O2 -Wn o-strict-aliasing -Wno-sign-compare -Wdeclaration-after-statement -o .libs/test- ls test-ls.o  /usr/lib/libgobject-2.0.so /usr/lib/libglib-2.0.so ../src/.libs/li bgpod.so -Wl,--rpath -Wl,/usr/local/lib
creating test-ls
/bin/sh ../libtool --tag=CC --mode=link gcc  -Wall      -Wchar-subscripts -Wmiss ing-declarations -Wmissing-prototypes   -Wnested-externs -Wpointer-arith       - Wcast-align -Wsign-compare      -Werror -std=c89        -g -O2 -Wno-strict-alias ing -Wno-sign-compare -Wdeclaration-after-statement   -o test-init-ipod    -lgob ject-2.0 -lglib-2.0    ../src/libgpod.la
gcc -Wall -Wchar-subscripts -Wmissing-declarations -Wmissing-prototypes -Wnested -externs -Wpointer-arith -Wcast-align -Wsign-compare -Werror -std=c89 -g -O2 -Wn o-strict-aliasing -Wno-sign-compare -Wdeclaration-after-statement -o .libs/test- init-ipod  /usr/lib/libgobject-2.0.so /usr/lib/libglib-2.0.so ../src/.libs/libgp od.so -Wl,--rpath -Wl,/usr/local/lib
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/crt1.o: In function `_start':. ./sysdeps/i386/elf/start.S:115: undefined reference to `main'
collect2: ld returned 1 exit status
make[2]: *** [test-init-ipod] Error 1
make[2]: Leaving directory `/home/leo/libgpod/tests'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/leo/libgpod'
make: *** [all] Error 2
leo@leo-desktop:~/libgpod$

```

Now, I'm stumped.  I searched, and read various places.  I tried a few things that I could think of with my limited linux-knowledge.  Please help me. ](*,) 

Thanks in advance.

---

### Post by -Leo- on 2006-06-08
*Bump*  Still hoping someone can help me in finding a solution. :-k

---

### Post by sportman1280 on 2006-08-12
same issue here. any help?

---

### Post by camelreef on 2006-09-24
yup, same thing here...

I am trying to get the latest CVS version of libgpod in an attempt to recover the cover art functionnality of Amarok on a Gen 2 iPod Nano.

Nico

---

### Post by DNAspark99 on 2006-09-27
> **camelreef said:**
> yup, same thing here...

I am trying to get the latest CVS version of libgpod in an attempt to recover the cover art functionnality of Amarok on a Gen 2 iPod Nano.

Nico

ditto - current libgpod/amarok locks the ArtworkDB file, and bloats it to 17MB, album art doesn't show up... have to shutdown amarok to allow unmounting/ejecting of ipod

---

### Post by oestrogen on 2006-11-12
Try installing g77. It worked for me.

---

