---
title: "gtk+ 3.0 compile problem"
date: 2011-03-17
forum: General Help
---

### Post by parag14 on 2011-03-17
i am getting an error in compiling gtk+ 3.0 package.
when i do ./configure, i get the following error in the end:

configure: error: Package requirements (glib-2.0 >= 2.28.0    atk >= 1.30    pango >= 1.24.0    cairo >= 1.10.0    cairo-gobject >= 1.10.0    gdk-pixbuf-2.0 >= 2.22.0) were not met:

No package 'atk' found
No package 'cairo' found
No package 'cairo-gobject' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables BASE_DEPENDENCIES_CFLAGS
and BASE_DEPENDENCIES_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

i have installed the packages cairo-gobject2 and libatk1.0-0
also, i have tried those solutions suggesting that i export PKG_CONFIG_PATH as /usr/local/lib/pkgconfig:usr/bin/pkg-config, but to no avail.

please someone suggest what should i do??

---

### Post by cap10Ibraim on 2011-03-17
post it in the Programming Talk section 
[http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39) 
maybe someone will help you there

---

### Post by andrewthomas on 2011-03-17
> **parag14 said:**
> i am getting an error in compiling gtk+ 3.0 package.
when i do ./configure, i get the following error in the end:

configure: error: Package requirements (glib-2.0 >= 2.28.0    atk >= 1.30    pango >= 1.24.0    cairo >= 1.10.0    cairo-gobject >= 1.10.0    gdk-pixbuf-2.0 >= 2.22.0) were not met:

No package 'atk' found
No package 'cairo' found
No package 'cairo-gobject' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables BASE_DEPENDENCIES_CFLAGS
and BASE_DEPENDENCIES_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

i have installed the packages cairo-gobject2 and libatk1.0-0
also, i have tried those solutions suggesting that i export PKG_CONFIG_PATH as /usr/local/lib/pkgconfig:usr/bin/pkg-config, but to no avail.

please someone suggest what should i do??
You need the -dev packages installed

---

