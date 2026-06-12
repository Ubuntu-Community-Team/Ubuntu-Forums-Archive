---
title: "Need help installing from source."
date: 2010-03-01
forum: General Help
---

### Post by letmekilluplz on 2010-03-01
I downloaded this program with clicks automatically and I can't seem to get it installed.

I've been trying to use this process:

unpack
cd to the package
./configure
make
sudo makeinstall

When I rune ./configure it gives me this: 

```
$ ./configure
Checking for c compiler ... gcc
Checking for c++ compiler ... g++
Checking for GNU Make ... yes, using make
Checking for extra headers ... no
Checking for extra libraries ... no
Checking for gcc support of -MM option ... yes
Checking for g++ support of -MM option ... yes
Checking for inttypes.h ... yes
Checking for unistd.h ... yes
Checking for malloc.h ... yes
Checking for X11 header presence ... not found (check if the dev(el) packages are installed
Checking for X11 ... no
Checking for XTest extension ... no
No X11 found. Not building anything that depends on it

Debug symbols disabled.
All compiler warnings disabled.

Cleaning up source tree ... done

Generating config.mak ... done.



```

Any help? Thanks in advance!

---

### Post by mc4man on 2010-03-01
Before you build anything take a look in the source folder for any text files, sometimes they're helpful

Also running ./configure --help can be a good thing to check.

What you're probalbly missing ( but maybe not all) is 

```
sudo apt-get install libx11-dev
```

---

### Post by letmekilluplz on 2010-03-01
I installed that and I'm getting the same errors, running configure --help does not give any useful information, and I checked the install file and what I have been doing is correct.

---

### Post by mc4man on 2010-03-02
> I installed that and I'm getting the same errors

You may wish to post/link to what source you're trying to build and what release of ubuntu you have installed. some times sources are limited to a range of the versions of some libraires that are usable

---

### Post by timZZ on 2010-03-02
Just remember if you have automatic updates turned on dependencies that application may require maybe updated while your original application is not and this can effect how the application runs.

Just a side note.

---

### Post by letmekilluplz on 2010-03-02
I am trying to install a program called xautoclick and I'm using Ubuntu 9.10

---

### Post by mc4man on 2010-03-02
If you're runnuing a 64 bit install probably time to say so, ...anyway on a 32 bit 9.10

> doug@doug-desktop:~/Download/xautoclick-[COLOR="Blue"]0.20-[/COLOR]src$ ./configure
Checking for c compiler ... gcc
Checking for c++ compiler ... g++
Checking for GNU Make ... yes, using make
Checking for extra headers ... no
Checking for extra libraries ... no
Checking for gcc support of -MM option ... yes
Checking for g++ support of -MM option ... yes
Checking for inttypes.h ... yes
Checking for unistd.h ... yes
Checking for malloc.h ... yes
Checking for X11 header presence ... yes (using /usr/include)
Checking for X11 ... yes (using -L/usr/lib32 -lX11 -lXext)
Checking for XTest extension ... yes
Checking for gtk-config ... gtk-config
Checking for GTK cflags ... -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include
Checking for GTK libs ... -L/usr/lib -lgtk -lgdk -rdynamic -lgmodule -lglib -ldl -lXi -lXext -lX11 -lm
Checking for glib-config ... glib-config
Checking for glib cflags ... -I/usr/include/glib-1.2 -I/usr/lib/glib/include
Checking for glib libs ... -L/usr/lib -lglib
Checking for pkg-config ... pkg-config
Checking for GTK+ 2.0 ... yes
Checking for GTK+ 2.0 cflags ... -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  
Checking for GTK+ 2.0 libs ... -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lpangoft2-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lgio-2.0 -lcairo -lpango-1.0 -lfreetype -lfontconfig -lgobject-2.0 -lgmodule-2.0 -lglib-2.0  
Checking for glib 2.0 cflags ... -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  
Checking for glib 2.0 libs ... -lglib-2.0  
Checking for Qt 3.x header files ... -I/usr/share/qt3/include
Checking for Qt 3.x libraries ... -L/usr/share/qt3/lib -lqt-mt

Debug symbols disabled.
All compiler warnings disabled.

Cleaning up source tree ... done

Generating config.mak ... done.

aAutoClick    : yes
cAutoClick    : yes
gAutoClick    : yes
gAutoClick2   : yes
qtAutoClick   : yes

Installation to /usr/local

So I see at a min. ( i build a lot so the configure went right thru ,  
libx11-dev
libqt3-mt-dev
libgtk2.0-dev
libglib2.0-dev

There will be a number of other packages possibly installed as dep's of the above listed.

---

