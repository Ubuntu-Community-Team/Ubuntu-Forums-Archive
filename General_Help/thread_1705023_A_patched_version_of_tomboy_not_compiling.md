---
title: "A patched version of tomboy not compiling"
date: 2011-03-11
forum: General Help
---

### Post by nmvictor on 2011-03-11
I grabbed a pacthed version of tomboy from [this]("https://github.com/gz/tomboy") in order to use tomboy Task manager addin created by the same developers I guess. Well I managed with the ```
./autogen.sh
``` and  ```
./configure
``` scripts until I came up with a valid make file. I later ran ```
make 
``` but produced the following ```

make  all-recursive
make[1]: Entering directory `/home/nmvictor/Desktop/gz-tomboy-e753a55'
Making all in data
make[2]: Entering directory `/home/nmvictor/Desktop/gz-tomboy-e753a55/data'
Making all in icons
make[3]: Entering directory `/home/nmvictor/Desktop/gz-tomboy-e753a55/data/icons'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/nmvictor/Desktop/gz-tomboy-e753a55/data/icons'
make[3]: Entering directory `/home/nmvictor/Desktop/gz-tomboy-e753a55/data'
sed -e "s|\@bindir\@|/usr/local/bin|g"	\
	    -e "s|\@wrapper\@|tomboy|g"		\
	    < org.gnome.Tomboy.service.in > org.gnome.Tomboy.service
sed -e "s|\@bindir\@|/usr/local/bin|g"	\
	    -e "s|\@wrapper\@|tomboy-panel|g"		\
	    < GNOME_TomboyApplet.server.in.in > GNOME_TomboyApplet.server.in
LC_ALL=C /usr/bin/intltool-merge -o -u -c ../po/.intltool-merge-cache ../po GNOME_TomboyApplet.server.in GNOME_TomboyApplet.server
Found cached translation database
Merging translations into GNOME_TomboyApplet.server.
make[3]: Leaving directory `/home/nmvictor/Desktop/gz-tomboy-e753a55/data'
make[2]: Leaving directory `/home/nmvictor/Desktop/gz-tomboy-e753a55/data'
Making all in libtomboy
make[2]: Entering directory `/home/nmvictor/Desktop/gz-tomboy-e753a55/libtomboy'
/bin/bash ../libtool  --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I.. -I.. -DG_LOG_DOMAIN=\"libtomboy\" -DEGG_COMPILATION -DGTK_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DG_DISABLE_DEPRECATED -pthread -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/gio-unix-2.0/ -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/atk-1.0   -DHAS_GTK_2_20    -g -O2 -MT libtomboy_la-tomboykeybinder.lo -MD -MP -MF .deps/libtomboy_la-tomboykeybinder.Tpo -c -o libtomboy_la-tomboykeybinder.lo `test -f 'tomboykeybinder.c' || echo './'`tomboykeybinder.c
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I.. -I.. -DG_LOG_DOMAIN=\"libtomboy\" -DEGG_COMPILATION -DGTK_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DG_DISABLE_DEPRECATED -pthread -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/gio-unix-2.0/ -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/atk-1.0 -DHAS_GTK_2_20 -g -O2 -MT libtomboy_la-tomboykeybinder.lo -MD -MP -MF .deps/libtomboy_la-tomboykeybinder.Tpo -c tomboykeybinder.c  -fPIC -DPIC -o .libs/libtomboy_la-tomboykeybinder.o
tomboykeybinder.c: In function ‘tomboy_keybinder_is_modifier’:
tomboykeybinder.c:316: error: ‘gdk_display’ undeclared (first use in this function)
tomboykeybinder.c:316: error: (Each undeclared identifier is reported only once
tomboykeybinder.c:316: error: for each function it appears in.)
make[2]: *** [libtomboy_la-tomboykeybinder.lo] Error 1
make[1]: *** [all-recursive] Error 1
make: *** [all] Error 2
make[2]: Leaving directory `/home/nmvictor/Desktop/gz-tomboy-e753a55/libtomboy'
make[1]: Leaving directory `/home/nmvictor/Desktop/gz-tomboy-e753a55'

``` 

Will someone please help me resolve the problem, My configure log is attached below if you will be interested.

---

### Post by andrewthomas on 2011-03-11
EDIT: this is probably your problem.
[http://git.gnome.org/browse/tomboy/tree/libtomboy/Makefile.am?h=gnome-2-30&id=96b1742d6a61aaff1b66667740e5a9a64ebd2a8c](http://git.gnome.org/browse/tomboy/tree/libtomboy/Makefile.am?h=gnome-2-30&id=96b1742d6a61aaff1b66667740e5a9a64ebd2a8c)

[http://git.gnome.org/browse/tomboy/patch/?id=96b1742d6a61aaff1b66667740e5a9a64ebd2a8c](http://git.gnome.org/browse/tomboy/patch/?id=96b1742d6a61aaff1b66667740e5a9a64ebd2a8c)
If you apply that patch you may be ok.


That is a dead branch.
There has not been a commit since last may. It is at the 1.3.0 where the current master :
```

1.5.2             commit a66f252cb9...Sandy Armstrong    5 months
1.4.2             commit bf2348b537...Sandy Armstrong    5 months
1.2.2             commit d91199b743...Sandy Armstrong    5 months
1.5.1.1           commit 4cdc0ad09a...Sandy Armstrong    5 months
1.5.1             commit f9380f8788...Sandy Armstrong    5 months
1.5.0-minus       commit 3433f19c1e...Sandy Armstrong    5 months
1.4.1             commit 0e969fabdc...Benjamin Podszun   5 months
1.4.0             commit 21f2c81dec...Sandy Armstrong    5 months
1.3.4_really      commit 1d45ff8e98...Sandy Armstrong    6 months
1.3.4             commit cac8d4584f...Sandy Armstrong    6 months
1.3.3             commit 3dbba3e29d...Sandy Armstrong    6 months
1.3.2             commit a82d6aea75...Benjamin Podszun   7 months
1.3.1             commit 486c351b3e...Sandy Armstrong    8 months
1.3.0             commit 69d9584945...Sandy Armstrong    9 months

```

---

### Post by nmvictor on 2011-03-12
Please forgive my asking, I am quite new to this git and patches stuff, how do I apply a patch to a git branch? Please, sorry if this is annoying you, but please help me resolve this, I need to get tomboy to work with support for TaskManager plugin.Thanks in advance!

---

### Post by andrewthomas on 2011-03-12
What I suspect is that that 'fork' of tomboy halted development because it was merged into a later version of tomboy.  

You should first get the source package from natty here:

[http://packages.ubuntu.com/source/natty/tomboy](http://packages.ubuntu.com/source/natty/tomboy)

[http://archive.ubuntu.com/ubuntu/pool/main/t/tomboy/tomboy_1.5.2-1ubuntu4.diff.gz](http://archive.ubuntu.com/ubuntu/pool/main/t/tomboy/tomboy_1.5.2-1ubuntu4.diff.gz)

[http://archive.ubuntu.com/ubuntu/pool/main/t/tomboy/tomboy_1.5.2.orig.tar.gz](http://archive.ubuntu.com/ubuntu/pool/main/t/tomboy/tomboy_1.5.2.orig.tar.gz)

extract both packages into a directory and put the /debian folder into the tomboy folder.

Then build a .deb with .configure, make and checkinstall.

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)
[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)
[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

If that doesn't work.  Post back and I will help you patch the 'fork.'

---

### Post by nmvictor on 2011-03-12
> 
extract both packages into a directory and put the /debian folder into the tomboy folder.
I dont quite understand, what /debian directory should be put in the tomboy folder? All the same I did ./configure, make then checkinstall but checkinstall failed with the following error
```

....
....
# some other success messages here
....
....
Installed schema `/schemas/desktop/gnome/url-handlers/note/enabled' for locale `gl'
Installed schema `/schemas/desktop/gnome/url-handlers/note/enabled' for locale `ko'
test -z "/usr/local/share/dbus-1/services" || /bin/mkdir -p "/usr/local/share/dbus-1/services"
/bin/mkdir: cannot create directory `/usr/local/share/dbus-1': No such file or directory
make[3]: *** [install-dbusserviceDATA] Error 1
make[3]: Leaving directory `/home/nmvictor/tomboy-1.5.2/data'
make[2]: *** [install-am] Error 2
make[2]: Leaving directory `/home/nmvictor/tomboy-1.5.2/data'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/nmvictor/tomboy-1.5.2/data'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.


```
Just in case you are wondering, I ran checkinstall with root privileges, so permission is rules out, Please help and thanks for the concern so far.

---

### Post by sharm on 2011-03-12
> **nmvictor said:**
> I grabbed a pacthed version of tomboy from [this]("https://github.com/gz/tomboy") in order to use tomboy Task manager addin created by the same developers I guess.

You guess wrong.  This was a project by a group of students a year or so ago.  It was never submitted to upstream Tomboy for review or anything like that.  As far as I know it has never been built by anybody but those students.  You should contact them for help building it, perhaps by filing an issue in their github repository.

Andrew is right that this is a fork of Tomboy, but wrong about it ever being merged back in.

There are tons of forks of things in github, gitorious, and other similar services.  It would be best to check the website of a project to see where it is developed before jumping to conclusions about a random repository you find.  Tomboy is developed at git.gnome.org.

---

