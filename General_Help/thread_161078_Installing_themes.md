---
title: "Installing themes"
date: 2006-04-16
forum: General Help
---

### Post by lzfy on 2006-04-16
Hi can someone help me with installing themes? I know it is a little bit difficult installing themes in KDE. You have to compile them.
but when I do that I get the following error message
> lzfy@ubuntu:~/33203-Hypnotista_Siyah-0.1/Hypnotista_Siyah-0.1$ ./configure
checking build system type... i686-pc-linux
checking host system type... i686-pc-linux
checking target system type... i686-pc-linux
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
lzfy@ubuntu:~/33203-Hypnotista_Siyah-0.1/Hypnotista_Siyah-0.1$


I know I'm missing a package but I don't know which one that is. :oops:

btw I'm using Kubuntu 6.06 flight 6

---

### Post by mscman on 2006-04-16
You're missing a compiler.  You need to install the package "build-essential"

---

### Post by ComplexNumber on 2006-04-16
[quote=lzfy]Hi can someone help me with installing themes? I know it is a little bit difficult installing themes in KDE. You have to compile them.
but when I do that I get the following error message


I know I'm missing a package but I don't know which one that is. :oops:

btw I'm using Kubuntu 6.06 flight 6[/quote]
install the gcc packages.

---

### Post by ace2005 on 2006-04-16
I think this is all you need

build-essential
kdebase-dev
kdelibs4-dev
libx11-dev
libqt4-dev

I think thats all but i'm not sure, i sort of went and installed just about everything i could find after searching for "kde dev" "qt dev" "x11 dev" and most of the compilers

oh and i also installed some gtk dev files since i wanted to install qtcurve and searched for "gtk java" and installed that too since i wanted my qt,gtk,java apps to look the same.

---

### Post by lzfy on 2006-04-16
Thanks guys :)  it works now. I just build my first theme 8)

edit - Ok I installed the theme but I can't see it in the appearance menu. Do I need to do more things?

---

### Post by lzfy on 2006-04-17
> lzfy@ubuntu:~/Desktop/Hypnotista_Siyah-0.1$ sudo make install
Password:
Making install in kwin
make[1]: Entering directory `/home/lzfy/Desktop/Hypnotista_Siyah-0.1/kwin'
Making install in .
make[2]: Entering directory `/home/lzfy/Desktop/Hypnotista_Siyah-0.1/kwin'
/usr/share/qt3/bin/moc ./Hypnotista_Siyah.h -o Hypnotista_Siyah.moc
if /bin/sh ../libtool --silent --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.. -
I./../../lib -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPO
RT  -D_REENTRANT  -Wnon-virtual-dtor -Wno-long-long -Wundef -Wall -W -Wpointer-a
rith -Wwrite-strings -O2 -fno-exceptions -fno-check-new -fno-common -MT Hypnotis
ta_Siyah.lo -MD -MP -MF ".deps/Hypnotista_Siyah.Tpo" -c -o Hypnotista_Siyah.lo H
ypnotista_Siyah.cpp; \
        then mv -f ".deps/Hypnotista_Siyah.Tpo" ".deps/Hypnotista_Siyah.Plo"; el
se rm -f ".deps/Hypnotista_Siyah.Tpo"; exit 1; fi
/usr/include/kde/kdecoration.h:176: warning: 'class KDecorationProvides' has vir
tual functions but non-virtual destructor
Hypnotista_Siyah.h:130: warning: non-local variable 'Hypnotista_Siyah::<anonymou
s struct> Hypnotista_Siyah::Settings_Param' uses anonymous type
Hypnotista_Siyah.cpp:747: warning: unused parameter 'bttstate'
/bin/sh ../libtool --silent --mode=link g++  -Wnon-virtual-dtor -Wno-long-long -
Wundef -Wall -W -Wpointer-arith -Wwrite-strings -O2 -fno-exceptions -fno-check-n
ew -fno-common   -o kwin3_Hypnotista_Siyah.la -rpath /usr/local/kde/lib/kde3 -L/
usr/X11R6/lib -L/usr/share/qt3/lib -L/usr/lib  -avoid-version -module -no-undefi
ned  -R /usr/lib -R /usr/share/qt3/lib -R /usr/X11R6/lib  -module Hypnotista_Siy
ah.lo -lkdeui /usr/lib/libkdecorations.la
make[3]: Entering directory `/home/lzfy/Desktop/Hypnotista_Siyah-0.1/kwin'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/kde/lib/kde3" || mkdir -p -- . "/usr/local/kde/lib/kde3"
 /bin/sh ../libtool --silent --mode=install /usr/bin/install -c -p  'kwin3_Hypno
tista_Siyah.la' '/usr/local/kde/lib/kde3/kwin3_Hypnotista_Siyah.la'
PATH="$PATH:/sbin" ldconfig -n /usr/local/kde/lib/kde3
test -z "/usr/local/kde/share/apps/kwin" || mkdir -p -- . "/usr/local/kde/share/
apps/kwin"
 /usr/bin/install -c -p -m 644 'Hypnotista_Siyah.desktop' '/usr/local/kde/share/
apps/kwin/Hypnotista_Siyah.desktop'
make[3]: Leaving directory `/home/lzfy/Desktop/Hypnotista_Siyah-0.1/kwin'
make[2]: Leaving directory `/home/lzfy/Desktop/Hypnotista_Siyah-0.1/kwin'
Making install in config
make[2]: Entering directory `/home/lzfy/Desktop/Hypnotista_Siyah-0.1/kwin/config
'
/usr/share/qt3/bin/uic -L /usr/lib/kde3/plugins/designer -nounload -o Hypnotista
_Siyahconfig.h ./Hypnotista_Siyahconfig.ui
/usr/share/qt3/bin/moc ./config.h -o config.moc
if /bin/sh ../../libtool --silent --mode=compile --tag=CXX g++ -DHAVE_CONFIG_H -
I. -I. -I../.. -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUP
PORT  -D_REENTRANT  -Wnon-virtual-dtor -Wno-long-long -Wundef -Wall -W -Wpointer
-arith -Wwrite-strings -O2 -fno-exceptions -fno-check-new -fno-common  -MT confi
g.lo -MD -MP -MF ".deps/config.Tpo" -c -o config.lo config.cpp; \
        then mv -f ".deps/config.Tpo" ".deps/config.Plo"; else rm -f ".deps/conf
ig.Tpo"; exit 1; fi
config.h:45: warning: non-local variable '<anonymous struct> Config_Params' uses
 anonymous type
config.h:51: warning: non-local variable '<anonymous struct> Read_Config' uses a
nonymous type
config.cpp: In member function 'void Hypnotista_SiyahConfig::save(KConfig*)':
config.cpp:156: warning: 'size' is used uninitialized in this function
/usr/share/qt3/bin/moc Hypnotista_Siyahconfig.h -o Hypnotista_Siyahconfig.moc
rm -f Hypnotista_Siyahconfig.cpp
echo '#include <klocale.h>' > Hypnotista_Siyahconfig.cpp
/usr/share/qt3/bin/uic -L /usr/lib/kde3/plugins/designer -nounload -tr tr2i18n -
i Hypnotista_Siyahconfig.h ./Hypnotista_Siyahconfig.ui > Hypnotista_Siyahconfig.
cpp.temp ; ret=$?; \
        /usr/bin/perl -pe "s,tr2i18n( \"\" ),QString::null,g" Hypnotista_Siyahco
nfig.cpp.temp | /usr/bin/perl -pe "s,tr2i18n( \"\"\, \"\" ),QString::null,g" | /
usr/bin/perl -pe "s,image([0-9][0-9]*)_data,img\$1_Hypnotista_Siyahconfig,g" >>
Hypnotista_Siyahconfig.cpp ;\
        rm -f Hypnotista_Siyahconfig.cpp.temp ;\
        if test "$ret" = 0; then echo '#include "Hypnotista_Siyahconfig.moc"' >>
 Hypnotista_Siyahconfig.cpp; else rm -f Hypnotista_Siyahconfig.cpp ; exit $ret ;
 fi
if /bin/sh ../../libtool --silent --mode=compile --tag=CXX g++ -DHAVE_CONFIG_H -
I. -I. -I../.. -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUP
PORT  -D_REENTRANT  -Wnon-virtual-dtor -Wno-long-long -Wundef -Wall -W -Wpointer
-arith -Wwrite-strings -O2 -fno-exceptions -fno-check-new -fno-common  -MT Hypno
tista_Siyahconfig.lo -MD -MP -MF ".deps/Hypnotista_Siyahconfig.Tpo" -c -o Hypnot
ista_Siyahconfig.lo Hypnotista_Siyahconfig.cpp; \
        then mv -f ".deps/Hypnotista_Siyahconfig.Tpo" ".deps/Hypnotista_Siyahcon
fig.Plo"; else rm -f ".deps/Hypnotista_Siyahconfig.Tpo"; exit 1; fi
/bin/sh ../../libtool --silent --mode=link --tag=CXX g++  -Wnon-virtual-dtor -Wn
o-long-long -Wundef -Wall -W -Wpointer-arith -Wwrite-strings -O2 -fno-exceptions
 -fno-check-new -fno-common    -o kwin_Hypnotista_Siyah_config.la -rpath /usr/lo
cal/kde/lib/kde3 -L/usr/X11R6/lib -L/usr/share/qt3/lib -L/usr/lib  -avoid-versio
n -module -no-undefined  -R /usr/lib -R /usr/share/qt3/lib -R /usr/X11R6/lib  -m
odule config.lo Hypnotista_Siyahconfig.lo -lkdeui
make[3]: Entering directory `/home/lzfy/Desktop/Hypnotista_Siyah-0.1/kwin/config
'
test -z "/usr/local/kde/lib/kde3" || mkdir -p -- . "/usr/local/kde/lib/kde3"
 /bin/sh ../../libtool --silent --mode=install /usr/bin/install -c -p  'kwin_Hyp
notista_Siyah_config.la' '/usr/local/kde/lib/kde3/kwin_Hypnotista_Siyah_config.l
a'
PATH="$PATH:/sbin" ldconfig -n /usr/local/kde/lib/kde3
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/lzfy/Desktop/Hypnotista_Siyah-0.1/kwin/config'
make[2]: Leaving directory `/home/lzfy/Desktop/Hypnotista_Siyah-0.1/kwin/config'
make[1]: Leaving directory `/home/lzfy/Desktop/Hypnotista_Siyah-0.1/kwin'
make[1]: Entering directory `/home/lzfy/Desktop/Hypnotista_Siyah-0.1'
cd . && /bin/sh /home/lzfy/Desktop/Hypnotista_Siyah-0.1/admin/missing --run auto                                                                                                  header
/home/lzfy/Desktop/Hypnotista_Siyah-0.1/admin/missing: line 52: autoheader: comm                                                                                                  and not found
WARNING: `autoheader' is missing on your system.  You should only need it if
         you modified `acconfig.h' or `configure.in'.  You might want
         to install the `Autoconf' and `GNU m4' packages.  Grab them
         from any GNU archive site.
rm -f stamp-h1
touch config.h.in
cd . && /bin/sh ./config.status config.h
config.status: creating config.h
config.status: config.h is unchanged
make[2]: Entering directory `/home/lzfy/Desktop/Hypnotista_Siyah-0.1'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/lzfy/Desktop/Hypnotista_Siyah-0.1'
make[1]: Leaving directory `/home/lzfy/Desktop/Hypnotista_Siyah-0.1'
lzfy@ubuntu:~/Desktop/Hypnotista_Siyah-0.1$


this is the output

---

### Post by ComplexNumber on 2006-04-17
to start with, it tells you there that you need autoconf and m4.

---

### Post by lzfy on 2006-04-17
I did that but it still doesn't work.

---

### Post by ComplexNumber on 2006-04-17
[quote=lzfy]I did that but it still doesn't work.[/quote] ok, lets get this straight, what are you trying to do now :confused:. above, you've mentioned that you've installed the theme.

---

### Post by Neo Ex on 2006-04-17
Before compiling use
```
./configure --prefix=`kde-config --prefix`
```
instead of
```
./configure
```

---

### Post by GeneralZod on 2006-04-17
[QUOTE=lzfy]I did that but it still doesn't work.[/QUOTE]

I don't see any serious errors there - it almost sounds like the missing items are optional, and that the ./configure finished successfully.  Did you try

```

make

```

?

---

### Post by ComplexNumber on 2006-04-17
[quote=GeneralZod]I don't see any serious errors there - it almost sounds like the missing items are optional, and that the ./configure finished successfully.  Did you try

```

make

``` 
?[/quote] i guess he must have done otherwise it would show "no targets to make" (although, maybe i should let lzfy speak about this :p).

---

### Post by lzfy on 2006-04-18
> ok, lets get this straight, what are you trying to do now . above, you've mentioned that you've installed the theme.

Well i did all the steps but I still can't select the theme in the Control Panel.

> Before compiling use

./configure --prefix=`kde-config --prefix`

I will try this when I get home :) 

[QUOTE=ComplexNumber]i guess he must have done otherwise it would show "no targets to make" (although, maybe i should let lzfy speak about this :p).[/QUOTE]

hehe I did sudo make install. The problem is not compiling, the problem is that I can select the theme in CP, maybe I should look somewhere else?

---

### Post by lzfy on 2006-04-18
> Before compiling use
 
 ./configure --prefix=`kde-config --prefix`

Thank you very much :)  It works now. 

Can you tell me what --prefix=`kde-config --prefix` does?

---

### Post by Neo Ex on 2006-04-18
It will install the program in the directory where KDE and its programs are installed. In our case it is /usr/share/apps for the programs. If you run './configure' it will install the program in another folder (for example /usr/local/share) and KDE can't find it.

---

### Post by lzfy on 2006-04-18
Ah I see, thanks for the explanation :)

so basically I have installed the theme on more then one place, if so is it easy to remove?

---

### Post by Neo Ex on 2006-04-19
You can delete the files, or you can run 'sudo make uninstall' in the directory where are the sources. But if you do this, it will uninstall the theme in /usr/share/apps. Thus, you have to create a new folder with the sources, then use './configure' and run 'sudo make uninstall'. It might uninstall the previous installation (that doesn't work). I hope you've understood :) (I'm Italian and it's not so simple trying to explain).

---

### Post by lzfy on 2006-04-19
Thank you Neo Ex for the great explanation, it's really usefull to know this things:)

---

