---
title: "Problem with a command while compiling"
date: 2010-01-01
forum: General Help
---

### Post by hexbase on 2010-01-01
Hi,

While making a program, i get this:

libtool: relink:  icc -shared  .libs/libxfce4kbd_private_la-xfce-shortcuts-provider.o .libs/libxfce4kbd_private_la-xfce-shortcuts-grabber.o .libs/libxfce4kbd_private_la-xfce-shortcut-dialog.o .libs/libxfce4kbd_private_la-xfce-shortcuts.o   
-L/usr/local/lib -lxfcegui4 -L/usr/lib -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lpangoft2-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lgio-2.0 -lcairo -lpango-1.0 -lfreetype -lz -lfontconfig -lgmodule-2.0 -lSM -lICE -lX11 -lxfce4util -lxfconf-0 -ldbus-glib-1 -ldbus-1 -lpthread -lrt -lgobject-2.0 -lglib-2.0  -Wl,-O1   -Wl,-soname -Wl,libxfce4kbd-private.so.5 -Wl,-version-script -Wl,.libs/libxfce4kbd-private.ver -o .libs/libxfce4kbd-private.so.5.0.0

xfce/2_libxfcegui4-4.6.1/libtool: line 7303: icc: command not found
libtool: install: error: relink `libxfce4kbd-private.la' with the above command before installing it

icc is the intel c compiler. The thing is that you need to run a bash script inside the directory you're going to use it to get it working.
So libtool needs to run that bash script first to use icc. 
How do i solve that so i dont have to run that bash script anymore?

---

