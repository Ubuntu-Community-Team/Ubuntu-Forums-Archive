---
title: "Troube installing Gimp Ace"
date: 2011-09-09
forum: General Help
---

### Post by revnobody on 2011-09-09
I am trying to install the Ace plugin for Gimp. When I run ./config   I keep getting this:


checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking for strerror in -lcposix... no
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for gcc option to accept ANSI C... none needed
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for pkg-config... /usr/bin/pkg-config
[COLOR=Red]checking for gimp-2.0 >= 2.2.0 gimpui-2.0 >= 2.2.0... Package gimp-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gimp-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gimp-2.0' found Package gimpui-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gimpui-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gimpui-2.0' found
configure: error: Library requirements (gimp-2.0 >= 2.2.0 gimpui-2.0 >= 2.2.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
[/COLOR] 
I am not sure how to fix this. Any advice would be greatly appreciated, as I use this plugin almost daily on my other machine.

---

### Post by dbdexter on 2011-09-09
I found a guide to install gimp on ubuntu, but i've not tried it: [http://basicubuntu.blogspot.com/2009/02/compiling-gimp-on-ubuntu.html](http://basicubuntu.blogspot.com/2009/02/compiling-gimp-on-ubuntu.html)
Hope this helped):P):P):P

---

### Post by revnobody on 2011-09-09
Thanks for the quick reply. I will read over it and see if it has any info to help my current problem. I do already have Gimp installed. My problem is just with compiling this plug in. ..... ;)

---

### Post by dbdexter on 2011-09-09
But if you install gimp using this guide and then extract the plugin in the directory containing the files you have installed, you should be able to install the gimp-ace plugin
now i'm installing gimp and i'll attempt to install gimp-ace

---

### Post by Bodsda on 2011-09-09
> **revnobody said:**
> I am trying to install the Ace plugin for Gimp. When I run ./config I keep getting this:
 
 
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking for strerror in -lcposix... no
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for gcc option to accept ANSI C... none needed
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for pkg-config... /usr/bin/pkg-config
[COLOR=red]checking for gimp-2.0 >= 2.2.0 gimpui-2.0 >= 2.2.0... Package gimp-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gimp-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gimp-2.0' found Package gimpui-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gimpui-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gimpui-2.0' found[/COLOR]
[COLOR=red]configure: error: Library requirements (gimp-2.0 >= 2.2.0 gimpui-2.0 >= 2.2.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.[/COLOR]

I am not sure how to fix this. Any advice would be greatly appreciated, as I use this plugin almost daily on my other machine.
 
Are you sure it is gimp-2.0 that you have installed? It is looking for a specific gimp-2.0.pc file. Run the following command to locate the file
 
```

sudo find / -name 'gimp-2.0.pc'

```
 
Thanks,
Bodsda

---

### Post by revnobody on 2011-09-09
I am running Gimp 2.6. Documentation for the plug in says it will work. But, you are correct there is no file gimp-2.0.pc.

My other computer is also running Gimp 2.6 and the plug in does work on it. I am just now sure how it was compiled and installed as it was already there when I purchased the computer.

Thanks for all the quick replies. I really appreciate it.

---

### Post by Bodsda on 2011-09-09
> **revnobody said:**
> I am running Gimp 2.6. Documentation for the plug in says it will work. But, you are correct there is no file gimp-2.0.pc.
 
Thanks for all the quick replies. I really appreciate it.
 
Look for an updated plugin, that one is specifically checking for gimp-2.0 so wont install if it cant find it.
 
Can you run that find command on your other machine, and see if it finds the file.
 
Thanks,
Bodsda

---

### Post by revnobody on 2011-09-09
Yeah I can try it tomorrow at my store, that is where the computer is. I have searched high and low and can't seem to find an updated plug in. I have even searched for alternatives..haha. I use this particular plug in for at least 80% of my design work. I really hope that I can get this working :confused:   I do have a gimp 2.0 folder in my root but not with the extension .pc

---

### Post by revnobody on 2011-09-09
I found this from another user that was running Gimp 2.6.10 and it looks that he had no problems. I downloaded this from the same place. [http://registry.gimp.org/node/20](http://registry.gimp.org/node/20)




I used it long time ago as win32 binary version with Gimp and now  after the total changeover after the mighty release of Ubuntu 10.10 - (a  big Windows dying plague happened here since release of 10.10;-)
 But i missed very quick this filter in the original pack - so downloaded the 0.67 sources
compiled it sucessfully and it runs surprisingly well w/o any problem
(just ./configure && make && sudo make install)
 System Ubuntu 10.10 Maverick, Gimp 2.6.10

---

### Post by Bodsda on 2011-09-09
> **revnobody said:**
> Yeah I can try it tomorrow at my store, that is where the computer is. I have searched high and low and can't seem to find an updated plug in. I have even searched for alternatives..haha. I use this particular plug in for at least 80% of my design work. I really hope that I can get this working :confused: I do have a gimp 2.0 folder in my root but not with the extension .pc
 
It wont be a folder, it will be a file.
If the docs say that it will work, then fair enough. Does it come with compilation instructions?
 
Bodsda

---

### Post by revnobody on 2011-09-09
Yes, I have included them below.  I have the extracted folder on my desktop and then cd to the directory. Then when I ./configure   I get the above error.



   The `configure' shell script attempts to guess correct values for
various system-dependent variables used during compilation.  It uses
those values to create a `Makefile' in each directory of the package.
It may also create one or more `.h' files containing system-dependent
definitions.  Finally, it creates a shell script `config.status' that
you can run in the future to recreate the current configuration, and a
file `config.log' containing compiler output (useful mainly for
debugging `configure').

   It can also use an optional file (typically called `config.cache'
and enabled with `--cache-file=config.cache' or simply `-C') that saves
the results of its tests to speed up reconfiguring.  (Caching is
disabled by default to prevent problems with accidental use of stale
cache files.)

   If you need to do unusual things to compile the package, please try
to figure out how `configure' could check whether to do them, and mail
diffs or instructions to the address given in the `README' so they can
be considered for the next release.  If you are using the cache, and at
some point `config.cache' contains results you don't want to keep, you
may remove or edit it.

   The file `configure.ac' (or `configure.in') is used to create
`configure' by a program called `autoconf'.  You only need
`configure.ac' if you want to change it or regenerate `configure' using
a newer version of `autoconf'.

The simplest way to compile this package is:

  1. `cd' to the directory containing the package's source code and type
     `./configure' to configure the package for your system.  If you're
     using `csh' on an old version of System V, you might need to type
     `sh ./configure' instead to prevent `csh' from trying to execute
     `configure' itself.

     Running `configure' takes awhile.  While running, it prints some
     messages telling which features it is checking for.

  2. Type `make' to compile the package.

  3. Optionally, type `make check' to run any self-tests that come with
     the package.

  4. Type `make install' to install the programs and any data files and
     documentation.

  5. You can remove the program binaries and object files from the
     source code directory by typing `make clean'.  To also remove the
     files that `configure' created (so you can compile the package for
     a different kind of computer), type `make distclean'.  There is
     also a `make maintainer-clean' target, but that is intended mainly
     for the package's developers.  If you use it, you may have to get
     all sorts of other programs in order to regenerate files that came
     with the distribution.

---

### Post by Bodsda on 2011-09-09
Ok, lets start again. Remove any trace of gimp-ace. 
 
Download [gimp-ace2]("http://registry.gimp.org/files/gimp-ace-0.6.7.tar.gz") (built for gimp2.2, should work on 2.4, comments confirm working on 2.6 and 2.7)
 
unpack the sources
 
```

cd <source directory>
./configure

```
 
Please paste entire output.
 
Thanks,
Bodsda

---

### Post by revnobody on 2011-09-09
I think I need to install the developer files in order to get the file it is looking for. Looks as if this is where this file would be.  Let me try this and I will get back to you......thanks again for all your help

---

### Post by revnobody on 2011-09-09
revnobody@Revnobody-Linux:~/Desktop/gimp-ace-0.2.6.7$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking for strerror in -lcposix... no
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for gcc option to accept ANSI C... none needed
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for pkg-config... /usr/bin/pkg-config
checking for gimp-2.0 >= 2.2.0 gimpui-2.0 >= 2.2.0... Package gimp-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gimp-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gimp-2.0' found Package gimpui-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gimpui-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gimpui-2.0' found
configure: error: Library requirements (gimp-2.0 >= 2.2.0 gimpui-2.0 >= 2.2.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
revnobody@Revnobody-Linux:~/Desktop/gimp-ace-0.2.6.7$

---

### Post by Bodsda on 2011-09-09
> **revnobody said:**
> revnobody@Revnobody-Linux:~/Desktop/gimp-ace-0.2.6.7$ ./configure
<snip>
No package 'gimpui-2.0' found
configure: error: Library requirements (gimp-2.0 >= 2.2.0 gimpui-2.0 >= 2.2.0) not met; <snip>
 
Can you install any 'gimp-dev*' packages and possibly 'lib-gimp*' if there are any.
 
Thanks,
Bodsda

---

### Post by revnobody on 2011-09-09
Ok getting closer. I used  this:
```
 sudo apt-get install libgimp2.0-dev
```


Now I get further. Here is my new readout.

revnobody@Revnobody-Linux:~$ cd /home/revnobody/Desktop/gimp-ace-0.2.6.7
revnobody@Revnobody-Linux:~/Desktop/gimp-ace-0.2.6.7$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking for strerror in -lcposix... no
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for gcc option to accept ANSI C... none needed
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for pkg-config... /usr/bin/pkg-config
checking for gimp-2.0 >= 2.2.0 gimpui-2.0 >= 2.2.0... yes
checking GIMP_CFLAGS... -pthread -I/usr/include/glib-2.0 -I/usr/lib/i386-linux-gnu/glib-2.0/include -I/usr/include/atk-1.0 -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/gimp-2.0 -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/cairo -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/pixman-1  
checking GIMP_LIBS... -pthread -L/usr/lib/i386-linux-gnu -lgimpui-2.0 -lgimpwidgets-2.0 -lgimpmodule-2.0 -lgimp-2.0 -lgimpmath-2.0 -lgimpconfig-2.0 -lgimpcolor-2.0 -lgimpbase-2.0 -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgio-2.0 -lpangoft2-1.0 -lpangocairo-1.0 -lgdk_pixbuf-2.0 -lm -lcairo -lpango-1.0 -lfreetype -lfontconfig -lgobject-2.0 -lgmodule-2.0 -lgthread-2.0 -lrt -lglib-2.0  
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for iconv... /usr/bin/iconv
checking for msgfmt... /usr/bin/msgfmt
checking for msgmerge... /usr/bin/msgmerge
checking for xgettext... /usr/bin/xgettext
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for catalogs to be installed...  az de fr sk sv zh_TW
checking for bind_textdomain_codeset... (cached) yes
checking if GTK+ is version 2.7.0 or newer... yes
checking if GIMP is version 2.3.0 or newer... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating po/Makefile.in
config.status: creating help/Makefile
config.status: creating help/en/Makefile
config.status: creating help/images/Makefile
config.status: creating config.h
config.status: executing depfiles commands
config.status: executing intltool commands
config.status: executing default-1 commands
revnobody@Revnobody-Linux:~/Desktop/gimp-ace-0.2.6.7$ make
make  all-recursive
make[1]: Entering directory `/home/revnobody/Desktop/gimp-ace-0.2.6.7'
Making all in po
make[2]: Entering directory `/home/revnobody/Desktop/gimp-ace-0.2.6.7/po'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/revnobody/Desktop/gimp-ace-0.2.6.7/po'
Making all in src
make[2]: Entering directory `/home/revnobody/Desktop/gimp-ace-0.2.6.7/src'
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I.. -pthread -I/usr/include/glib-2.0 -I/usr/lib/i386-linux-gnu/glib-2.0/include -I/usr/include/atk-1.0 -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/gimp-2.0 -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/cairo -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/pixman-1 -I/usr/local/include -DLOCALEDIR=\""/usr/local/share/locale"\" -DDATADIR=\""/usr/local/share/gimp-ace"\"   -g -O2 -Wall -MT gimp_ace.o -MD -MP -MF ".deps/gimp_ace.Tpo" \
      -c -o gimp_ace.o `test -f 'gimp_ace.c' || echo './'`gimp_ace.c; \
    then mv -f ".deps/gimp_ace.Tpo" ".deps/gimp_ace.Po"; \
    else rm -f ".deps/gimp_ace.Tpo"; exit 1; \
    fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I.. -pthread -I/usr/include/glib-2.0 -I/usr/lib/i386-linux-gnu/glib-2.0/include -I/usr/include/atk-1.0 -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/gimp-2.0 -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/cairo -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/pixman-1 -I/usr/local/include -DLOCALEDIR=\""/usr/local/share/locale"\" -DDATADIR=\""/usr/local/share/gimp-ace"\"   -g -O2 -Wall -MT dialog.o -MD -MP -MF ".deps/dialog.Tpo" \
      -c -o dialog.o `test -f 'dialog.c' || echo './'`dialog.c; \
    then mv -f ".deps/dialog.Tpo" ".deps/dialog.Po"; \
    else rm -f ".deps/dialog.Tpo"; exit 1; \
    fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I.. -pthread -I/usr/include/glib-2.0 -I/usr/lib/i386-linux-gnu/glib-2.0/include -I/usr/include/atk-1.0 -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/gimp-2.0 -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/cairo -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/pixman-1 -I/usr/local/include -DLOCALEDIR=\""/usr/local/share/locale"\" -DDATADIR=\""/usr/local/share/gimp-ace"\"   -g -O2 -Wall -MT preview.o -MD -MP -MF ".deps/preview.Tpo" \
      -c -o preview.o `test -f 'preview.c' || echo './'`preview.c; \
    then mv -f ".deps/preview.Tpo" ".deps/preview.Po"; \
    else rm -f ".deps/preview.Tpo"; exit 1; \
    fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I.. -pthread -I/usr/include/glib-2.0 -I/usr/lib/i386-linux-gnu/glib-2.0/include -I/usr/include/atk-1.0 -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/gimp-2.0 -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/cairo -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/pixman-1 -I/usr/local/include -DLOCALEDIR=\""/usr/local/share/locale"\" -DDATADIR=\""/usr/local/share/gimp-ace"\"   -g -O2 -Wall -MT glace.o -MD -MP -MF ".deps/glace.Tpo" \
      -c -o glace.o `test -f 'glace.c' || echo './'`glace.c; \
    then mv -f ".deps/glace.Tpo" ".deps/glace.Po"; \
    else rm -f ".deps/glace.Tpo"; exit 1; \
    fi
glace.c: In function ‘Glace_CfgBeginToHeseries’:
glace.c:1321:33: warning: comparison between ‘Glace_Modes’ and ‘enum <anonymous>’
glace.c:1330:32: warning: comparison between ‘Glace_Modes’ and ‘enum <anonymous>’
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I.. -pthread -I/usr/include/glib-2.0 -I/usr/lib/i386-linux-gnu/glib-2.0/include -I/usr/include/atk-1.0 -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/gimp-2.0 -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/cairo -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/pixman-1 -I/usr/local/include -DLOCALEDIR=\""/usr/local/share/locale"\" -DDATADIR=\""/usr/local/share/gimp-ace"\"   -g -O2 -Wall -MT glaceG.o -MD -MP -MF ".deps/glaceG.Tpo" \
      -c -o glaceG.o `test -f 'glaceG.c' || echo './'`glaceG.c; \
    then mv -f ".deps/glaceG.Tpo" ".deps/glaceG.Po"; \
    else rm -f ".deps/glaceG.Tpo"; exit 1; \
    fi
glaceG.c: In function ‘Glace_WError’:
glaceG.c:53:3: warning: format not a string literal and no format arguments
glaceG.c: In function ‘Glace_Redraw_Preview’:
glaceG.c:307:31: warning: pointer targets in passing argument 2 of ‘gimp_preview_draw_buffer’ differ in signedness
/usr/include/gimp-2.0/libgimpwidgets/gimppreview.h:132:13: note: expected ‘const guchar *’ but argument is of type ‘char *’
gcc  -g -O2 -Wall   -o gimp-ace  gimp_ace.o dialog.o preview.o glace.o glaceG.o -pthread -L/usr/lib/i386-linux-gnu -lgimpui-2.0 -lgimpwidgets-2.0 -lgimpmodule-2.0 -lgimp-2.0 -lgimpmath-2.0 -lgimpconfig-2.0 -lgimpcolor-2.0 -lgimpbase-2.0 -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgio-2.0 -lpangoft2-1.0 -lpangocairo-1.0 -lgdk_pixbuf-2.0 -lm -lcairo -lpango-1.0 -lfreetype -lfontconfig -lgobject-2.0 -lgmodule-2.0 -lgthread-2.0 -lrt -lglib-2.0   
make[2]: Leaving directory `/home/revnobody/Desktop/gimp-ace-0.2.6.7/src'
Making all in help
make[2]: Entering directory `/home/revnobody/Desktop/gimp-ace-0.2.6.7/help'
Making all in en
make[3]: Entering directory `/home/revnobody/Desktop/gimp-ace-0.2.6.7/help/en'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/revnobody/Desktop/gimp-ace-0.2.6.7/help/en'
Making all in images
make[3]: Entering directory `/home/revnobody/Desktop/gimp-ace-0.2.6.7/help/images'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/revnobody/Desktop/gimp-ace-0.2.6.7/help/images'
make[3]: Entering directory `/home/revnobody/Desktop/gimp-ace-0.2.6.7/help'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/revnobody/Desktop/gimp-ace-0.2.6.7/help'
make[2]: Leaving directory `/home/revnobody/Desktop/gimp-ace-0.2.6.7/help'
make[2]: Entering directory `/home/revnobody/Desktop/gimp-ace-0.2.6.7'
make[2]: Leaving directory `/home/revnobody/Desktop/gimp-ace-0.2.6.7'
make[1]: Leaving directory `/home/revnobody/Desktop/gimp-ace-0.2.6.7'
revnobody@Revnobody-Linux:~/Desktop/gimp-ace-0.2.6.7$ make install
Making install in po
make[1]: Entering directory `/home/revnobody/Desktop/gimp-ace-0.2.6.7/po'
if test -n ""; then \
       /usr/local/share; \
    else \
      /bin/sh ../mkinstalldirs /usr/local/share; \
    fi
mkdir -p -- /usr/local/share/locale/az/LC_MESSAGES
mkdir: cannot create directory `/usr/local/share/locale': Permission denied
/usr/bin/install: cannot create regular file `/usr/local/share/locale/az/LC_MESSAGES/gimp20-plugin-template.mo': No such file or directory
installing az.gmo as /usr/local/share/locale/az/LC_MESSAGES/gimp20-plugin-template.mo
mkdir -p -- /usr/local/share/locale/de/LC_MESSAGES
mkdir: cannot create directory `/usr/local/share/locale': Permission denied
/usr/bin/install: cannot create regular file `/usr/local/share/locale/de/LC_MESSAGES/gimp20-plugin-template.mo': No such file or directory
installing de.gmo as /usr/local/share/locale/de/LC_MESSAGES/gimp20-plugin-template.mo
mkdir -p -- /usr/local/share/locale/fr/LC_MESSAGES
mkdir: cannot create directory `/usr/local/share/locale': Permission denied
/usr/bin/install: cannot create regular file `/usr/local/share/locale/fr/LC_MESSAGES/gimp20-plugin-template.mo': No such file or directory
installing fr.gmo as /usr/local/share/locale/fr/LC_MESSAGES/gimp20-plugin-template.mo
mkdir -p -- /usr/local/share/locale/sk/LC_MESSAGES
mkdir: cannot create directory `/usr/local/share/locale': Permission denied
/usr/bin/install: cannot create regular file `/usr/local/share/locale/sk/LC_MESSAGES/gimp20-plugin-template.mo': No such file or directory
installing sk.gmo as /usr/local/share/locale/sk/LC_MESSAGES/gimp20-plugin-template.mo
mkdir -p -- /usr/local/share/locale/sv/LC_MESSAGES
mkdir: cannot create directory `/usr/local/share/locale': Permission denied
/usr/bin/install: cannot create regular file `/usr/local/share/locale/sv/LC_MESSAGES/gimp20-plugin-template.mo': No such file or directory
installing sv.gmo as /usr/local/share/locale/sv/LC_MESSAGES/gimp20-plugin-template.mo
mkdir -p -- /usr/local/share/locale/zh_TW/LC_MESSAGES
mkdir: cannot create directory `/usr/local/share/locale': Permission denied
/usr/bin/install: cannot create regular file `/usr/local/share/locale/zh_TW/LC_MESSAGES/gimp20-plugin-template.mo': No such file or directory
installing zh_TW.gmo as /usr/local/share/locale/zh_TW/LC_MESSAGES/gimp20-plugin-template.mo
if test "gimp-ace" = "glib"; then \
      if test -n ""; then \
         /usr/local/share/glib-2.0/gettext/po; \
      else \
        /bin/sh ../mkinstalldirs /usr/local/share/glib-2.0/gettext/po; \
      fi; \
      /usr/bin/install -c -m 644 ./Makefile.in.in \
              /usr/local/share/glib-2.0/gettext/po/Makefile.in.in; \
    else \
      : ; \
    fi
make[1]: Leaving directory `/home/revnobody/Desktop/gimp-ace-0.2.6.7/po'
Making install in src
make[1]: Entering directory `/home/revnobody/Desktop/gimp-ace-0.2.6.7/src'
make[2]: Entering directory `/home/revnobody/Desktop/gimp-ace-0.2.6.7/src'
/bin/bash ../mkinstalldirs /usr/lib/gimp/2.0/plug-ins
  /usr/bin/install -c gimp-ace /usr/lib/gimp/2.0/plug-ins/gimp-ace
/usr/bin/install: cannot create regular file `/usr/lib/gimp/2.0/plug-ins/gimp-ace': Permission denied
make[2]: *** [install-binPROGRAMS] Error 1
make[2]: Leaving directory `/home/revnobody/Desktop/gimp-ace-0.2.6.7/src'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/revnobody/Desktop/gimp-ace-0.2.6.7/src'
make: *** [install-recursive] Error 1
revnobody@Revnobody-Linux:~/Desktop/gimp-ace-0.2.6.7$

---

### Post by Bodsda on 2011-09-09
Hmm, permission denied errors.
 
Out of interest, where there any gimp-deve* packages?
 
Try running ./configure as root.
```

sudo ./configure

```
 
Thanks,
Bodsda

---

### Post by dbdexter on 2011-09-09
it WORKS!!!
When you installed gimp USING THE GUIDE do this:
./configure --prefix=/opt/gimp-2.6
make
sudo make install
This should work

---

### Post by revnobody on 2011-09-09
Still getting the same thing as root.  I am not sure how to check for gimp dev.  I did read somewhere before something about someone using Gimp templates to get it working but I can't find this info now and I am not sure what they were referring to or if it is even relevant.

---

### Post by Bodsda on 2011-09-09
> **revnobody said:**
> Still getting the same thing as root. I am not sure how to check for gimp dev. I did read somewhere before something about someone using Gimp templates to get it working but I can't find this info now and I am not sure what they were referring to or if it is even relevant.
 
Type this in the terminal (where it says <tab> that means hit the tab button)
```

sudo apt-get install gimp-dev<tab><tab>

```
 
Bodsda

---

### Post by revnobody on 2011-09-09
says unable to locate

---

### Post by Bodsda on 2011-09-09
> **revnobody said:**
> says unable to locate
 
What does? Please paste full output
 
Thanks,
Bodsda

---

### Post by revnobody on 2011-09-09
Actually I ran ./configure  make   make install again as root and it worked!!!!  :guitar:  Thank you so much for all your help!! This has been driving me crazy for hours!.....  It is now working perfectly!

Problem Solved

---

### Post by Bodsda on 2011-09-09
> **revnobody said:**
> Actually I ran ./configure make make install again as root and it worked!!!! :guitar: Thank you so much for all your help!! This has been driving me crazy for hours!..... It is now working perfectly!
 
Problem Solved
 
Excellent! 
Glad i could help
 
Bodsda

---

### Post by revnobody on 2011-09-09
Very much appreciated... high five to you!:P

---

