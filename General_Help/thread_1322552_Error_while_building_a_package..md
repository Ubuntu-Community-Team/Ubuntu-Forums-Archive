---
title: "Error while building a package."
date: 2009-11-11
forum: General Help
---

### Post by prasanthp on 2009-11-11
While building a package from source i got this error..
The command i used is :
root@boss[marquee-plugins-0.22]#dpkg-buildpackage -rfakeroot -us -uc -sa


Can any one plz sort out what i sthe error



 gcc -DHAVE_CONFIG_H -I. -I.. -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -D_REENTRANT -I/usr/include/libhildondesktop -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/include/libxml2 -I/usr/include/dbus-1.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/lib/dbus-1.0/include -D_REENTRANT -DORBIT2=1 -pthread -I/usr/include/libhildonwm -I/usr/include/hildon-1 -I/usr/include/libxml2 -I/usr/include/gconf/2 -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/orbit-2.0 -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -Wall -g -O2 -Wall -ansi -Wmissing-prototypes -Wmissing-declarations -std=c99 -rdynamic -MT drop-down-menu-plugin.lo -MD -MP -MF .deps/drop-down-menu-plugin.Tpo -c drop-down-menu-plugin.c  -fPIC -DPIC -o .libs/drop-down-menu-plugin.o
drop-down-menu-plugin.c: In function 'on_clicked':
drop-down-menu-plugin.c:288: error: 'HD_ATOM_MB_GRAB_TRANSFER' undeclared (first use in this function)
drop-down-menu-plugin.c:288: error: (Each undeclared identifier is reported only once
drop-down-menu-plugin.c:288: error: for each function it appears in.)
drop-down-menu-plugin.c:290: warning: implicit declaration of function 'hd_wm_window_get_display'
drop-down-menu-plugin.c:290: warning: assignment makes pointer from integer without a cast
drop-down-menu-plugin.c: In function 'drop_down_menu_plugin_class_init':
drop-down-menu-plugin.c:442: warning: unused variable 'item_class'
make[3]: *** [drop-down-menu-plugin.lo] Error 1
make[3]: Leaving directory `/root/Desktop/test/marquee-plugins/marquee-plugins-0.22/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/root/Desktop/test/marquee-plugins/marquee-plugins-0.22'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/root/Desktop/test/marquee-plugins/marquee-plugins-0.22'
make: *** [build-stamp] Error 2
dpkg-buildpackage: failure: debian/rules build gave error exit status 2

---

