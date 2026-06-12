---
title: "Compiling Komparator 0.3"
date: 2006-02-27
forum: General Help
---

### Post by gingermark on 2006-02-27
Hi there,

I'm looking to install [Komparator 0.3]("http://kde-apps.org/content/show.php?content=33545"). There appears to be no binary version available, so I have to compile it. 

I type './configure' and it does it's thing.
Great.
I type 'make' and I get the errors you can see at the end of the output below.

I have compiled other programs, but am hardly an expert, and don't understand the error messages. Any help there would be appreciated.

Best regards,
gingermark.


'make' output:
> make  all-recursive
make[1]: Entering directory `/home/gingermark/debs+sources/komparator-0.3'
Making all in doc
make[2]: Entering directory `/home/gingermark/debs+sources/komparator-0.3/doc'
/usr/bin/meinproc --check --cache index.cache.bz2 ./index.docbook
meinproc: WARNING: KLocale: trying to look up "" in catalog. Fix the program
Making all in .
make[3]: Entering directory `/home/gingermark/debs+sources/komparator-0.3/doc'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/gingermark/debs+sources/komparator-0.3/doc'
make[2]: Leaving directory `/home/gingermark/debs+sources/komparator-0.3/doc'
Making all in po
make[2]: Entering directory `/home/gingermark/debs+sources/komparator-0.3/po'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/gingermark/debs+sources/komparator-0.3/po'
Making all in src
make[2]: Entering directory `/home/gingermark/debs+sources/komparator-0.3/src'
source='main.cpp' object='main.o' libtool=no \
depfile='.deps/main.Po' tmpdepfile='.deps/main.TPo' \
depmode=gcc3 /bin/sh ../admin/depcomp \
g++ -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -O2 -Wformat-security -Wmissing-format-attribute -Wno-non-virtual-dtor -fno-exceptions -fno-check-new -fno-common  -c -o main.o `test -f 'main.cpp' || echo './'`main.cpp
/usr/share/qt3/bin/moc ./komparator.h -o komparator.moc
source='komparator.cpp' object='komparator.o' libtool=no \
depfile='.deps/komparator.Po' tmpdepfile='.deps/komparator.TPo' \
depmode=gcc3 /bin/sh ../admin/depcomp \
g++ -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -O2 -Wformat-security -Wmissing-format-attribute -Wno-non-virtual-dtor -fno-exceptions -fno-check-new -fno-common  -c -o komparator.o `test -f 'komparator.cpp' || echo './'`komparator.cpp
/usr/share/qt3/bin/moc ./komparatorwidget.h -o komparatorwidget.moc
source='komparatorwidget.cpp' object='komparatorwidget.o' libtool=no \
depfile='.deps/komparatorwidget.Po' tmpdepfile='.deps/komparatorwidget.TPo' \
depmode=gcc3 /bin/sh ../admin/depcomp \
g++ -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -O2 -Wformat-security -Wmissing-format-attribute -Wno-non-virtual-dtor -fno-exceptions -fno-check-new -fno-common  -c -o komparatorwidget.o `test -f 'komparatorwidget.cpp' || echo './'`komparatorwidget.cpp
komparatorwidget.cpp:616: error: ISO C++ forbids declaration of &#8216;QTabBarToolTip&#8217; with no type
komparatorwidget.cpp:616: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
make[2]: *** [komparatorwidget.o] Error 1
make[2]: Leaving directory `/home/gingermark/debs+sources/komparator-0.3/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/gingermark/debs+sources/komparator-0.3'
make: *** [all] Error 2

---

### Post by bernardfrancois on 2006-02-27
```

komparatorwidget.cpp:616: error: ISO C++ forbids declaration of &#8216;QTabBarToolTip&#8217; with no type
komparatorwidget.cpp:616: error: expected &#8216;;&#8217; before &#8216;*&#8217; token

```

These are mistakes in the program code. Every statement in C++ is terminated with a ';'. Probably one has been forgotten (that's the 2nd error). The first error is about a variable which has been used without specifying a type.

Sometimes there's a mistake on a previous line causing those mistakes.
You should contact the developers and show these two error lines. But make sure you were trying to compile the latest _stable_ version. Also try to check the site if they suggest a specific compiler to use to compile the code.

[edit]
You also have to make sure first (before compiling) that you have all packges that this program depends on. But since it only depends on KDE3.4.x (make sure you have that version) and you are using Kubuntu, you probably won't have to resolve any dependencies.
[/edit]

---

### Post by bernardfrancois on 2006-02-27
I was curious so I checked the source code. The definition of the last member in the following struct is the line with the compilation error. I don't see any problem. Anyone?

```

struct QTabPrivate // FIXME: evil! evil! evil! don't do that! really! i mean it!
{                  // from qtabbar.cpp
    int id;
    int focus;
#ifndef QT_NO_ACCEL
    QAccel * a;
#endif
    QTab *pressed;
    QTabBar::Shape s;
    QToolButton* rightB;
    QToolButton* leftB;
    int btnWidth;
    bool  scrolls;
    QTabBarToolTip * toolTips;
};

```

---

### Post by gingermark on 2006-02-27
I'm running KDE 3.5.1 - to be honest I didn't notice that "depends on" line. Would that be the cause of the problem then?

I didn't realise KDE 3.5 was much different from the 3.4.x series.

---

### Post by bernardfrancois on 2006-02-27
I don't think it's a problem if you have a newer KDE version. And if it is, then it's the problem of the developers of your program, since nobody will be able to run it in the future.

I think you should contact the developers about those two compilation errors.
I checked their [website](http://komparator.sourceforge.net/) and the Komparator program seems to be a new project (since January).

---

### Post by gingermark on 2006-02-27
The developer kindly provided 3 patches, and I could then compile the program.

I think it's a pretty useful utility, especially now larger hard drives are more common and a lot of us move a lot of data about. As such, I'm attaching the .deb that checkinstall created, in the hope it might be of use to anyone else who might want to install this app.

To clarify, I'm running Breezy on the K7 kernel, although checkinstall claims the package is for i386, so hopefully it'll work for most users. No guarantees though :-)

P.S. For some reason I wasn't allowed to upload a .deb file (although I'm sure I've seen other users do it). As such, I simply zipped the deb file in order for it to be accepted. EDIT: And for some reason my sig has gone to the top of the post!

---

### Post by sirlancelot on 2006-02-28
Thanks for the .deb

I'm running i386 and it works great! \\:D/

---

### Post by bailout on 2006-02-28
Looks like an interesting program. I use something similar built into PowerDesk pro on win to sync a backup of my data partition onto an external hd.

However I think this would be better built into konq than a seperate app.

---

