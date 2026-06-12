---
title: "changing glib version"
date: 2009-12-20
forum: General Help
---

### Post by PanzerMKZ on 2009-12-20
Ok I have a machine that I want to install a program on when I configure I get this.

checking for GLIB - version >= 2.6.0...
*** 'pkg-config --modversion glib-2.0' returned 2.22.3, but GLIB (2.12.11)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
no

*** If you don't have GLIB, you can get it from [ftp://ftp.gtk.org/pub/glib/](ftp://ftp.gtk.org/pub/glib/)
*** We recommend you get the latest stable GLIB 2 version.
*** Compile and install it, and make sure pkg-config finds it,
*** by adding the path where the .pc file is located to PKG_CONFIG_PATH

I would like to know how to change the glib version to the latest one without installing anything using apt-get or synaptic.  This machine is not connected to the net.

Thanks

Panzer

---

### Post by FearfulJesuit on 2009-12-20
I am unsure as to what your problem is but if I were to venture a guess I would say that your path for Glib is messed up and it's picking up the old one. Good thing is you can fix this without the net. But there are things I need to know. 

Do you have the most recent glib version installed via synaptic or did you install it yourself? If you did, give me the directory location of where it is installed. You will have to reset the LD_LIBRARY_PATH variable so that it locates the newest version of glib.

---

### Post by PanzerMKZ on 2009-12-20
I installed it myself as I don't have net connection on this machine.

I did configure make and make install with no other options of glib.


Panzer

---

### Post by FearfulJesuit on 2009-12-20
Let me know your directory where you installed glib. But here's what you want to do to fix that. 

```
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/wherever glib is/
ldconfig

```

You want to look for the glib-2.XX folder and find the header file (blah blah.h). That header file will then direct whatever program to the glib libraries.

---

### Post by PanzerMKZ on 2009-12-20
~/glib/glib-2.22.3/

Like I said I just did 
config
make 
make install


Is there a command I can use to check exactly where I installed glib?

Panzer

---

### Post by FearfulJesuit on 2009-12-20
Let me see if I'm understanding you correctly:
1st: You are trying to install a program that use glib, correct?
2nd: The program you're trying to install is trying to use glib but the installed version is too old.
3rd: So you went ahead and tried to install the new version of glib.
4th: Glib installed fine but the program you're trying to install can't find the new Glib. 
5th: That is exactly why I gave you the code for changing the LD_LIBRARY_PATH for Glib. This should help the program you want to install find the Glib path. 

Is this a little bit clearer? I apologize for the poor explanation.:)

If this is not the problem, can you explain it again?:-P

---

### Post by PanzerMKZ on 2009-12-20
yes.  That is pretty much it on the head.  I have run the command to point to the new glib and that is a no go.


Panzer

---

### Post by FearfulJesuit on 2009-12-20
What are the contents of the folder ~/glib-2.22.3/?

---

### Post by PanzerMKZ on 2009-12-20
~/glib/glib-2.22.3$ ls
acglib.m4                       glib-gettextize.in
acinclude.m4                    glib-zip
aclocal.m4                      glib-zip.in
AUTHORS                         gmodule
autogen.sh                      gmodule-2.0.pc
build                           gmodule-2.0.pc.in
ChangeLog                       gmodule-2.0-uninstalled.pc
ChangeLog.pre-1-2               gmodule-2.0-uninstalled.pc.in
ChangeLog.pre-2-0               gmodule-export-2.0.pc
ChangeLog.pre-2-10              gmodule-export-2.0.pc.in
ChangeLog.pre-2-12              gmodule-no-export-2.0.pc
ChangeLog.pre-2-14              gmodule-no-export-2.0.pc.in
ChangeLog.pre-2-16              gmodule-no-export-2.0-uninstalled.pc
ChangeLog.pre-2-18              gmodule-no-export-2.0-uninstalled.pc.in
ChangeLog.pre-2-2               gobject
ChangeLog.pre-2-20              gobject-2.0.pc
ChangeLog.pre-2-4               gobject-2.0.pc.in
ChangeLog.pre-2-6               gobject-2.0-uninstalled.pc
ChangeLog.pre-2-8               gobject-2.0-uninstalled.pc.in
compile                         gthread
config.guess                    gthread-2.0.pc
config.h                        gthread-2.0.pc.in
config.h.in                     gthread-2.0-uninstalled.pc
config.h.win32                  gthread-2.0-uninstalled.pc.in
config.h.win32.in               gtk-doc.make
config.log                      HACKING
config.lt                       INSTALL
config.status                   INSTALL.in
config.sub                      install-sh
configure                       libtool
configure.in                    ltmain.sh
COPYING                         m4macros
depcomp                         MAINTAINERS
docs                            Makefile
gio                             Makefile.am
gio-2.0.pc                      Makefile.decl
gio-2.0.pc.in                   Makefile.in
gio-2.0-uninstalled.pc          makefile.msc
gio-2.0-uninstalled.pc.in       missing
gio-unix-2.0.pc                 mkinstalldirs
gio-unix-2.0.pc.in              msvc_recommended_pragmas.h
gio-unix-2.0-uninstalled.pc     NEWS
gio-unix-2.0-uninstalled.pc.in  NEWS.pre-1-3
glib                            po
glib-2.0.pc                     README
glib-2.0.pc.in                  README.commits
glib-2.0-uninstalled.pc         README.in
glib-2.0-uninstalled.pc.in      README.win32
glibconfig.h                    sanity_check
glibconfig.h.win32              stamp-gc-h
glibconfig.h.win32.in           stamp-h1
glib-gettextize                 tests


Panzer

---

### Post by FearfulJesuit on 2009-12-20
Panzer,
I don't know why I didn't think of this earlier. This should work but I'm not entirely sure.

```

sudo ./configure --prefix=/usr
make
make install

```

But before you do this, go to synaptic and uninstall the old glib. Let me know if this works.

---

### Post by PanzerMKZ on 2009-12-20
Yes that got me further thanks.  now I need ncurses-devel package.


Panzer

---

### Post by PanzerMKZ on 2009-12-20
Thanks after your final post and a quick ncurses install I am all set.  


Panzer

---

### Post by FearfulJesuit on 2009-12-20
Woot. Can you edit topic and put [SOLVED] infront. People have this issue all the time and should be able to find it easier.

---

### Post by Agent ME on 2009-12-20
> **FearfulJesuit said:**
> Panzer,
I don't know why I didn't think of this earlier. This should work but I'm not entirely sure.

```

sudo ./configure --prefix=/usr
make
make install

```

But before you do this, go to synaptic and uninstall the old glib. Let me know if this works.
The "make install" step needs to have sudo, not the "./configure" step.

---

