---
title: "how to upgrade/update GTK+ to the latest version?"
date: 2011-10-14
forum: General Help
---

### Post by jinjin on 2011-10-14
hello all, i'm new to gtk+.  i'm running on ubuntu 10.04 and my computer  has gtk+  but the version is 2.20.   the latest version of gtk+ 2 is  2.24.   i don't want to upgrade to gtk+ 3 but i do want to upgrade the  version to gtk+ 2.24.   how can i do this? i read went on the site and  read how to install gtk + 2.24 but do i really need to go through all  those steps just to update the gtk+ to 2.24? isn't there an easy way to  upgrade via terminal or synpatic package manager or something else?

also,  someone told me that if i want to use c++, i have to get a c++ binding ?   do i really need to?  i mean if i use a C++ function like cout instead  of C printf, you're telling me that it won't work?

i'm new to this so sorry if i asked stupid questions. please help me.

---

### Post by crdlb on 2011-10-14
What do you need Gtk 2.24 for? I would stick with the version included in 10.04. If you're going to write something using Gtk, you'll probably want it to work on the current ubuntu LTS anyway.  And yes, you can use Gtk's C API from C++, but gtkmm is a nicer API.

If you have any more questions about programming with Gtk (as opposed to installation of Gtk on Ubuntu), you should create a thread in [Programming Talk]("http://ubuntuforums.org/forumdisplay.php?f=39").

---

### Post by jinjin on 2011-10-14
> **crdlb said:**
> What do you need Gtk 2.24 for? I would stick with the version included in 10.04. If you're going to write something using Gtk, you'll probably want it to work on the current ubuntu LTS anyway.  And yes, you can use Gtk's C API from C++, but gtkmm is a nicer API.

If you have any more questions about programming with Gtk (as opposed to installation of Gtk on Ubuntu), you should create a thread in [Programming Talk]("http://ubuntuforums.org/forumdisplay.php?f=39").

i need it cause i want the latest version since 2.24 is what we are using in class but i don't want a complete overhaul like gtk 3.  but that's going off topic, i still need my question answered so BUMP!

---

### Post by crdlb on 2011-10-14
> **jinjin said:**
> i need it cause i want the latest version since 2.24 is what we are using in class but i don't want a complete overhaul like gtk 3.  but that's going off topic, i still need my question answered so BUMP!

Gtk 2 is binary-compatible so that anything compiled on 2.20 will work on 2.24 and vice versa (as long as you don't use any new API). If you're sure you need to do this, run: ```
sudo apt-get build-dep libgtk2.0-0
``` That will install everything needed to build gtk2 from source. Then download gtk 2.24 from gtk.org and ./configure, make, etc. it. By default, it would install to /usr/local, where it will override the default gtk installation, but not overwrite it. Keep the source directory around so that you can 'sudo make uninstall' later if needed. It would be even better to install it somewhere in your home directory or into /opt/, but that can be a little tricky.

---

### Post by jinjin on 2011-10-14
> **crdlb said:**
> Gtk 2 is binary-compatible so that anything compiled on 2.20 will work on 2.24 and vice versa (as long as you don't use any new API). If you're sure you need to do this, run: ```
sudo apt-get build-dep libgtk2.0-0
``` That will install everything needed to build gtk2 from source. Then download gtk 2.24 from gtk.org and ./configure, make, etc. it. By default, it would install to /usr/local, where it will override the default gtk installation, but not overwrite it. Keep the source directory around so that you can 'sudo make uninstall' later if needed. It would be even better to install it somewhere in your home directory or into /opt/, but that can be a little tricky.

ok thanks for help, i appreciate it, i'll try that.  but i have anotehr question, wouldn't i need to do the same thing for the GTK dependencies such as glib and pango and update them each individually before i can update gtk to 2.24?

---

