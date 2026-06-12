---
title: "Glib and Gtk Problem"
date: 2005-02-04
forum: General Help
---

### Post by TheCondor on 2005-02-04
Hello everybody  :D 

Im relatively new to linux, and especially to Ubuntu, I just installed it yesterday and I must say its  A M A Z I N G !!

I like it very much so far and I reckon its going to be my distro from now and on. So easy and fast. Yet stable and good looking  8-) 

However, Im having a problem Im afraid I cant seem to find out how to solve it, and I havent done anything because I didnt wanna mess up.

Im using Lopster in all my computers, for remote administration and for filesharing in my opennap server. Its the number 1 app I use all the time, and its very essential to me.

I got the source in order to compile it, but it asked for gtk. Gtk asked for glib, I got glib 2.10 and installed it. Going fine so far. ( btw, i looooove the console  :D  )

When I tried to install gtk 1.2 version ( thats what lopster needs, I read on their site that it can be installed and be functionable along with other-later versions of glib ) the terminal gave me this : 


checking for glib-config... /usr/local/bin/glib-config
checking for GLIB - version >= 1.2.0...
*** 'glib-config --version' returned 1.2.9, but GLIB (1.2.10)
*** was found! If glib-config was correct, then it is best
*** to remove the old version of GLIB. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If glib-config was wrong, set the environment variable GLIB_CONFIG
*** to point to the correct copy of glib-config, and remove the file config.cache
*** before re-running configure
no
configure: error:
*** GLIB 1.2.0 or better is required. The latest version of GLIB
*** is always available from [ftp://ftp.gtk.org/](ftp://ftp.gtk.org/).

I understand that something is wrong with glib and its versions that are installed on my system, thats what Im assuming at least.

Since I dont have enough knowledge for this, could someone help me out? Its something I really wanna have working and I know I will do sooner or later, but I need someone's help to guide me through this cos Im a bit confused :confused: 

I browsed the forum for such a problem and saw a thread about glib and gtk but wasnt related to my problem. 

Id appreciate some help, thanks in advance for reading this post.

Also, I must say thanks to all the people here at this forum, and all the people working for this distribution. Its a neat piece of art, lovely work indeed. Keep up the good work folks

---

### Post by TheCondor on 2005-02-05
Well lol it seems noone knew about it... I sorted it anyway, I have two versions of glib installed hence all the mess. I just removed the older one and it was all fine after that   :-)

---

### Post by granite230 on 2005-04-04
So now I get this message while trying to update GAIM 1.0.0 to 1.2.1:

checking for GLIB - version >= 2.0.0...
*** 'pkg-config --modversion glib-2.0' returned 2.2.3, but GLIB (2.4.7)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
no
configure: error:
*** GLib 2.0 is required to build Gaim; please make sure you have the GLib
*** development headers installed. The latest version of GLib is
*** always available at [http://www.gtk.org/](http://www.gtk.org/).
granite@granite:~/gaim-1.2.1 $ locate libGL
warning: locate: warning: database /var/lib/slocate/slocate.db' is more than 8 days old

I checked Synaptic Package Manager and I see:

dbus-glib-1 (0.22-1ubuntu2)

libglib1.2 (1.2.10-9)
libglib1.2-dev (1.2.10-9)

libglib2.0-0 (2.4.7-0ubuntu2)
libglib2.0-data (2.4.7-0ubuntu2)
libglib2.0-dev (2.4.7-0ubuntu2)

so... I'm a n00b here but my guess is that I have the same problem you had.
Is it safe to delete libglib1.2 (1.2.10-9) and libglib1.2-dev (1.2.10-9)? I assume this is the older version and libglib2.0-0 (2.4.7-0ubuntu2) etc is the latest version?

If I try to delete it I get this message:

'the chosen action also affects other packages. The changes are required in order to proceed'
amule
libglib1.2-dev
libgtk1.2
libgtk1.2-dev
libwxgtk2.4
nerolinux
nvidia-glx-dev
xmms

Of course I want to keep these programs up and running so I wanna make sure I don't delete the wrong stuff here and mess up my system. Is it safe to delete 
libglib1.2 (1.2.10-9) and libglib1.2-dev (1.2.10-9)??
Is this what you did to fix the problem?

---

### Post by SaxmanTy on 2006-06-04
I'm actually having the same problem.  All I want to do is install the new version of rhythmbox, so that I can edit the tags for my music files.  I downloaded the source, and did ./configure.  And I had found that this new version needs a newer version of Gtk.  So I downloaded that, ran ./configure and Gtk needs the newer versions of glib, atk, pango, cairo.  I started with glib-2.8.6, and had no trouble compiling it.  But when I goto atk.1.10.3, I get the error message that these guys have been getting.  There are two versions of glib.  It suggest to remove the older version of glib, but when I go to synaptic to do that, it tells me that in order to remove it, it'll have to remove a HUGE list of apps, including Gaim, Ubuntu-desktop, and some others that I know I use, or know might screw up the system! Has anyone figured this out?  Or does anyone know how I can simply install the updated version of rhythmbox so that I don't have to go though all this mess?  By the way, I did get the deb file for the new rhythmbox, and synaptic tells me that it's broken, and yep, the dependencies that it needs are the ones I'm trying to install.  I would really appreciate any help!

---

### Post by MajesticHazard on 2007-08-04
I'm also having the exact same problem as above, but when trying to install the program scatterchat.

---

