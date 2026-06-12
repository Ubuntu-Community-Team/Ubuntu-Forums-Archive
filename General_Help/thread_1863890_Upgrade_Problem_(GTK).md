---
title: "Upgrade Problem (GTK)"
date: 2011-10-18
forum: General Help
---

### Post by LocallyCompact on 2011-10-18
Hello, I just upgraded to the new ubuntu and now I'm getting the following error when I try to build opencv:

[ 36%] Building CXX object modules/highgui/CMakeFiles/opencv_highgui.dir/src/window_gtk.o
In file included from /usr/include/gtk-2.0/gdk/gdkscreen.h:32:0,
                 from /usr/include/gtk-2.0/gdk/gdkapplaunchcontext.h:31,
                 from /usr/include/gtk-2.0/gdk/gdk.h:32,
                 from /usr/include/gtk-2.0/gtk/gtk.h:32,
                 from /home/dan/OpenCV-2.3.1/modules/highgui/src/window_gtk.cpp:48:
/usr/include/gtk-2.0/gdk/gdktypes.h:55:23: fatal error: gdkconfig.h: No such file or directory
compilation terminated.
make[2]: *** [modules/highgui/CMakeFiles/opencv_highgui.dir/src/window_gtk.o] Error 1
make[1]: *** [modules/highgui/CMakeFiles/opencv_highgui.dir/all] Error 2
make: *** [all] Error 2

Could use some help with this asap please.

---

