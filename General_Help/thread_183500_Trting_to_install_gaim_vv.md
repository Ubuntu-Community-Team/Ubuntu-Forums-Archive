---
title: "Trting to install gaim vv"
date: 2006-05-28
forum: General Help
---

### Post by styven on 2006-05-28
Hi all,

Trying to install Gaim vv, have got this far and i see that i need Glib 2.0, have done an apt search and get all this, which one is the one i want.

checking for GLIB - version >= 2.0.0... no
*** Could not run GLIB test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occurred. This usually means GLIB is incorrectly installed.
configure: error:
*** GLib 2.0 is required to build Gaim; please make sure you have the GLib
*** development headers installed. The latest version of GLib is
*** always available at [http://www.gtk.org/](http://www.gtk.org/).
styven@edubuntu:~/gaim-vv-1.2.0$ sudo apt-get install glib2
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package glib2
styven@edubuntu:~/gaim-vv-1.2.0$ apt-cache search glib 2.0
ja-trans - Japanese gettext message files
libgetopt-java - GNU getopt - Java port
libglib2.0-cil - CLI binding for the GLib utility library 2.0, unstable version
libgnetwork1.0-0 - networking wrapper library using Glib/GObject
libgnetwork1.0-dev - networking wrapper library using Glib/GObject (development files)
libpolyp0-glib2.0 - Library for the polypaudio sound server
libpolyp0-glib2.0-dev - Library for the polypaudio sound server
libdb1-compat - The Berkeley database routines [glibc 2.0/2.1 compatibility]
libglib-perl - Perl interface to the GLib and GObject libraries
libglib2.0-0 - The GLib library of C routines
libglib2.0-0-dbg - The GLib libraries and debugging symbols
libglib2.0-data - Common files for GLib library
libglib2.0-dev - Development files for the GLib library
libglib2.0-doc - Documentation files for the GLib library
styven@edubuntu:~/gaim-vv-1.2.0$

I thank you in advance for your help..........steve.

---

### Post by tkjacobsen on 2006-05-28
if you just want a newer gaim: 
[http://mighmos.org/packages.php](http://mighmos.org/packages.php)


EDIT: sorry thought gaim vv was som newer version. Didn't realize it was a fork

---

### Post by jdkchem on 2006-05-28
Gaim 2.0 beta is available.  Is there an Ubuntu/Debian package available?

Yes, there is an Ubuntu package available at [http://mighmos.org/packages.php](http://mighmos.org/packages.php)

---

### Post by BatsotO on 2006-05-28
As aalternative, there is autopackege version of gaim-vv

[http://gaim-vv.sourceforge.net/](http://gaim-vv.sourceforge.net/)

---

### Post by styven on 2006-05-28
Hi, thanks for the responses so far...........

I tried the autopackage, upon clickong on it, i got error message,

gedit was not able to automatically detect the character coding. Please, check that you are not trying to open a binary file and try again selecting a character coding in the 'Open File...' (or 'Open Location') dialogue.

It seems i had to change the permissions and tick "execute" to run the file.

now things seem to be happening, will update later.

---

### Post by styven on 2006-05-28
update................

Extracting files: [100%]
Copying files to /usr/lib/gstreamer-0.8
Error: Package Jpeg2000 Gstreamer Plugin could not be installed.

hmmm.......

---

### Post by styven on 2006-05-28
Ok.............didn't need gstreamer0.8 anyway.

Have installed gaim vv using the auto package (if only all software installed this way), only to find out that it does not suppport webcams for MSN accounts.....................will happen at some point.

Thanks everyone Steve.

---

