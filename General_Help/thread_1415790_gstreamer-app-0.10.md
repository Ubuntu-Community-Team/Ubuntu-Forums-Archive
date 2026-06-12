---
title: "gstreamer-app-0.10"
date: 2010-02-25
forum: General Help
---

### Post by 7raTEYdCql on 2010-02-25
I've been trying to install byzanz-0.2.1.
I have to install it from source, because of the unavailability of deb packages on the internet.  [http://ftp.gnome.org/pub/GNOME/sources/byzanz/0.2/](http://ftp.gnome.org/pub/GNOME/sources/byzanz/0.2/) During the ./configure, there are some package conflicts which i can't figure out.

The error i get, is, there is no package "gstreamer-app-0.10" found. I've searched the internet for a source file for the above, and haven't been able to find one. Can someone help me.

---

### Post by joshua.davies on 2010-04-19
I had a similar problem compiling "WebKit", and I fixed this by installing "gst-plugins-base".

---

### Post by johndoe32102002 on 2012-01-03
I have found this error in compiling the latest version of QT:
rc-4.8.0/mkspecs/linux-g++-64 -o Makefile.WebKit
Project ERROR: Package gstreamer-app-0.10 not found
make[1]: *** [WebCore/Makefile.WebKit] Error 2

When searching packages.ubuntu.com, no such package exists (also searched packages.debian.org).  Installing 'gst-plugins-base' did not fix the problem.

---

### Post by vsevik on 2012-02-22
I had this error trying to build qt.

This helped:
[http://superuser.com/questions/124943/how-can-i-resolve-gstreamer-dependencies-in-ubuntu](http://superuser.com/questions/124943/how-can-i-resolve-gstreamer-dependencies-in-ubuntu)

---

