---
title: "Help Installing GNOME Alarm Applet 0.1.2"
date: 2010-04-26
forum: General Help
---

### Post by fipem on 2010-04-26
Hey there guys, I'm trying to use amarok as an alarm, reading a lot I found out that I need this applet in order to do such thing, GNOME Alarm Applet 0.1.2, but I'm unable to do such since it gives me this, I've download this applet from here [http://linux.softpedia.com/progDownload/GNOME-Alarm-Applet-Download-33717.html](http://linux.softpedia.com/progDownload/GNOME-Alarm-Applet-Download-33717.html) in a tar.gz format, I unpack it and the tryed to run ./configure and gives me this, when I try to do make it says that there isn't any make file, even tho there IS a makefile.ini in the folder...

fipem@Fipem:~/Descargas/alarm-applet-0.1.2$ ls
aclocal.m4  ChangeLog    configure     depcomp     m4           missing
src
AUTHORS     config.h.in  configure.ac  INSTALL     Makefile.am  NEWS
autogen.sh  config.log   COPYING       install-sh  Makefile.in  README
fipem@Fipem:~/Descargas/alarm-applet-0.1.2$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles...
no
./configure: line 2313: GNOME_INIT: command not found
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.19... yes
checking what warning flags to pass to the C compiler... -Wall
-Wmissing-prototypes
checking what language compliance flags to pass to the C compiler...
checking for GLIB... configure: error: Package requirements (glib-2.0 >=
2.13.0 gobject-2.0 >= 2.13.0) were not met:

No package 'glib-2.0' found
No package 'gobject-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GLIB_CFLAGS
and GLIB_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

fipem@Fipem:~/Descargas/alarm-applet-0.1.2$


Could anyone please explain me what am I doing wrong here?
Is there any .dev package to avoid compiling this?

Thanks a lot for the help...

P.S. I'm quite noob, so please any explanation in the easiest possible way! THANKS AGAIN!!!

---

### Post by stinkeye on 2010-04-26
That's on old version.
The name has changed to alarm-clock-applet.
Do a search in synaptic package manager for it.
 
For a more recent release, go to this page and, if your on karmic or later,
scroll down to downloads and just click on the green box.

If you want updates and bug fixes for alarm-clock-applet
click on the link for the ppa and follow the instruction for adding the ppa to your sources list.
This is the best way to install programs which are not in the ubuntu repositories (or you want the latest version)
because it will automatically be updated to newer versions.

[**_[COLOR="DarkRed"]http://alarm-clock.pseudoberries.com/[/COLOR]_**]("http://alarm-clock.pseudoberries.com/")

---

