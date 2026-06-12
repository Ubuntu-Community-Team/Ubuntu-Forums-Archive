---
title: "Error when installing Kiba Dock!"
date: 2010-08-05
forum: General Help
---

### Post by reydempto on 2010-08-05
Ladies and gentlemen, I am trying to install Kiba Dock on Ubuntu 10.04 using [this tutorial]("http://hydtechblog.com/2010/03/23/how-to-install-kiba-dock-on-karmic-and-lucid/"). However, at this particular spot I hit an error.

When I execute the command 

```
cd kiba-plugins/     <--Works fine
./autogen.sh         <--Works fine
```
but...

```
sudo make install
```
Yields this output:

```

Making install in plugins
make[1]: Entering directory `/home/steve/kiba-plugins/plugins'
make  install-recursive
make[2]: Entering directory `/home/steve/kiba-plugins/plugins'
Making install in bounce
make[3]: Entering directory `/home/steve/kiba-plugins/plugins/bounce'
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../.. -pthread -D_REENTRANT -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/libxml2 -I/usr/include/akamaru -I/usr/include/librsvg-2 -I/usr/local/include/kiba-dock   -DDATADIR='"/usr/local/share"' -DLIBDIR='"/usr/local/lib"' -I../../plugins -I/usr/local/include    -g -O2 -MT bounce.lo -MD -MP -MF ".deps/bounce.Tpo" -c -o bounce.lo bounce.c; \
	then mv -f ".deps/bounce.Tpo" ".deps/bounce.Plo"; else rm -f ".deps/bounce.Tpo"; exit 1; fi
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I. -I../.. -pthread -D_REENTRANT -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/libxml2 -I/usr/include/akamaru -I/usr/include/librsvg-2 -I/usr/local/include/kiba-dock -DDATADIR=\"/usr/local/share\" -DLIBDIR=\"/usr/local/lib\" -I../../plugins -I/usr/local/include -g -O2 -MT bounce.lo -MD -MP -MF .deps/bounce.Tpo -c bounce.c  -fPIC -DPIC -o .libs/bounce.o
bounce.c:27:18: error: kiba.h: No such file or directory
bounce.c: In function ‘plugin_unload’:
bounce.c:637: error: ‘Kiba’ undeclared (first use in this function)
bounce.c:637: error: (Each undeclared identifier is reported only once
bounce.c:637: error: for each function it appears in.)
bounce.c:637: error: ‘kiba’ undeclared (first use in this function)
bounce.c: In function ‘plugin_load’:
bounce.c:666: error: ‘Kiba’ undeclared (first use in this function)
bounce.c:666: error: ‘kiba’ undeclared (first use in this function)
bounce.c:667: error: ‘KibaPrefsFile’ undeclared (first use in this function)
bounce.c:667: error: ‘file’ undeclared (first use in this function)
bounce.c:686: warning: passing argument 2 of ‘kiba_prefs_add_callback’ from incompatible pointer type
/usr/local/include/kiba-dock/kiba-prefs.h:92: note: expected ‘KibaPrefCallback’ but argument is of type ‘char *’
bounce.c:686: warning: passing argument 4 of ‘kiba_prefs_add_callback’ makes integer from pointer without a cast
/usr/local/include/kiba-dock/kiba-prefs.h:92: note: expected ‘gboolean’ but argument is of type ‘struct KibaBounce *’
bounce.c:686: error: too many arguments to function ‘kiba_prefs_add_callback’
bounce.c:688: warning: passing argument 2 of ‘kiba_prefs_add_callback’ from incompatible pointer type
/usr/local/include/kiba-dock/kiba-prefs.h:92: note: expected ‘KibaPrefCallback’ but argument is of type ‘char *’
bounce.c:688: warning: passing argument 4 of ‘kiba_prefs_add_callback’ makes integer from pointer without a cast
/usr/local/include/kiba-dock/kiba-prefs.h:92: note: expected ‘gboolean’ but argument is of type ‘struct KibaBounce *’
bounce.c:688: error: too many arguments to function ‘kiba_prefs_add_callback’
bounce.c:690: warning: passing argument 2 of ‘kiba_prefs_add_callback’ from incompatible pointer type
/usr/local/include/kiba-dock/kiba-prefs.h:92: note: expected ‘KibaPrefCallback’ but argument is of type ‘char *’
bounce.c:690: warning: passing argument 4 of ‘kiba_prefs_add_callback’ makes integer from pointer without a cast
/usr/local/include/kiba-dock/kiba-prefs.h:92: note: expected ‘gboolean’ but argument is of type ‘struct KibaBounce *’
bounce.c:690: error: too many arguments to function ‘kiba_prefs_add_callback’
bounce.c:692: warning: passing argument 2 of ‘kiba_prefs_add_callback’ from incompatible pointer type
/usr/local/include/kiba-dock/kiba-prefs.h:92: note: expected ‘KibaPrefCallback’ but argument is of type ‘char *’
bounce.c:692: warning: passing argument 4 of ‘kiba_prefs_add_callback’ makes integer from pointer without a cast
/usr/local/include/kiba-dock/kiba-prefs.h:92: note: expected ‘gboolean’ but argument is of type ‘struct KibaBounce *’
bounce.c:692: error: too many arguments to function ‘kiba_prefs_add_callback’
bounce.c:694: warning: passing argument 2 of ‘kiba_prefs_add_callback’ from incompatible pointer type
/usr/local/include/kiba-dock/kiba-prefs.h:92: note: expected ‘KibaPrefCallback’ but argument is of type ‘char *’
bounce.c:694: warning: passing argument 4 of ‘kiba_prefs_add_callback’ makes integer from pointer without a cast
/usr/local/include/kiba-dock/kiba-prefs.h:92: note: expected ‘gboolean’ but argument is of type ‘struct KibaBounce *’
bounce.c:694: error: too many arguments to function ‘kiba_prefs_add_callback’
bounce.c:696: warning: passing argument 2 of ‘kiba_prefs_add_callback’ from incompatible pointer type
/usr/local/include/kiba-dock/kiba-prefs.h:92: note: expected ‘KibaPrefCallback’ but argument is of type ‘char *’
bounce.c:696: warning: passing argument 4 of ‘kiba_prefs_add_callback’ makes integer from pointer without a cast
/usr/local/include/kiba-dock/kiba-prefs.h:92: note: expected ‘gboolean’ but argument is of type ‘struct KibaBounce *’
bounce.c:696: error: too many arguments to function ‘kiba_prefs_add_callback’
bounce.c: At top level:
bounce.c:729: error: ‘KIBA_PLUGIN_MULTIPLE_LOADABLE’ undeclared here (not in a function)
bounce.c:735: warning: excess elements in struct initializer
bounce.c:735: warning: (near initialization for ‘vtable’)
bounce.c:739:59: error: macro "KIBA_INIT_PLUGIN" passed 5 arguments, but takes just 2
bounce.c:739: warning: data definition has no type or storage class
make[3]: *** [bounce.lo] Error 1
make[3]: Leaving directory `/home/steve/kiba-plugins/plugins/bounce'
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory `/home/steve/kiba-plugins/plugins'
make[1]: *** [install] Error 2
make[1]: Leaving directory `/home/steve/kiba-plugins/plugins'
make: *** [install-recursive] Error 1

```

So what's the deal?

---

### Post by reydempto on 2010-08-05
To anyone else having problems with Kiba Dock-- Follow this tutorial EXACTLY, and it will work in 10.04!

[http://ubuntuforums.org/showthread.php?t=1201132]("http://ubuntuforums.org/showthread.php?t=1201132")

Something was placed in an incorrect folder the first time I tried it. There we go!

---

