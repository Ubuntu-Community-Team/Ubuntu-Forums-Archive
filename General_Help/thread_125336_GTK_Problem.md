---
title: "GTK Problem"
date: 2006-02-03
forum: General Help
---

### Post by TheSource on 2006-02-03
I'm going through dependecy hell right now trying to install a program from source. I got a few sorted out but now I'm stuck on gtk+. It keeps spitting this out at me in terminal.

> 
checking for GLIB - version >= 2.4.0...
*** 'pkg-config --modversion glib-2.0' returned 2.9.5, but GLIB (2.8.3)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
no
configure: error:
*** GLIB 2.4.0 or better is required. The latest version of
*** GLIB is always available from [ftp://ftp.gtk.org/pub/gtk/](ftp://ftp.gtk.org/pub/gtk/).


---

### Post by bernardfrancois on 2006-02-04
The latest version of GLIB in my repositories here is 2.0... (package *libglib2.0-dev*).
You'll have to find the website of GLIB and download the sources... Or try to find a debian package (for example after adding the debian repositories to synaptic).

Or you can try to find an older version of the program you want to install from source...
Binary packages are mostly a few weeks to months behind...

---

### Post by hw-tph on 2006-02-04
Actually, the current version of glib2 (in Breezy) is 2.8.3:
```
hakan@devon:~$ apt-cache policy libglib2.0-0
libglib2.0-0:
  Installed: 2.8.3-0ubuntu1
  Candidate: 2.8.3-0ubuntu1
  Version table:
 *** 2.8.3-0ubuntu1 0
        500 http://se.archive.ubuntu.com breezy/main Packages
        100 /var/lib/dpkg/status
```

Oh, and you will want to install the libglib2.0-dev package to build software that depends on it.


Håkan

---

