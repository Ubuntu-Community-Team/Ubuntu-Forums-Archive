---
title: "Unable to install gtk+-2.18.7"
date: 2010-02-21
forum: General Help
---

### Post by dandeliondream on 2010-02-21
Help what's wrong?


user@ubuntu:~/gtk+-2.18.7$ ./configure --prefix=/opt/gtk

.
.
.checking whether gcc and cc understand -c and -o together... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking whether make sets $(MAKE)... (cached) yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for BASE_DEPENDENCIES... configure: error: Package requirements (glib-2.0 >= 2.21.3    atk >= 1.13.0    pango >= 1.20    cairo >= 1.6) were not met:

Requested 'glib-2.0 >= 2.21.3' but version of GLib is 2.20.1
No package 'pango' found
No package 'cairo' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables BASE_DEPENDENCIES_CFLAGS
and BASE_DEPENDENCIES_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

---

### Post by RedSquirrel on 2010-02-21
**Requested 'glib-2.0 >= 2.21.3' but version of GLib is 2.20.1**

At the very least, your glib is too old.

May I ask why you are compiling a newer version of GTK+ on Ubuntu?

In my opinion, if you want or need a newer version, it would be easier to install a different linux distribution that has an updated GTK+ package or to use a source-based distribution where you can pick the version you want to compile.

I don't think building and installing GTK+ on a binary distribution such as Ubuntu is going to be much fun.

---

### Post by dandeliondream on 2010-02-21
I'm trying to create a GUI using c++ and mySQL so i decide to try out GTK+.
Do you have any recommendation as to what program can do drag and drop GUI using c++ with mySQL?
 
> **RedSquirrel said:**
> **Requested 'glib-2.0 >= 2.21.3' but version of GLib is 2.20.1**
 
At the very least, your glib is too old.
 
May I ask why you are compiling a newer version of GTK+ on Ubuntu?
 
In my opinion, if you want or need a newer version, it would be easier to install a different linux distribution that has an updated GTK+ package or to use a source-based distribution where you can pick the version you want to compile.
 
I don't think building and installing GTK+ on a binary distribution such as Ubuntu is going to be much fun.

---

### Post by RedSquirrel on 2010-02-23
> **dandeliondream said:**
> I'm trying to create a GUI using c++ and mySQL so i decide to try out GTK+.

If you want to use GTK+, you don't have to compile it yourself. You may  have to install a few development packages (libgtk2.0-dev, etc.) from  the Ubuntu repositories, however.



> **dandeliondream said:**
> Do you have any recommendation as to what program can do drag and drop GUI using c++ with mySQL?

If you haven't already done so, you could ask this question regarding GUI development on the [Programming Talk]("http://ubuntuforums.org/forumdisplay.php?f=39") sub-forum.




(Edit: Broke the quotation of the OP's post into two pieces for clarity.)

---

