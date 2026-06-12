---
title: "maitreya - source code compilation help"
date: 2010-03-21
forum: General Help
---

### Post by anksush on 2010-03-21
Hi,

I am trying to install [Maitreya software]("http://www.saravali.de/developer/installation.html") and the instructions are not so clear..anyway when I give sh .configure it compiled but make gave error and make install also gave error..

<CODE>
make  all-recursive
make[1]: Entering directory `/home/sush/Downloads/maitreya/maitreya6/trunk'
Making all in po
make[2]: Entering directory `/home/sush/Downloads/maitreya/maitreya6/trunk/po'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/sush/Downloads/maitreya/maitreya6/trunk/po'
Making all in src
make[2]: Entering directory `/home/sush/Downloads/maitreya/maitreya6/trunk/src'
Making all in swe
make[3]: Entering directory `/home/sush/Downloads/maitreya/maitreya6/trunk/src/swe'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/sush/Downloads/maitreya/maitreya6/trunk/src/swe'
Making all in base
make[3]: Entering directory `/home/sush/Downloads/maitreya/maitreya6/trunk/src/base'
source='Calculator.cpp' object='Calculator.o' libtool=no \
    DEPDIR=.deps depmode=none /bin/bash ../../depcomp \
    g++ -DHAVE_CONFIG_H -I. -I../.. -I. -I../swe -I../pics -I/usr/lib/wx/include/gtk2-unicode-release-2.8 -I/usr/include/wx-2.8 -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES -D__WXGTK__ -Wall -DSTRICT -Wno-write-strings    -c -o Calculator.o Calculator.cpp
../../depcomp: line 611: exec: g++: not found
make[3]: *** [Calculator.o] Error 127
make[3]: Leaving directory `/home/sush/Downloads/maitreya/maitreya6/trunk/src/base'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/sush/Downloads/maitreya/maitreya6/trunk/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/sush/Downloads/maitreya/maitreya6/trunk'
make: *** [all] Error 2
sush@ankit-laptop:~/Downloads/maitreya/maitreya6/trunk$ make install
Making install in po
make[1]: Entering directory `/home/sush/Downloads/maitreya/maitreya6/trunk/po'
/bin/mkdir -p /usr/local/share
/bin/mkdir: cannot create directory `/usr/local/share/locale': Permission denied
/usr/bin/install: cannot create regular file `/usr/local/share/locale/de/LC_MESSAGES/maitreya6.mo': No such file or directory
installing de.gmo as /usr/local/share/locale/de/LC_MESSAGES/maitreya6.mo
/bin/mkdir: cannot create directory `/usr/local/share/locale': Permission denied
/usr/bin/install: cannot create regular file `/usr/local/share/locale/ru/LC_MESSAGES/maitreya6.mo': No such file or directory
installing ru.gmo as /usr/local/share/locale/ru/LC_MESSAGES/maitreya6.mo
/bin/mkdir: cannot create directory `/usr/local/share/locale': Permission denied
/usr/bin/install: cannot create regular file `/usr/local/share/locale/te/LC_MESSAGES/maitreya6.mo': No such file or directory
installing te.gmo as /usr/local/share/locale/te/LC_MESSAGES/maitreya6.mo
/bin/mkdir: cannot create directory `/usr/local/share/locale': Permission denied
/usr/bin/install: cannot create regular file `/usr/local/share/locale/pl/LC_MESSAGES/maitreya6.mo': No such file or directory
installing pl.gmo as /usr/local/share/locale/pl/LC_MESSAGES/maitreya6.mo
/bin/mkdir: cannot create directory `/usr/local/share/locale': Permission denied
/usr/bin/install: cannot create regular file `/usr/local/share/locale/it/LC_MESSAGES/maitreya6.mo': No such file or directory
installing it.gmo as /usr/local/share/locale/it/LC_MESSAGES/maitreya6.mo
/bin/mkdir: cannot create directory `/usr/local/share/locale': Permission denied
/usr/bin/install: cannot create regular file `/usr/local/share/locale/hu/LC_MESSAGES/maitreya6.mo': No such file or directory
installing hu.gmo as /usr/local/share/locale/hu/LC_MESSAGES/maitreya6.mo
if test "maitreya6" = "gettext-tools"; then \
      /bin/mkdir -p /usr/local/share/gettext/po; \
      for file in Makefile.in.in remove-potcdate.sin quot.sed boldquot.sed [email]en@quot.header[/email] [email]en@boldquot.header[/email] insert-header.sin Rules-quot   Makevars.template; do \
        /usr/bin/install -c -m 644 ./$file \
                /usr/local/share/gettext/po/$file; \
      done; \
      for file in Makevars; do \
        rm -f /usr/local/share/gettext/po/$file; \
      done; \
    else \
      : ; \
    fi
make[1]: Leaving directory `/home/sush/Downloads/maitreya/maitreya6/trunk/po'
Making install in src
make[1]: Entering directory `/home/sush/Downloads/maitreya/maitreya6/trunk/src'
Making install in swe
make[2]: Entering directory `/home/sush/Downloads/maitreya/maitreya6/trunk/src/swe'
make[3]: Entering directory `/home/sush/Downloads/maitreya/maitreya6/trunk/src/swe'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/sush/Downloads/maitreya/maitreya6/trunk/src/swe'
make[2]: Leaving directory `/home/sush/Downloads/maitreya/maitreya6/trunk/src/swe'
Making install in base
make[2]: Entering directory `/home/sush/Downloads/maitreya/maitreya6/trunk/src/base'
source='Calculator.cpp' object='Calculator.o' libtool=no \
    DEPDIR=.deps depmode=none /bin/bash ../../depcomp \
    g++ -DHAVE_CONFIG_H -I. -I../.. -I. -I../swe -I../pics -I/usr/lib/wx/include/gtk2-unicode-release-2.8 -I/usr/include/wx-2.8 -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES -D__WXGTK__ -Wall -DSTRICT -Wno-write-strings    -c -o Calculator.o Calculator.cpp
../../depcomp: line 611: exec: g++: not found
make[2]: *** [Calculator.o] Error 127
make[2]: Leaving directory `/home/sush/Downloads/maitreya/maitreya6/trunk/src/base'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/sush/Downloads/maitreya/maitreya6/trunk/src'
make: *** [install-recursive] Error 1

</CODE>

I have absolutely no idea how to create make and then install from source code. Please can someone guide me step by step.

Many Thanks.

---

### Post by anksush on 2010-03-22
I was able to solve this myself. I just had to refer some ubuntu documentation.

Detailed steps [here.]("http://makegadgetswork.blogspot.com/2010/03/install-maitreya-vedic-astrology_22.html")

---

