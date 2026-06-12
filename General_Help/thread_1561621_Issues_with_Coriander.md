---
title: "Issues with Coriander"
date: 2010-08-26
forum: General Help
---

### Post by sodabread on 2010-08-26
Hey there,

I've been trying to configure Coriander on my 32-bit system (Ubuntu v10.04), but I've run into an issue that I've only found discussion boards for in French, a language I'm nowhere near fluent enough in to translate on a tech forum. When I run the ./configure command in the coriander folder, things run fine. Everything configures normally, and I move on. But then, when I run 'make', it runs a few lines making folders, and then this error message pops up:

In file included from coriander.h:92,
                 from main.c:24:
conversions.h:26: error: expected declaration specifiers or ‘...’ before ‘SDL_Overlay’
make[2]: *** [main.o] Error 1
make[2]: Leaving directory `/home/milo/Downloads/coriander-2.0.0/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/milo/Downloads/coriander-2.0.0'
make: *** [all] Error 2

I have scoured the internet in search of an answer to this, but have come up with zip. Also, I'm fairly new to Ubuntu, and have only been working with it for a couple of months. Please help!

Thanks, 
Soda

---

### Post by kapare on 2010-09-15
I'm wonrking to make this work for fedora 13 and when doing make or make check I have the same issue!

But if I do sudo yum install coriander it works but with some segfault when using it I report a Bugzilla on Red Hat with there automatic report...

Did you found something else?

[fedora@fedora13 coriander-2.0.0]$ make check
Making check in po
make[1]: Entering directory `/home/fedora/Downloads/coriander-2.0.0/po'
make[1]: Nothing to be done for `check'.
make[1]: Leaving directory `/home/fedora/Downloads/coriander-2.0.0/po'
Making check in src
make[1]: Entering directory `/home/fedora/Downloads/coriander-2.0.0/src'
gcc -DHAVE_CONFIG_H -I. -I.. -Wall -DPACKAGE_DATA_DIR=\""/usr/local/share"\" -DPACKAGE_LOCALE_DIR=\""/usr/local//locale"\" -DORBIT2=1 -pthread -I/usr/include/libgnomeui-2.0 -I/usr/include/libart-2.0 -I/usr/include/gconf/2 -I/usr/include/gnome-keyring-1 -I/usr/include/libgnome-2.0 -I/usr/include/libbonoboui-2.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/gtk-2.0 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/orbit-2.0 -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libbonobo-2.0 -I/usr/include/bonobo-activation-2.0 -I/usr/include/libxml2 -I/usr/include/pango-1.0 -I/usr/include/gail-1.0 -I/usr/include/freetype2 -I/usr/include/atk-1.0 -I/usr/lib/gtk-2.0/include -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/include/libpng12      -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64     -g -O2 -MT main.o -MD -MP -MF .deps/main.Tpo -c -o main.o main.c
In file included from coriander.h:92,
                 from main.c:24:
conversions.h:26: error: expected declaration specifiers or ‘...’ before ‘SDL_Overlay’
make[1]: *** [main.o] Error 1
make[1]: Leaving directory `/home/fedora/Downloads/coriander-2.0.0/src'
make: *** [check-recursive] Error 1

---

### Post by kapare on 2010-09-15
aaaa I just do sudo yum search libsdl this pop SDL package and then install :

sudo yum install SDL SDL-devel

So you can easilly do sudo apt-cache search libsdl OR SDL to found proper package to install!

I'm now stock to 

/usr/bin/ld: tools.o: undefined reference to symbol 'XOpenDisplay' ....

---

### Post by kapare on 2010-09-15
The problem on fedora was implicit DSO linking for :
/usr/bin/ld: tools.o: undefined reference to symbol 'XOpenDisplay' ....

More info on : [http://old.nabble.com/Coriander-fix-for-implicit-DSO-linking-to27726350.html](http://old.nabble.com/Coriander-fix-for-implicit-DSO-linking-to27726350.html)

The patch have only been added on the git tree so no rpm or deb package seem to have been release for the coriander 2.0.1 version. So here the steps to recompile it.


git clone git://coriander.git.sourceforge.net/gitroot/coriander/coriander

cd coriander

autoconf
autoheader
aclocal
automake
automake --add-missing

I add to rerun everything back??
autoconf
autoheader
autoheader
automake
# Found this in man autoreconf


it failed because of libgnomeui package missing

sudo apt-get install libgnomeui-dev

It failed because of libxv-dev package missing

sudo apt-get install libxv-dev

It failed because of libraw1394 package missing

sudo apt-get install libraw1394-dev

More...

sudo apt-get install libdc1394-22-dev
sudo apt-get install ftplib-dev

./configure

make

make install      
# simply go to 
cd src
./coriander

Et voila!

---

