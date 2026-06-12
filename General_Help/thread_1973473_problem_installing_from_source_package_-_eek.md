---
title: "problem installing from source package - eek"
date: 2012-05-04
forum: General Help
---

### Post by agladkov1 on 2012-05-04
Hi,

I am completely new to Linux, but am very interested in giving the system a go.

I was trying to install a package called liPE; it's a disk partition editing utility, from source.

When trying ./configure it turned out that lipe required a dependency (gtk+ i think), which I proceeded to download and try to install from source, but after being presented with massive lists of yet more dependencies I eventually realised it *was* possible to install the original dependency through apt-get. All seemed to go well, though I managed to install some dependencies like ncurses manually by that point, although that went without errors.

After installing the dependency through apt-get, lipe then ./configured without any errors. HOWEVER, the 'make' failed with ' Make Error 1|2' , which seems like a very generic message, so I'll post the entire make log below:

```
lipe will be installed in /usr/sbin.

configure complete, now type 'make'
arseni@arseni:~/Downloads/lipe-1.12$ sudo make
make  all-recursive
make[1]: Entering directory `/home/arseni/Downloads/lipe-1.12'
Making all in src
make[2]: Entering directory `/home/arseni/Downloads/lipe-1.12/src'
if gcc -DHAVE_CONFIG_H -I. -I. -I..  -DSYSTEM_DATA_DIR=\""/usr/share"\"   -g -O2 -Wall -pthread -I/usr/include/gtk-2.0 -I/usr/lib/i386-linux-gnu/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/glib-2.0 -I/usr/lib/i386-linux-gnu/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12   -MT lipecurse.o -MD -MP -MF ".deps/lipecurse.Tpo" -c -o lipecurse.o lipecurse.c; \
    then mv -f ".deps/lipecurse.Tpo" ".deps/lipecurse.Po"; else rm -f ".deps/lipecurse.Tpo"; exit 1; fi
lipecurse.c: In function ‘error_curse’:
lipecurse.c:904:2: warning: format not a string literal and no format arguments [-Wformat-security]
if gcc -DHAVE_CONFIG_H -I. -I. -I..  -DSYSTEM_DATA_DIR=\""/usr/share"\"   -g -O2 -Wall -pthread -I/usr/include/gtk-2.0 -I/usr/lib/i386-linux-gnu/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/glib-2.0 -I/usr/lib/i386-linux-gnu/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12   -MT lipegtk.o -MD -MP -MF ".deps/lipegtk.Tpo" -c -o lipegtk.o lipegtk.c; \
    then mv -f ".deps/lipegtk.Tpo" ".deps/lipegtk.Po"; else rm -f ".deps/lipegtk.Tpo"; exit 1; fi
In file included from lipegtk.h:29:0,
                 from lipegtk.c:19:
common.h:162:39: error: unknown type name ‘off64_t’
common.h:163:40: error: unknown type name ‘off64_t’
lipegtk.c: In function ‘error_gtk’:
lipegtk.c:29:4: warning: format not a string literal and no format arguments [-Wformat-security]
lipegtk.c: In function ‘callback_goto_child’:
lipegtk.c:252:10: warning: assignment discards ‘const’ qualifier from pointer target type [enabled by default]
lipegtk.c: In function ‘callback_goto_last’:
lipegtk.c:350:11: warning: assignment discards ‘const’ qualifier from pointer target type [enabled by default]
lipegtk.c: In function ‘callback_save’:
lipegtk.c:425:4: warning: format not a string literal and no format arguments [-Wformat-security]
lipegtk.c:448:4: warning: implicit declaration of function ‘write_partition_table’ [-Wimplicit-function-declaration]
lipegtk.c: In function ‘fill_gwindow’:
lipegtk.c:664:2: warning: implicit declaration of function ‘read_partition_table’ [-Wimplicit-function-declaration]
make[2]: *** [lipegtk.o] Error 1
make[2]: Leaving directory `/home/arseni/Downloads/lipe-1.12/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/arseni/Downloads/lipe-1.12'
make: *** [all] Error 2

```

May it be possible that by messing around with manual installs from source I have inadvertently screwed up the system? Or might this be some other issue, such as the program im trying to install being completely incompatible with Ubuntu?

Thanks!

---

### Post by PhantomTurtle on 2012-05-04
You have to install build-essential first. So open up terminal and type in,
```
sudo apt-get install build-essential
```

Alternatively you can just search build-essential in the Ubuntu Software Center or Synaptic package manager and install them. Then try compiling again.

---

### Post by mc4man on 2012-05-04
The source is 3.5 years old & unmaintained - as is you won't be building gtk support on your current Ubuntu install

You could however build with just cli & ncurses, how well it will work I  don't know & never will. (i'd hope you know what your doing as far as pt, ect...

If really inclined then clean your source, configure out gtk, ect.

make distclean
./configure --disable-gtk2 && make


[http://www.sojaare.com/LiPE/man.php](http://www.sojaare.com/LiPE/man.php)

---

### Post by agladkov1 on 2012-05-05
[PhantomTurtle]("http://ubuntuforums.org/member.php?u=1450094"), I ran the command and it turns out I have the latest version, but thank you for the advice anyway!

---

### Post by agladkov1 on 2012-05-05
> **mc4man said:**
> The source is 3.5 years old & unmaintained - as is you won't be building gtk support on your current Ubuntu install

You could however build with just cli & ncurses, how well it will work I  don't know & never will. (i'd hope you know what your doing as far as pt, ect...

If really inclined then clean your source, configure out gtk, ect.

make distclean
./configure --disable-gtk2 && make


[http://www.sojaare.com/LiPE/man.php](http://www.sojaare.com/LiPE/man.php)

Fantastic, thank you very much! I ran it without gtk and it worked great. Brilliant. I'm back to Linux now!

---

