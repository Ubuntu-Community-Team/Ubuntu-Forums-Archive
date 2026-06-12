---
title: "Need help on installing gloobus Cover!!!"
date: 2011-10-04
forum: General Help
---

### Post by JoshH54 on 2011-10-04
I really want to install gloobus cover. I already have the preview and its class but now i want the cover and am running into a little difficulty. 

I am following these instructions [http://www.webupd8.org/2010/02/how-to-install-gloobus-flow-clutter.html](http://www.webupd8.org/2010/02/how-to-install-gloobus-flow-clutter.html)

I have completed the instructions but it doesn't seem to be working. I dont know the coding but the only time i see and error in the coding is in the "[B]3. Download and install Nautilus Clutter GTKlist" part. 

W[B]hen i type "sudo apt-get build-dep nautilus" i get
[/B][/B]```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
josh@LINUX-PC:~/gloobus-flow$ cd
josh@LINUX-PC:~$ bzr branch lp:~gloobus-dev/gloobus-flow/nautilus-clutter-gtklist
You have not informed bzr of your Launchpad ID, and you must do this to
write to Launchpad or access private data.  See "bzr help launchpad-login".
Branched 58 revision(s).                                                       
josh@LINUX-PC:~$ cd nautilus-clutter-gtklist
josh@LINUX-PC:~/nautilus-clutter-gtklist$ ./autogen.sh --prefix=/usr
/usr/bin/gnome-autogen.sh
checking for autoconf >= 2.53...
  testing autoconf2.50... not found.
  testing autoconf... found 2.67
checking for automake >= 1.7...
  testing automake-1.11... found 1.11.1
checking for libtool >= 1.5...
  testing libtoolize... found 2.2.6b
checking for glib-gettext >= 2.2.0...
  testing glib-gettextize... found 2.28.6
checking for intltool >= 0.30...
  testing intltoolize... found 0.41.1
checking for pkg-config >= 0.14.0...
  testing pkg-config... found 0.25
checking for gtk-doc >= 1.0...
  testing gtkdocize... found 1.17
Checking for required M4 macros...
Checking for forbidden M4 macros...
Processing ./configure.in
Running libtoolize...
libtoolize: putting auxiliary files in `.'.
libtoolize: copying file `./ltmain.sh'
libtoolize: putting macros in AC_CONFIG_MACRO_DIR, `m4'.
libtoolize: copying file `m4/libtool.m4'
libtoolize: copying file `m4/ltoptions.m4'
libtoolize: copying file `m4/ltsugar.m4'
libtoolize: copying file `m4/ltversion.m4'
libtoolize: copying file `m4/lt~obsolete.m4'
Running glib-gettextize... Ignore non-fatal messages.
Copying file mkinstalldirs
Copying file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
ftp://ftp.gnu.org/pub/gnu/config/.

Running intltoolize...
Running gtkdocize...
Running aclocal-1.11...
configure.in:25: warning: AC_INIT: not a literal: http://bugzilla.gnome.org/enter_bug.cgi?product=nautilus
Running autoconf...
configure.in:25: warning: AC_INIT: not a literal: http://bugzilla.gnome.org/enter_bug.cgi?product=nautilus
Running autoheader...
autoheader: WARNING: Using auxiliary files such as `acconfig.h', `config.h.bot'
autoheader: WARNING: and `config.h.top', to define templates for `config.h.in'
autoheader: WARNING: is deprecated and discouraged.
autoheader: 
autoheader: WARNING: Using the third argument of `AC_DEFINE' and
autoheader: WARNING: `AC_DEFINE_UNQUOTED' allows one to define a template without
autoheader: WARNING: `acconfig.h':
autoheader: 
autoheader: WARNING:   AC_DEFINE([NEED_FUNC_MAIN], 1,
autoheader:         [Define if a function `main' is needed.])
autoheader: 
autoheader: WARNING: More sophisticated templates can also be produced, see the
autoheader: WARNING: documentation.
configure.in:25: warning: AC_INIT: not a literal: http://bugzilla.gnome.org/enter_bug.cgi?product=nautilus
Running automake-1.11...
configure.in:25: warning: AC_INIT: not a literal: http://bugzilla.gnome.org/enter_bug.cgi?product=nautilus
configure.in:57: installing `./config.guess'
configure.in:57: installing `./config.sub'
configure.in:34: installing `./install-sh'
configure.in:34: installing `./missing'
cut-n-paste-code/libegg/Makefile.am: installing `./depcomp'
Makefile.am: installing `./INSTALL'
Running ./configure --enable-maintainer-mode --prefix=/usr ...
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking how to create a ustar tar archive... gnutar
checking whether to enable maintainer-specific portions of Makefiles... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
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
checking whether byte ordering is bigendian... no
checking for an ANSI C-conforming const... yes
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking whether ln -s works... yes
checking whether make sets $(MAKE)... (cached) yes
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for ar... ar
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for ALL... yes
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
checking whether NLS is requested... yes
checking for intltool >= 0.40.1... 0.41.1 found
checking for intltool-update... /usr/bin/intltool-update
checking for intltool-merge... /usr/bin/intltool-merge
checking for intltool-extract... /usr/bin/intltool-extract
checking for xgettext... (cached) /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for msgfmt... (cached) /usr/bin/msgfmt
checking for gmsgfmt... (cached) /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for perl >= 5.8.1... 5.10.1
checking for XML::Parser... ok
checking for gtkdoc-check... /usr/bin/gtkdoc-check
checking for gtkdoc-rebase... /usr/bin/gtkdoc-rebase
checking for gtkdoc-mkpdf... /usr/bin/gtkdoc-mkpdf
checking whether to build gtk-doc documentation... no
checking for perl5... no
checking for perl... perl
checking for glib-genmarshal... /usr/bin/glib-genmarshal
checking sys/mount.h usability... yes
checking sys/mount.h presence... yes
checking for sys/mount.h... yes
checking sys/vfs.h usability... yes
checking sys/vfs.h presence... yes
checking for sys/vfs.h... yes
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking for mallopt... yes
checking for X... libraries , headers 
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for XOpenDisplay in -lX11... yes
checking for EXIF... yes
checking for EXEMPI... yes
checking for EXEMPI_NEW_API... yes
checking for TRACKER... no
checking for TRACKER... no
checking for BEAGLE... no
checking for is_selinux_enabled in -lselinux... yes
checking selinux/selinux.h usability... yes
checking selinux/selinux.h presence... yes
checking for selinux/selinux.h... yes
checking for library containing selinux_raw_to_trans_context... -lselinux
checking for CLUTTER... yes
checking for more warnings... no
checking for XRenderFindFormat in -lXrender... yes
checking X11/XF86keysym.h usability... yes
checking X11/XF86keysym.h presence... yes
checking for X11/XF86keysym.h... yes
checking for gconftool-2... /usr/bin/gconftool-2
Using config source xml:merged:/etc/gconf/gconf.xml.defaults for schema installation
Using $(sysconfdir)/gconf/schemas as install directory for schema files
checking for update-mime-database... /usr/bin/update-mime-database
checking for sed... /bin/sed
configure: creating ./config.status
config.status: creating Makefile
config.status: creating cut-n-paste-code/Makefile
config.status: creating cut-n-paste-code/libegg/Makefile
config.status: creating data/Makefile
config.status: creating data/icons/Makefile
config.status: creating data/patterns/Makefile
config.status: creating data/nautilus-computer.desktop.in
config.status: creating data/nautilus-file-management-properties.desktop.in
config.status: creating data/nautilus-home.desktop.in
config.status: creating data/nautilus.desktop.in
config.status: creating data/nautilus-folder-handler.desktop.in
config.status: creating data/nautilus-browser.desktop.in
config.status: creating data/nautilus-autorun-software.desktop.in
config.status: creating docs/Makefile
config.status: creating docs/reference/Makefile
config.status: creating docs/reference/libnautilus-extension/Makefile
config.status: creating docs/reference/libnautilus-extension/version.xml
config.status: creating eel/Makefile
config.status: creating icons/Makefile
config.status: creating libnautilus-private/Makefile
config.status: creating libnautilus-extension/Makefile
config.status: creating libnautilus-extension/libnautilus-extension.pc
config.status: creating libnautilus-extension/libnautilus-extension-uninstalled.pc
config.status: creating m4/Makefile
config.status: creating m4/shave-libtool
config.status: creating m4/shave
config.status: creating po/Makefile.in
config.status: creating src/Makefile
config.status: creating src/file-manager/Makefile
config.status: creating test/Makefile
config.status: creating config.h
config.status: executing depfiles commands
config.status: executing libtool commands
config.status: executing default-1 commands
config.status: executing po/stamp-it commands

nautilus-2.29.1:

    prefix:                 /usr
    source code location:    .
    compiler:        /bin/bash /home/josh/nautilus-clutter-gtklist/m4/shave cc gcc
    tracker support:    no
    beagle support:        no
    xmp support:        yes
    PackageKit support:     yes

    profiling support:      off
    nautilus-extension documentation: no

    clutter view: yes

Now type `make' to compile nautilus

```Which to me looks fine.
Then i type "make" and i get
```
Making all in m4
Making all in eel
  CC    eel-accessibility.o
  CC    eel-alert-dialog.o
  CC    eel-art-extensions.o
  CC    eel-art-gtk-extensions.o
  CC    eel-background.o
eel-background.c: In function ‘free_background_pixmap’:
eel-background.c:217:12: warning: assignment makes pointer from integer without a cast
eel-background.c: In function ‘drawable_get_adjusted_size’:
eel-background.c:334:10: warning: assignment makes pointer from integer without a cast
eel-background.c: In function ‘eel_background_expose’:
eel-background.c:481:5: warning: assignment makes pointer from integer without a cast
eel-background.c: In function ‘set_root_pixmap’:
eel-background.c:679:9: warning: assignment makes pointer from integer without a cast
eel-background.c: In function ‘widget_realized_setup’:
eel-background.c:897:45: warning: comparison between pointer and integer
eel-background.c: In function ‘eel_background_is_dark’:
eel-background.c:1025:2: error: too few arguments to function ‘gnome_bg_is_dark’
/usr/include/gnome-desktop-2.0/libgnomeui/gnome-bg.h:110:18: note: declared here
make[2]: *** [eel-background.lo] Error 1
make[1]: *** [all-recursive] Error 1
make: *** [all] Error 2

```There is an error at the end?
So then i think screw it and say "sudo make install" and i get
```
Making install in m4
Making install in eel
  CC    eel-background.o
eel-background.c: In function ‘free_background_pixmap’:
eel-background.c:217:12: warning: assignment makes pointer from integer without a cast
eel-background.c: In function ‘drawable_get_adjusted_size’:
eel-background.c:334:10: warning: assignment makes pointer from integer without a cast
eel-background.c: In function ‘eel_background_expose’:
eel-background.c:481:5: warning: assignment makes pointer from integer without a cast
eel-background.c: In function ‘set_root_pixmap’:
eel-background.c:679:9: warning: assignment makes pointer from integer without a cast
eel-background.c: In function ‘widget_realized_setup’:
eel-background.c:897:45: warning: comparison between pointer and integer
eel-background.c: In function ‘eel_background_is_dark’:
eel-background.c:1025:2: error: too few arguments to function ‘gnome_bg_is_dark’
/usr/include/gnome-desktop-2.0/libgnomeui/gnome-bg.h:110:18: note: declared here
make[1]: *** [eel-background.lo] Error 1
make: *** [install-recursive] Error 1

```Another error by there.
I finish the instructions and then nothing has changed like it is ment to.

Can some1 please help. I understand if what i have shown you is not enough so if you need anything else just say.
Thanks in advance :D

---

