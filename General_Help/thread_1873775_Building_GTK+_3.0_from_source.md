---
title: "Building GTK+ 3.0 from source"
date: 2011-11-01
forum: General Help
---

### Post by Inebriated on 2011-11-01
I did a search and could find nothing on this topic, also I'm not sure if this is the correct location, but here goes.

./configure seemed to work without a hitch.
```

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to disable maintainer-specific portions of Makefiles... yes
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking whether gcc and cc understand -c and -o together... yes
checking for gcc option to accept ISO C99... -std=gnu99
checking for gcc -std=gnu99 option to accept ISO Standard C... (cached) -std=gnu99
checking whether make sets $(MAKE)... (cached) yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for native Win32... no
checking for c++... c++
checking whether we are using the GNU C++ compiler... yes
checking whether c++ accepts -g... yes
checking dependency style of c++... gcc3
checking how to print strings... printf
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for fgrep... /bin/grep -F
checking for ld used by gcc -std=gnu99... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking how to convert i686-pc-linux-gnu file names to i686-pc-linux-gnu format... func_convert_file_noop
checking how to convert i686-pc-linux-gnu file names to toolchain format... func_convert_file_noop
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for dlltool... no
checking how to associate runtime and link libraries... printf %s\n
checking for ar... ar
checking for archiver @FILE support... @
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc -std=gnu99 object... ok
checking for sysroot... no
checking for mt... mt
checking if mt is a manifest tool... no
checking how to run the C preprocessor... gcc -std=gnu99 -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc -std=gnu99 supports -fno-rtti -fno-exceptions... no
checking for gcc -std=gnu99 option to produce PIC... -fPIC -DPIC
checking if gcc -std=gnu99 PIC flag -fPIC -DPIC works... yes
checking if gcc -std=gnu99 static flag -static works... yes
checking if gcc -std=gnu99 supports -c -o file.o... yes
checking if gcc -std=gnu99 supports -c -o file.o... (cached) yes
checking whether the gcc -std=gnu99 linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking how to run the C++ preprocessor... c++ -E
checking for ld used by c++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the c++ linker (/usr/bin/ld) supports shared libraries... yes
checking for c++ option to produce PIC... -fPIC -DPIC
checking if c++ PIC flag -fPIC -DPIC works... yes
checking if c++ static flag -static works... yes
checking if c++ supports -c -o file.o... yes
checking if c++ supports -c -o file.o... (cached) yes
checking whether the c++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... (cached) GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
configure: creating ./config.lt
config.lt: creating libtool
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... 64
checking dependency style of gcc -std=gnu99... gcc3
checking for nm... /usr/bin/nm -B
checking for some Win32 platform... no
checking whether build environment is sane... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for BASE_DEPENDENCIES... yes
checking for CAIRO_BACKEND... yes
checking Whether to write dependencies into .pc files... no
checking for perl5... no
checking for perl... /usr/bin/perl
checking for indent... no
checking for lstat... yes
checking for mkstemp... yes
checking for flockfile... yes
checking for getc_unlocked... yes
checking for localtime_r... yes
checking for _NL_TIME_FIRST_WEEKDAY... yes
checking for _NL_MEASUREMENT_MEASUREMENT... yes
checking for _NL_PAPER_HEIGHT... yes
checking for _NL_PAPER_WIDTH... yes
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
checking if msgfmt accepts -c... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for catalogs to be installed...  af am ang ar as ast az az_IR be be@latin bg bn bn_IN br bs ca ca@valencia crh cs cy da de dz el en en_CA en_GB eo es et eu fa fi fr ga gl gu he hi hr hu hy ia id io is it ja ka kg kk kn ko ku lg li lt lv mai mi mk ml mn mr ms my nb nds ne nl nn nso oc or pa pl ps pt pt_BR ro ru rw si sk sl sq sr sr@latin sr@ije sv ta te th tk tr tt ug uk ur uz uz@cyrillic vi wa xh yi zh_CN zh_HK zh_TW
checking for extra flags to get ANSI library prototypes... none needed
checking for the BeOS... no
checking for HP-UX... no
checking for pkg-config... (cached) /usr/bin/pkg-config
checking pkg-config is at least version 0.16... yes
checking for GLIB - version >= 2.28.0... yes (version 2.28.7)
checking for bind_textdomain_codeset... (cached) yes
checking pwd.h usability... yes
checking pwd.h presence... yes
checking for pwd.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking for unistd.h... (cached) yes
checking ftw.h usability... yes
checking ftw.h presence... yes
checking for ftw.h... yes
checking for GNU ftw extensions... yes
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking for sys/param.h... yes
checking for getpagesize... yes
checking for working mmap... yes
checking for mallinfo... yes
checking for getresuid... yes
checking for uid_t in sys/types.h... yes
checking for fd_set... yes, found in sys/types.h
checking for uxtheme.h... no
checking crt_externs.h usability... no
checking crt_externs.h presence... no
checking for crt_externs.h... no
checking for _NSGetEnviron... no
checking whether to build dynamic modules... yes
checking whether dynamic modules work... yes
checking immodules to build... 
checking sys/systeminfo.h usability... no
checking sys/systeminfo.h presence... no
checking for sys/systeminfo.h... no
checking sys/sysinfo.h usability... yes
checking sys/sysinfo.h presence... yes
checking for sys/sysinfo.h... yes
checking for gdk-pixbuf-csource... /usr/local/bin/gdk-pixbuf-csource
checking for XOpenDisplay... yes
checking for XextFindDisplay... yes
checking if <X11/extensions/XIproto.h> is needed for xReply... no
checking for XConvertCase... yes
checking for XInternAtoms... yes
checking for XAddConnectionWatch... yes
checking for XkbQueryExtension... yes
checking for XShapeCombineMask... yes
checking for XSyncQueryExtension... yes
checking for X11/extensions/sync.h... yes
checking for Xinerama packages... yes
checking X11/extensions/XInput2.h usability... yes
checking X11/extensions/XInput2.h presence... yes
checking for X11/extensions/XInput2.h... yes
checking Pango flags... -pthread -I/usr/local/include/pango-1.0 -I/usr/local/include/glib-2.0 -I/usr/local/lib/glib-2.0/include -I/usr/local/include/cairo -I/usr/local/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12   -pthread -L/usr/local/lib -lpangocairo-1.0 -lpango-1.0 -lcairo -lgobject-2.0 -lgmodule-2.0 -lgthread-2.0 -lrt -lglib-2.0  
checking ATK flags... -pthread -I/usr/local/include/atk-1.0 -I/usr/local/include/glib-2.0 -I/usr/local/lib/glib-2.0/include   -pthread -L/usr/local/lib -latk-1.0 -lgobject-2.0 -lgthread-2.0 -lrt -lglib-2.0  
checking for library containing gethostent... none required
checking for library containing setsockopt... none required
checking for library containing connect... none required
checking for struct sockaddr_un.sun_len... no
checking for cups-config... no
checking libpapi... checking for papiServiceCreate in -lpapi... no
checking cairo-pdf.h usability... yes
checking cairo-pdf.h presence... yes
checking for cairo-pdf.h... yes
checking cairo-ps.h usability... yes
checking cairo-ps.h presence... yes
checking for cairo-ps.h... yes
checking cairo-svg.h usability... yes
checking cairo-svg.h presence... yes
checking for cairo-svg.h... yes
checking for pkg-config... (cached) /usr/bin/pkg-config
checking pkg-config is at least version 0.16... yes
checking for gobject-introspection... no
checking for gtkdoc-check... no
checking for gtkdoc-rebase... no
checking for gtkdoc-mkpdf... no
checking whether to build gtk-doc documentation... no
checking for db2html... false
checking for -Bsymbolic-functions linker flag... yes
configure: creating ./config.status
config.status: creating config.h.win32
config.status: creating gtk-zip.sh
config.status: creating Makefile
config.status: creating gdk-3.0.pc
config.status: creating gtk+-3.0.pc
config.status: creating gtk+-unix-print-3.0.pc
config.status: creating gail-3.0.pc
config.status: creating gtk+-3.0-uninstalled.pc
config.status: creating gail-3.0-uninstalled.pc
config.status: creating m4macros/Makefile
config.status: creating po/Makefile.in
config.status: creating po-properties/Makefile.in
config.status: creating demos/Makefile
config.status: creating demos/gtk-demo/Makefile
config.status: creating demos/gtk-demo/geninclude.pl
config.status: creating examples/Makefile
config.status: creating tests/Makefile
config.status: creating docs/Makefile
config.status: creating docs/reference/Makefile
config.status: creating docs/reference/gdk/Makefile
config.status: creating docs/reference/gdk/version.xml
config.status: creating docs/reference/gtk/Makefile
config.status: creating docs/reference/gtk/version.xml
config.status: creating docs/reference/libgail-util/Makefile
config.status: creating docs/reference/libgail-util/version.xml
config.status: creating docs/tools/Makefile
config.status: creating build/Makefile
config.status: creating build/win32/Makefile
config.status: creating build/win32/vs9/Makefile
config.status: creating gdk/Makefile
config.status: creating gdk/x11/Makefile
config.status: creating gdk/win32/Makefile
config.status: creating gdk/win32/rc/Makefile
config.status: creating gdk/win32/rc/gdk.rc
config.status: creating gdk/quartz/Makefile
config.status: creating gdk/tests/Makefile
config.status: creating gtk/Makefile
config.status: creating gtk/makefile.msc
config.status: creating gtk/gtkversion.h
config.status: creating gtk/gtk-win32.rc
config.status: creating gtk/tests/Makefile
config.status: creating modules/Makefile
config.status: creating modules/other/Makefile
config.status: creating modules/other/gail/Makefile
config.status: creating modules/other/gail/libgail-util/Makefile
config.status: creating modules/other/gail/tests/Makefile
config.status: creating modules/engines/Makefile
config.status: creating modules/engines/pixbuf/Makefile
config.status: creating modules/engines/ms-windows/Makefile
config.status: creating modules/engines/ms-windows/Theme/Makefile
config.status: creating modules/engines/ms-windows/Theme/gtk-3.0/Makefile
config.status: creating modules/input/Makefile
config.status: creating modules/printbackends/Makefile
config.status: creating modules/printbackends/cups/Makefile
config.status: creating modules/printbackends/lpr/Makefile
config.status: creating modules/printbackends/file/Makefile
config.status: creating modules/printbackends/papi/Makefile
config.status: creating modules/printbackends/test/Makefile
config.status: creating perf/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing libtool commands
config.status: executing default-1 commands
config.status: executing default-2 commands
config.status: executing gdk/gdkconfig.h commands
config.status: gdk/gdkconfig.h is unchanged

        GTK+ 3.0.0
        ===========

        GDK backends:         x11
        X11 extensions:       XKB Xinerama XI2 XRANDR XFIXES Composite DAMAGE
        Print backends:       file lpr
        Dynamic modules:      yes
        Included immodules:   none
        PackageKit support:   yes
        Introspection:        no
        Debugging:            minimum
        Documentation:        no

```

Everything looks good to me there. Of course, I could be missing something.

Then I go to make
```

make  all-recursive
make[1]: Entering directory `/home/gary/gtk+-3.0.0'
Making all in po
make[2]: Entering directory `/home/gary/gtk+-3.0.0/po'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/gary/gtk+-3.0.0/po'
Making all in po-properties
make[2]: Entering directory `/home/gary/gtk+-3.0.0/po-properties'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/gary/gtk+-3.0.0/po-properties'
Making all in gdk
make[2]: Entering directory `/home/gary/gtk+-3.0.0/gdk'
  GEN    gdkconfig.h
make  all-recursive
make[3]: Entering directory `/home/gary/gtk+-3.0.0/gdk'
Making all in x11
make[4]: Entering directory `/home/gary/gtk+-3.0.0/gdk/x11'
  CC     gdkapplaunchcontext-x11.lo
  CC     gdkasync.lo
  CC     gdkcursor-x11.lo
  CC     gdkdevice-core-x11.lo
  CC     gdkdevicemanager-core-x11.lo
  CC     gdkdevicemanager-x11.lo
  CC     gdkdisplaymanager-x11.lo
  CC     gdkdisplay-x11.lo
  CC     gdkdnd-x11.lo
  CC     gdkeventsource.lo
  CC     gdkgeometry-x11.lo
  CC     gdkkeys-x11.lo
  CC     gdkmain-x11.lo
  CC     gdkproperty-x11.lo
  CC     gdkscreen-x11.lo
  CC     gdkselection-x11.lo
  CC     gdktestutils-x11.lo
  CC     gdkvisual-x11.lo
  CC     gdkwindow-x11.lo
  CC     gdkxftdefaults.lo
  CC     gdkxid.lo
  CC     gdkdevicemanager-xi.lo
  CC     gdkdevice-xi.lo
  CC     gdkdevicemanager-xi2.lo
  CC     gdkdevice-xi2.lo
  CCLD   libgdk-x11.la
  CCLD   checksettings
make[4]: Leaving directory `/home/gary/gtk+-3.0.0/gdk/x11'
Making all in .
make[4]: Entering directory `/home/gary/gtk+-3.0.0/gdk'
  CC     gdk.lo
  CC     gdkcairo.lo
  CC     gdkcolor.lo
  CC     gdkcursor.lo
  CC     gdkdevice.lo
  CC     gdkdisplay.lo
  GEN    gdkconfig.h
  CC     gdkdisplaymanager.lo
  CC     gdkevents.lo
  CC     gdkglobals.lo
  CC     gdkoffscreenwindow.lo
  CC     gdkpixbuf-drawable.lo
  CC     gdkselection.lo
  CC     gdkwindow.lo
  CC     gdkwindowimpl.lo
  CC     gdkenumtypes.lo
  CCLD   libgdk-3.la
make[4]: Leaving directory `/home/gary/gtk+-3.0.0/gdk'
Making all in tests
make[4]: Entering directory `/home/gary/gtk+-3.0.0/gdk/tests'
  CC     gdk-color.o
  CCLD   gdk-color
/usr/local/lib/libgio-2.0.so: undefined reference to `g_variant_get_bytestring_array'
/usr/local/lib/libgio-2.0.so: undefined reference to `g_source_get_time'
/usr/local/lib/libgio-2.0.so: undefined reference to `g_cclosure_marshal_VOID__VARIANT'
../../gdk/.libs/libgdk-3.so: undefined reference to `g_list_free_full'
/usr/local/lib/libgio-2.0.so: undefined reference to `g_variant_dup_bytestring_array'
/usr/local/lib/libgio-2.0.so: undefined reference to `g_dcgettext'
/usr/local/lib/libgio-2.0.so: undefined reference to `g_signal_accumulator_first_wins'
/usr/local/lib/libgio-2.0.so: undefined reference to `g_variant_is_floating'
/usr/local/lib/libgio-2.0.so: undefined reference to `g_value_set_variant'
/usr/local/lib/libgio-2.0.so: undefined reference to `g_object_class_install_properties'
/usr/local/lib/libgio-2.0.so: undefined reference to `g_get_environ'
/usr/local/lib/libgio-2.0.so: undefined reference to `g_variant_compare'
/usr/local/lib/libgio-2.0.so: undefined reference to `g_value_get_variant'
/usr/local/lib/libgio-2.0.so: undefined reference to `g_source_set_dummy_callback'
/usr/local/lib/libgio-2.0.so: undefined reference to `g_variant_new_bytestring'
/usr/local/lib/libgio-2.0.so: undefined reference to `g_variant_new_bytestring_array'
/usr/local/lib/libgio-2.0.so: undefined reference to `g_param_spec_variant'
/usr/local/lib/libgio-2.0.so: undefined reference to `g_main_context_invoke'
/usr/local/lib/libgio-2.0.so: undefined reference to `g_source_add_child_source'
/usr/local/lib/libgio-2.0.so: undefined reference to `g_get_monotonic_time'
../../gdk/.libs/libgdk-3.so: undefined reference to `g_source_set_name'
/usr/local/lib/libgio-2.0.so: undefined reference to `g_variant_get_bytestring'
../../gdk/.libs/libgdk-3.so: undefined reference to `g_slist_free_full'
/usr/local/lib/libgio-2.0.so: undefined reference to `g_value_take_variant'
/usr/local/lib/libgio-2.0.so: undefined reference to `g_value_dup_variant'
/usr/local/lib/libgio-2.0.so: undefined reference to `g_error_get_type'
collect2: ld returned 1 exit status
make[4]: *** [gdk-color] Error 1
make[4]: Leaving directory `/home/gary/gtk+-3.0.0/gdk/tests'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/gary/gtk+-3.0.0/gdk'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/gary/gtk+-3.0.0/gdk'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/gary/gtk+-3.0.0'
make: *** [all] Error 2

```

I get all kinds of errors. I have all the dependencies, and I remembered to ldconfig after I make installed glib. Anyway, hopefully I can get some help. If anything is wrong with this thread, I'm sorry. I couldn't actually find the forum rules by using the search function, so if I'm breaking any rules feel free to notify me.

I also installed gtk3 on debian without a hitch.

Also if anybody could link me to the forum global rules or something (so I don't break them) I would be much obliged.

---

### Post by gsmanners on 2011-11-02
I think unless you have the libs installed already in /usr/local/libs that build isn't going to work. Did you read the part on exporting environment variables?

[http://developer.gnome.org/gtk/unstable/gtk-building.html](http://developer.gnome.org/gtk/unstable/gtk-building.html)

> Several environment variables are useful to pass to set before running configure.

---

### Post by Inebriated on 2011-11-02
Okay, I seem to at least be getting new errors now that I set the environmental variables.

I had gotten:
```
/usr/share/gir-1.0/GdkPixbuf-2.0.gir: Incompatible version 1.0 (supported: 1.2)
make[4]: *** [Gdk-3.0.gir] Error 1
```

So I reinstalled gdk-pixbuf and no longer get that error, instead now I'm getting:

```
/usr/share/gir-1.0/Pango-1.0.gir: Incompatible version 1.0 (supported: 1.2)
make[4]: *** [Gdk-3.0.gir] Error 1
```

Going to try and reinstall pango. I have the feeling I screwed the pooch somewhere. Maybe I should just do a fresh install.

---

### Post by hailtothethief on 2011-11-02
Building large projects from source can be an infuriating exercise. apt-get build-dep can make your life much easier. If you're using 11.10 I'm 99% sure the following command will eliminate your build dependency problems:

```
sudo apt-get build-dep libgtk-3-0
```

---

### Post by crdlb on 2011-11-02
Why are you installing GTK+ from source? What version of Ubuntu are you using?

---

