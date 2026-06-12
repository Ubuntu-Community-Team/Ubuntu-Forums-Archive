---
title: "helpam trying to install audacious from source but"
date: 2010-05-19
forum: General Help
---

### Post by elliotn on 2010-05-19
please help me I am trying to install audacious from a tar.gz 
here is the ./configure output```
elliotn@elliotn-desktop:~/Desktop/audacious-2.3$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
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
checking minix/config.h usability... no
checking minix/config.h presence... no
checking for minix/config.h... no
checking whether it is safe to define __EXTENSIONS__... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking whether we need an implib... no
checking for shared library system... GNU
checking if you are running Apple-GCC... no
checking whether make sets $(MAKE)... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking whether NLS is requested... yes
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for ranlib... ranlib
checking for strerror in -lcposix... no
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking for off_t... yes
checking for size_t... yes
checking for working alloca.h... yes
checking for alloca... yes
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking for sys/param.h... yes
checking for getpagesize... yes
checking for working mmap... yes
checking whether we are using the GNU C Library 2.1 or newer... yes
checking whether integer division by zero raises SIGFPE... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unsigned long long... yes
checking for inttypes.h... yes
checking whether the inttypes.h PRIxNN macros are broken... no
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking argz.h usability... yes
checking argz.h presence... yes
checking for argz.h... yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking nl_types.h usability... yes
checking nl_types.h presence... yes
checking for nl_types.h... yes
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking stddef.h usability... yes
checking stddef.h presence... yes
checking for stddef.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for unistd.h... (cached) yes
checking for sys/param.h... (cached) yes
checking for feof_unlocked... yes
checking for fgets_unlocked... yes
checking for getc_unlocked... yes
checking for getcwd... yes
checking for getegid... yes
checking for geteuid... yes
checking for getgid... yes
checking for getuid... yes
checking for mempcpy... yes
checking for munmap... yes
checking for putenv... yes
checking for setenv... yes
checking for setlocale... yes
checking for stpcpy... yes
checking for strcasecmp... yes
checking for strdup... yes
checking for strtoul... yes
checking for tsearch... yes
checking for __argz_count... yes
checking for __argz_stringify... yes
checking for __argz_next... yes
checking for __fsetlocking... yes
checking for iconv... yes
checking for iconv declaration... install-shextern size_t iconv (iconv_t cd, char * *inbuf, size_t *inbytesleft, char * *outbuf, size_t *outbytesleft);
checking for nl_langinfo and CODESET... yes
checking for LC_MESSAGES... yes
checking for bison... no
checking whether NLS is requested... yes
checking whether included gettext is requested... no
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for style of include used by make... GNU
checking for GNU make... make
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of gcc... none
checking for strerror in -lcposix... (cached) no
checking whether byte ordering is bigendian... no
checking whether ln -s works... yes
checking whether make sets $(MAKE)... (cached) yes
checking for rm... /bin/rm
checking for mv... /bin/mv
checking for cp... /bin/cp
checking for ar... /usr/bin/ar
checking for tr... /usr/bin/tr
checking for ranlib... /usr/bin/ranlib
checking for GLIB... yes
checking for GTHREAD... yes
checking for GTK... yes
checking for PANGO... yes
checking for CAIRO... yes
checking for MOWGLI... yes
checking for LIBMCS... yes
checking SSE2 support... yes
checking altivec.h usability... no
checking altivec.h presence... no
checking for altivec.h... no
checking for unistd.h... (cached) yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking fnmatch.h usability... yes
checking fnmatch.h presence... yes
checking for fnmatch.h... yes
checking for limits.h... (cached) yes
checking wchar.h usability... yes
checking wchar.h presence... yes
checking for wchar.h... yes
checking fts.h usability... yes
checking fts.h presence... yes
checking for fts.h... yes
checking execinfo.h usability... yes
checking execinfo.h presence... yes
checking for execinfo.h... yes
checking sys/signalfd.h usability... yes
checking sys/signalfd.h presence... yes
checking for sys/signalfd.h... yes
checking sys/errno.h usability... yes
checking sys/errno.h presence... yes
checking for sys/errno.h... yes
checking for mkdtemp... yes
checking for getmntinfo... no
checking for statvfs... yes
checking for strtoul... (cached) yes
checking for lrintf... no
checking for signalfd... yes
checking for lstat... yes
checking for audacious... no
checking for DBUS... no
checking for dbus-binding-tool... no
checking for glib-genmarshal... /usr/bin/glib-genmarshal
checking for xml2-config... no
checking for libxml - version >= 2.0.0... no
*** The xml2-config script installed by LIBXML could not be found
*** If libxml was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the XML2_CONFIG environment variable to the
*** full path to xml2-config.
configure: WARNING: *** libxml2 is not installed. XSPF playlist support will not be built. ***
checking for SM... yes
checking if __ELF__ is defined... yes
configure: touching .deps files
configure: creating ./config.status
config.status: creating audacious.pc
config.status: WARNING:  'audacious.pc.in' seems to ignore the --datarootdir setting
config.status: creating audclient.pc
config.status: WARNING:  'audclient.pc.in' seems to ignore the --datarootdir setting
config.status: creating buildsys.mk
config.status: creating extra.mk
config.status: creating man/audtool2.1
config.status: creating man/audacious2.1
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing default-1 commands
config.status: executing depfiles commands

Configuration:

  Install path:                           /usr/local
  Use one plugin dir:                     
  Allow user plugin dir:                  yes

  Additional debugging output:            no
  Automatic character code detection:     yes
  D-Bus support:                          no
  Session management (eggsm)              yes
  XSPF playlists                          no

  SSE2:                                   yes
  AltiVec:                                no

**
** WARNING! DBUS support is disabled. This means that various features
** the user might expect (such as remotely adding files to session via
** commandline) will not work!

```

if I type make it dies make but I see nothing under sounds
if I type make here is the output```
elliotn@elliotn-desktop:~/Desktop/audacious-2.3$ make
Entering directory src.
Entering directory libeggsmclient.
Successfully generated dependencies.
Leaving directory libeggsmclient.
Entering directory libaudcore.
Successfully generated dependencies.
Leaving directory libaudcore.
Entering directory libguess.
Successfully generated dependencies.
Leaving directory libguess.
Entering directory libid3tag.
Successfully generated dependencies.
Leaving directory libid3tag.
Entering directory libaudtag.
Successfully generated dependencies.
Leaving directory libaudtag.
Entering directory audacious.
Successfully generated dependencies.
Leaving directory audacious.
Entering directory libaudgui.
Successfully generated dependencies.
Leaving directory libaudgui.
Entering directory tests.
Leaving directory tests.
Leaving directory src.
Entering directory man.
Leaving directory man.
Entering directory pixmaps.
Leaving directory pixmaps.
Entering directory po.
Leaving directory po.
elliotn@elliotn-desktop:~/Desktop/audacious-2.3$
```


what should I do?

---

### Post by elliotn on 2010-05-19
bump

---

### Post by elliotn on 2010-05-19
my bump again

---

### Post by elliotn on 2010-05-20
bump

---

### Post by Sheerz on 2010-07-18
Installing these libs from the depository should fix your D-Bus problem.
```
sudo apt-get install libdbus-glib-1-dev
```
I'm currently investigating what will enable XSPF playlist support.  "Altivec" is a hardware feature.  It is not required to build the source.

---

### Post by jocko on 2010-07-18
> **elliotn said:**
> please help me I am trying to install audacious from a tar.gz 
here is the ./configure output```
...
checking for audacious... no
checking for DBUS... no
checking for dbus-binding-tool... no
checking for glib-genmarshal... /usr/bin/glib-genmarshal
checking for xml2-config... no
checking for libxml - version >= 2.0.0... no
*** The xml2-config script installed by LIBXML could not be found
*** If libxml was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the XML2_CONFIG environment variable to the
*** full path to xml2-config.
configure: WARNING: *** libxml2 is not installed. XSPF playlist support will not be built. ***
checking for SM... yes
checking if __ELF__ is defined... yes
configure: touching .deps files
configure: creating ./config.status
config.status: creating audacious.pc
config.status: WARNING:  'audacious.pc.in' seems to ignore the --datarootdir setting
config.status: creating audclient.pc
config.status: WARNING:  'audclient.pc.in' seems to ignore the --datarootdir setting
config.status: creating buildsys.mk
config.status: creating extra.mk
config.status: creating man/audtool2.1
config.status: creating man/audacious2.1
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing default-1 commands
config.status: executing depfiles commands

Configuration:

  Install path:                           /usr/local
  Use one plugin dir:                     
  Allow user plugin dir:                  yes

  Additional debugging output:            no
  Automatic character code detection:     yes
  D-Bus support:                          no
  Session management (eggsm)              yes
  XSPF playlists                          no

  SSE2:                                   yes
  AltiVec:                                no

**
** WARNING! DBUS support is disabled. This means that various features
** the user might expect (such as remotely adding files to session via
** commandline) will not work!

```if I type make it dies make but I see nothing under sounds
if I type make here is the output

...

what should I do?
I see nothing really wrong there, make successfully built audacious for you (minus dbus and XSPF[FONT=monospace] playlist support which was not built because you lack the libxml2 and libdbus development headers).

To get the missing headers, run this:
[/FONT]```
sudo apt-get install libdbus-1-dev libxml2-dev
```Then build audacious again:
```
make clean
./configure
make
sudo make install
```

**EDIT:** Ooops. This thread was old. The op probably solved the problem months ago. Let this thread sink back into oblivion...

---

