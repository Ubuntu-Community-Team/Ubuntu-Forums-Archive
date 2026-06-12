---
title: "GTK+ and wxwidgets install"
date: 2010-01-09
forum: General Help
---

### Post by padeco on 2010-01-09
hi there,

i have installed ubuntu 9.10. i am trying to install a program that requires wxwidgets. i can not install wxwidgets. i have followed the website hints etc.

mkdir build_gtk
cd build_gtk
sudo ../configure --with-gtk

all goes well... until

sudo make, and i get the following error:

:~/programs/wxWidgets-2.8.10/build_gtk$ sudo make
/home/user/programs/wxWidgets-2.8.10/build_gtk/bk-deps g++ -c -o coredll_gtk_gsockgtk.o -I./.pch/wxprec_coredll -D__WXGTK__     -I../src/tiff       -DWXUSINGDLL -DWXMAKINGDLL_CORE -DwxUSE_BASE=0 -fPIC -DPIC -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES -D__WXDEBUG__ -I/home/bull/programs/wxWidgets-2.8.10/build_gtk/lib/wx/include/gtk2-ansi-debug-2.8 -I../include -D_REENTRANT -pthread -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -DWX_PRECOMP -pthread -Wall -Wundef -Wno-ctor-dtor-privacy -g -O0 -D_REENTRANT -I/usr/include/libgnomeprintui-2.2 -I/usr/include/libgnomeprint-2.2 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/libart-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2 -I/usr/include/pango-1.0 -I/usr/include/gail-1.0 -I/usr/include/gtk-2.0 -I/usr/include/freetype2 -I/usr/include/atk-1.0 -I/usr/lib/gtk-2.0/include -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/include/directfb -I/usr/include/libpng12 ../src/gtk/gsockgtk.cpp
In file included from ../src/gtk/gsockgtk.cpp:21:
../include/wx/gsocket.h:40: error: using typedef-name ‘GSocket’ after ‘class’
/usr/include/glib-2.0/gio/giotypes.h:120: error: ‘GSocket’ has a previous declaration here
In file included from ../include/wx/gsocket.h:179,
                 from ../src/gtk/gsockgtk.cpp:21:
../include/wx/unix/gsockunx.h:40: error: using typedef-name ‘GSocket’ after ‘class’
/usr/include/glib-2.0/gio/giotypes.h:120: error: ‘GSocket’ has a previous declaration here
../src/gtk/gsockgtk.cpp: In function ‘void _GSocket_GDK_Input(void*, gint, GdkInputCondition)’:
../src/gtk/gsockgtk.cpp:34: error: ‘struct _GSocket’ has no member named ‘Detected_Read’
../src/gtk/gsockgtk.cpp:36: error: ‘struct _GSocket’ has no member named ‘Detected_Write’
../src/gtk/gsockgtk.cpp: In member function ‘virtual bool GSocketGUIFunctionsTableConcrete::Init_Socket(GSocket*)’:
../src/gtk/gsockgtk.cpp:56: error: ‘struct _GSocket’ has no member named ‘m_gui_dependent’
../src/gtk/gsockgtk.cpp:57: error: ‘struct _GSocket’ has no member named ‘m_gui_dependent’
../src/gtk/gsockgtk.cpp: In member function ‘virtual void GSocketGUIFunctionsTableConcrete::Destroy_Socket(GSocket*)’:
../src/gtk/gsockgtk.cpp:67: error: ‘struct _GSocket’ has no member named ‘m_gui_dependent’
../src/gtk/gsockgtk.cpp: In member function ‘virtual void GSocketGUIFunctionsTableConcrete::Install_Callback(GSocket*, GSocketEvent)’:
../src/gtk/gsockgtk.cpp:72: error: ‘struct _GSocket’ has no member named ‘m_gui_dependent’
../src/gtk/gsockgtk.cpp:75: error: ‘struct _GSocket’ has no member named ‘m_fd’
../src/gtk/gsockgtk.cpp:83: error: ‘struct _GSocket’ has no member named ‘m_server’
../src/gtk/gsockgtk.cpp:90: error: ‘struct _GSocket’ has no member named ‘m_fd’
../src/gtk/gsockgtk.cpp: In member function ‘virtual void GSocketGUIFunctionsTableConcrete::Uninstall_Callback(GSocket*, GSocketEvent)’:
../src/gtk/gsockgtk.cpp:98: error: ‘struct _GSocket’ has no member named ‘m_gui_dependent’
../src/gtk/gsockgtk.cpp:108: error: ‘struct _GSocket’ has no member named ‘m_server’
make: *** [coredll_gtk_gsockgtk.o] Error 1

many thanks,

padeco

---

### Post by vadz on 2010-01-10
This is a known (and already fixed) [bug]("https://bugs.launchpad.net/ubuntu/+source/wxwidgets2.8/+bug/423845"). You should apply the patch mentioned there manually until the next version is released.

---

