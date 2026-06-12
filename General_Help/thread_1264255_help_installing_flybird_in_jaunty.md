---
title: "help installing flybird in jaunty"
date: 2009-09-12
forum: General Help
---

### Post by strungoutfan78 on 2009-09-12
I need some assistance installing Flybird in xubuntu jaunty.  I've installed all dependencies except for one.  For some reason, whether I use the autopackage version or the tarball, it complains that i don't have 'libgnomeui' or some derivative of it installed on my system.  I have installed everything with 'libgnomeui' in it that I can find through synaptic and still no luck.  Has anyone else had success with this?  If so please help.  Here is the output when I try to install using scons in the terminal:
```
neil@neil-desktop:~/downloads/flybird$ scons
scons: Reading SConscript files ...

scons: warning: The Options class is deprecated; use the Variables class instead.
File "/home/neil/downloads/flybird/SConstruct", line 9, in <module>

scons: warning: The BoolOption() function is deprecated; use the BoolVariable() function instead.
File "/home/neil/downloads/flybird/SConstruct", line 12, in <module>

scons: warning: The EnumOption() function is deprecated; use the EnumVariable() function instead.
File "/home/neil/downloads/flybird/SConstruct", line 17, in <module>
scons: done reading SConscript files.
scons: Building targets ...
gcc -o src/accel.o -c -D_REENTRANT -DORBIT2=1 -pthread -pthread -I./ -g -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pango-1.0 -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/libgnomeui-2.0 -I/usr/include/libart-2.0 -I/usr/include/gconf/2 -I/usr/include/gnome-keyring-1 -I/usr/include/libgnome-2.0 -I/usr/include/libbonoboui-2.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/orbit-2.0 -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/include/libbonobo-2.0 -I/usr/include/bonobo-activation-2.0 -I/usr/include/libxml2 -I/usr/include/gail-1.0 -I/usr/include/eel-2 -I/usr/include/gnome-desktop-2.0 -I/usr/include/startup-notification-1.0 -Isrc src/accel.c
In file included from src/file-operations.h:25,
                 from src/accel.h:23,
                 from src/accel.c:22:
src/list.h:26:25: error: glade/glade.h: No such file or directory
In file included from src/directory.h:26,
                 from src/directory-factory.h:22,
                 from src/list-tabs.h:21,
                 from src/list.h:30,
                 from src/file-operations.h:25,
                 from src/accel.h:23,
                 from src/accel.c:22:
src/conf.h:39: error: expected ')' before '*' token
In file included from src/file-operations.h:25,
                 from src/accel.h:23,
                 from src/accel.c:22:
src/list.h:41: error: expected ')' before '*' token
In file included from src/accel.h:24,
                 from src/accel.c:22:
src/conf.h:39: error: expected ')' before '*' token
In file included from src/accel.c:22:
src/accel.h:28: error: expected declaration specifiers or '...' before 'GladeXML'
src/accel.h:40: error: expected ')' before '*' token
src/accel.h:43: error: expected ')' before '*' token
In file included from src/accel.c:28:
src/main-window.h:44: error: expected ')' before '*' token
src/main-window.h:46: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
src/accel.c:255: error: expected declaration specifiers or '...' before 'GladeXML'
src/accel.c: In function 'accel_init_accel_group':
src/accel.c:286: error: 'glade_xml' undeclared (first use in this function)
src/accel.c:286: error: (Each undeclared identifier is reported only once
src/accel.c:286: error: for each function it appears in.)
src/accel.c:287: warning: assignment makes pointer from integer without a cast
src/accel.c: At top level:
src/accel.c:312: error: expected declaration specifiers or '...' before 'GladeXML'
src/accel.c: In function 'accel_activate_group_for_widgets':
src/accel.c:329: error: 'glade_xml' undeclared (first use in this function)
src/accel.c:330: warning: assignment makes pointer from integer without a cast
src/accel.c: At top level:
src/accel.c:347: error: expected ')' before '*' token
src/accel.c:356: error: expected ')' before '*' token
src/accel.c:368: error: expected declaration specifiers or '...' before 'GladeXML'
src/accel.c: In function 'accel_init':
src/accel.c:372: error: 'glade_xml' undeclared (first use in this function)
src/accel.c:375: warning: passing argument 3 of 'accel_init_accel_group' makes integer from pointer without a cast
src/accel.c:375: error: too many arguments to function 'accel_init_accel_group'
src/accel.c:383: warning: passing argument 3 of 'accel_init_accel_group' makes integer from pointer without a cast
src/accel.c:383: error: too many arguments to function 'accel_init_accel_group'
src/accel.c: In function 'on_accel_search':
src/accel.c:535: warning: too few arguments for format
src/accel.c: In function 'on_accel_edit':
src/accel.c:591: warning: too few arguments for format
scons: *** [src/accel.o] Error 1
scons: building terminated because of errors.

```

And here is the response I get from autopackage:

```
Checking for required C library versions ... OK
Checking for GTK+ user interface toolkit ... OK
Checking for GConf Configuration Framework ... OK
Checking for GNOME User Interface Library ... failed
-------------------------------
Error: Could not find 'GNOME User Interface Library'. Try using the native package manager for Ubuntu 9.04 (apt-get) to install a package with similar name to 'libgnomeui'. 

Error: Unable to prepare package FlyBird.


```
Thanks.

---

### Post by strungoutfan78 on 2009-09-21
*bumpity bump*

---

