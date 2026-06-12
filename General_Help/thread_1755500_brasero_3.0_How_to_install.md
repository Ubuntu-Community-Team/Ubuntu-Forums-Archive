---
title: "brasero 3.0 How to install?"
date: 2011-05-11
forum: General Help
---

### Post by oklokl on 2011-05-11
ubuntu 10.10 M

[http://ftp.acc.umu.se/pub/GNOME/sources/brasero/](http://ftp.acc.umu.se/pub/GNOME/sources/brasero/)
I want updates 2.32=>3.0..

apt-get install libglib2.0-bin  libglib2.0-dev gnome-shell libgstreamer0.10-dev libgstreamer-plugins-base0.10-dev libgstreamer*

brasero-3.0.0
./configure
.............................
checking for BRASERO_GIO... no
[COLOR=Red]configure: error: Package requirements (    gio-2.0 >= 2.28.0) were not met:

Requested 'gio-2.0 >= 2.28.0' but version of GIO is 2.26.1[/COLOR]

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables BRASERO_GIO_CFLAGS
and BRASERO_GIO_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

---

### Post by Joe of loath on 2011-05-11
Because brasero 3 is part of Gnome 3, you'd have to install most of the Gnome 3 dependencies, which would break your current Gnome 2 install. It's not really possible without upgrading to Gnome 3.

---

### Post by oklokl on 2011-05-11
Thank you very much
 Thanks in friendly

---

