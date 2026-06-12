---
title: "trying to install latest deadbeef version through git clone and having problems with"
date: 2010-08-12
forum: General Help
---

### Post by shantiq on 2010-08-12
first step did


```
git clone git://deadbeef.git.sourceforge.net/gitroot/deadbeef/deadbeef

```


which gives me a deadbeef folder in my home folder with latest version therein

next steps are 

```
./autogen.sh
./configure
make
sudo make install
```


i installed   automake all six versions in the synaptic as some are different as to what they can do



also  libtool, gettext



and this is what i get   **any thoughts?**   am i missing a program or 2 to install from git?


```
shantiq@shantiq-desktop:~$ cd ./deadbeef
shantiq@shantiq-desktop:~/deadbeef$ ./autogen.sh
configure.ac:17: warning: macro `AM_GNU_GETTEXT' not found in library
libtoolize: warning: no serial number on `/usr/share/aclocal/libtool.m4', not copying.
libtoolize: putting macros in AC_CONFIG_MACRO_DIR, `m4'.
libtoolize: You should add the contents of `m4/ltoptions.m4' to `aclocal.m4'.
libtoolize: You should add the contents of `m4/ltsugar.m4' to `aclocal.m4'.
libtoolize: You should add the contents of `m4/ltversion.m4' to `aclocal.m4'.
libtoolize: You should add the contents of `m4/lt~obsolete.m4' to `aclocal.m4'.
plugins/aac/Makefile.am:3: Libtool library used but `LIBTOOL' is undefined
plugins/aac/Makefile.am:3:   The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
plugins/aac/Makefile.am:3:   to `configure.ac' and run `aclocal' and `autoconf' again.
plugins/aac/Makefile.am:3:   If `AC_PROG_LIBTOOL' is in `configure.ac', make sure
plugins/aac/Makefile.am:3:   its definition is in aclocal's search path.
plugins/adplug/Makefile.am:5: Libtool library used but `LIBTOOL' is undefined
plugins/adplug/Makefile.am:5:   The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
plugins/adplug/Makefile.am:5:   to `configure.ac' and run `aclocal' and `autoconf' again.
plugins/adplug/Makefile.am:5:   If `AC_PROG_LIBTOOL' is in `configure.ac', make sure
plugins/adplug/Makefile.am:5:   its definition is in aclocal's search path.
plugins/alsa/Makefile.am:3: Libtool library used but `LIBTOOL' is undefined
plugins/alsa/Makefile.am:3:   The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
plugins/alsa/Makefile.am:3:   to `configure.ac' and run `aclocal' and `autoconf' again.
plugins/alsa/Makefile.am:3:   If `AC_PROG_LIBTOOL' is in `configure.ac', make sure
plugins/alsa/Makefile.am:3:   its definition is in aclocal's search path.
plugins/ao/Makefile.am:3: Libtool library used but `LIBTOOL' is undefined
plugins/ao/Makefile.am:3:   The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
plugins/ao/Makefile.am:3:   to `configure.ac' and run `aclocal' and `autoconf' again.
plugins/ao/Makefile.am:3:   If `AC_PROG_LIBTOOL' is in `configure.ac', make sure
plugins/ao/Makefile.am:3:   its definition is in aclocal's search path.
plugins/artwork/Makefile.am:3: Libtool library used but `LIBTOOL' is undefined
plugins/artwork/Makefile.am:3:   The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
plugins/artwork/Makefile.am:3:   to `configure.ac' and run `aclocal' and `autoconf' again.
plugins/artwork/Makefile.am:3:   If `AC_PROG_LIBTOOL' is in `configure.ac', make sure
plugins/artwork/Makefile.am:3:   its definition is in aclocal's search path.
plugins/cdda/Makefile.am:3: Libtool library used but `LIBTOOL' is undefined
plugins/cdda/Makefile.am:3:   The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
plugins/cdda/Makefile.am:3:   to `configure.ac' and run `aclocal' and `autoconf' again.
plugins/cdda/Makefile.am:3:   If `AC_PROG_LIBTOOL' is in `configure.ac', make sure
plugins/cdda/Makefile.am:3:   its definition is in aclocal's search path.
plugins/dca/Makefile.am:3: Libtool library used but `LIBTOOL' is undefined
plugins/dca/Makefile.am:3:   The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
plugins/dca/Makefile.am:3:   to `configure.ac' and run `aclocal' and `autoconf' again.
plugins/dca/Makefile.am:3:   If `AC_PROG_LIBTOOL' is in `configure.ac', make sure
plugins/dca/Makefile.am:3:   its definition is in aclocal's search path.
plugins/dumb/Makefile.am:6: Libtool library used but `LIBTOOL' is undefined
plugins/dumb/Makefile.am:6:   The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
plugins/dumb/Makefile.am:6:   to `configure.ac' and run `aclocal' and `autoconf' again.
plugins/dumb/Makefile.am:6:   If `AC_PROG_LIBTOOL' is in `configure.ac', make sure
plugins/dumb/Makefile.am:6:   its definition is in aclocal's search path.
plugins/ffap/Makefile.am:3: Libtool library used but `LIBTOOL' is undefined
plugins/ffap/Makefile.am:3:   The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
plugins/ffap/Makefile.am:3:   to `configure.ac' and run `aclocal' and `autoconf' again.
plugins/ffap/Makefile.am:3:   If `AC_PROG_LIBTOOL' is in `configure.ac', make sure
plugins/ffap/Makefile.am:3:   its definition is in aclocal's search path.
plugins/ffmpeg/Makefile.am:3: Libtool library used but `LIBTOOL' is undefined
plugins/ffmpeg/Makefile.am:3:   The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
plugins/ffmpeg/Makefile.am:3:   to `configure.ac' and run `aclocal' and `autoconf' again.
plugins/ffmpeg/Makefile.am:3:   If `AC_PROG_LIBTOOL' is in `configure.ac', make sure
plugins/ffmpeg/Makefile.am:3:   its definition is in aclocal's search path.
plugins/flac/Makefile.am:3: Libtool library used but `LIBTOOL' is undefined
plugins/flac/Makefile.am:3:   The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
plugins/flac/Makefile.am:3:   to `configure.ac' and run `aclocal' and `autoconf' again.
plugins/flac/Makefile.am:3:   If `AC_PROG_LIBTOOL' is in `configure.ac', make sure
plugins/flac/Makefile.am:3:   its definition is in aclocal's search path.
plugins/gme/Makefile.am:11: Libtool library used but `LIBTOOL' is undefined
plugins/gme/Makefile.am:11:   The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
plugins/gme/Makefile.am:11:   to `configure.ac' and run `aclocal' and `autoconf' again.
plugins/gme/Makefile.am:11:   If `AC_PROG_LIBTOOL' is in `configure.ac', make sure
plugins/gme/Makefile.am:11:   its definition is in aclocal's search path.
plugins/gtkui/Makefile.am:3: Libtool library used but `LIBTOOL' is undefined
plugins/gtkui/Makefile.am:3:   The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
plugins/gtkui/Makefile.am:3:   to `configure.ac' and run `aclocal' and `autoconf' again.
plugins/gtkui/Makefile.am:3:   If `AC_PROG_LIBTOOL' is in `configure.ac', make sure
plugins/gtkui/Makefile.am:3:   its definition is in aclocal's search path.
plugins/hotkeys/Makefile.am:3: Libtool library used but `LIBTOOL' is undefined
plugins/hotkeys/Makefile.am:3:   The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
plugins/hotkeys/Makefile.am:3:   to `configure.ac' and run `aclocal' and `autoconf' again.
plugins/hotkeys/Makefile.am:3:   If `AC_PROG_LIBTOOL' is in `configure.ac', make sure
plugins/hotkeys/Makefile.am:3:   its definition is in aclocal's search path.
plugins/lastfm/Makefile.am:3: Libtool library used but `LIBTOOL' is undefined
plugins/lastfm/Makefile.am:3:   The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
plugins/lastfm/Makefile.am:3:   to `configure.ac' and run `aclocal' and `autoconf' again.
plugins/lastfm/Makefile.am:3:   If `AC_PROG_LIBTOOL' is in `configure.ac', make sure
plugins/lastfm/Makefile.am:3:   its definition is in aclocal's search path.
plugins/mms/Makefile.am:3: Libtool library used but `LIBTOOL' is undefined
plugins/mms/Makefile.am:3:   The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
plugins/mms/Makefile.am:3:   to `configure.ac' and run `aclocal' and `autoconf' again.
plugins/mms/Makefile.am:3:   If `AC_PROG_LIBTOOL' is in `configure.ac', make sure
plugins/mms/Makefile.am:3:   its definition is in aclocal's search path.
plugins/mpgmad/Makefile.am:3: Libtool library used but `LIBTOOL' is undefined
plugins/mpgmad/Makefile.am:3:   The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
plugins/mpgmad/Makefile.am:3:   to `configure.ac' and run `aclocal' and `autoconf' again.
plugins/mpgmad/Makefile.am:3:   If `AC_PROG_LIBTOOL' is in `configure.ac', make sure
plugins/mpgmad/Makefile.am:3:   its definition is in aclocal's search path.
plugins/musepack/Makefile.am:3: Libtool library used but `LIBTOOL' is undefined
plugins/musepack/Makefile.am:3:   The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
plugins/musepack/Makefile.am:3:   to `configure.ac' and run `aclocal' and `autoconf' again.
plugins/musepack/Makefile.am:3:   If `AC_PROG_LIBTOOL' is in `configure.ac', make sure
plugins/musepack/Makefile.am:3:   its definition is in aclocal's search path.
plugins/notify/Makefile.am:3: Libtool library used but `LIBTOOL' is undefined
plugins/notify/Makefile.am:3:   The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
plugins/notify/Makefile.am:3:   to `configure.ac' and run `aclocal' and `autoconf' again.
plugins/notify/Makefile.am:3:   If `AC_PROG_LIBTOOL' is in `configure.ac', make sure
plugins/notify/Makefile.am:3:   its definition is in aclocal's search path.
plugins/nullout/Makefile.am:3: Libtool library used but `LIBTOOL' is undefined
plugins/nullout/Makefile.am:3:   The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
plugins/nullout/Makefile.am:3:   to `configure.ac' and run `aclocal' and `autoconf' again.
plugins/nullout/Makefile.am:3:   If `AC_PROG_LIBTOOL' is in `configure.ac', make sure
plugins/nullout/Makefile.am:3:   its definition is in aclocal's search path.
plugins/oss/Makefile.am:3: Libtool library used but `LIBTOOL' is undefined
plugins/oss/Makefile.am:3:   The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
plugins/oss/Makefile.am:3:   to `configure.ac' and run `aclocal' and `autoconf' again.
plugins/oss/Makefile.am:3:   If `AC_PROG_LIBTOOL' is in `configure.ac', make sure
plugins/oss/Makefile.am:3:   its definition is in aclocal's search path.
plugins/pulse/Makefile.am:3: Libtool library used but `LIBTOOL' is undefined
plugins/pulse/Makefile.am:3:   The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
plugins/pulse/Makefile.am:3:   to `configure.ac' and run `aclocal' and `autoconf' again.
plugins/pulse/Makefile.am:3:   If `AC_PROG_LIBTOOL' is in `configure.ac', make sure
plugins/pulse/Makefile.am:3:   its definition is in aclocal's search path.
plugins/shellexec/Makefile.am:3: Libtool library used but `LIBTOOL' is undefined
plugins/shellexec/Makefile.am:3:   The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
plugins/shellexec/Makefile.am:3:   to `configure.ac' and run `aclocal' and `autoconf' again.
plugins/shellexec/Makefile.am:3:   If `AC_PROG_LIBTOOL' is in `configure.ac', make sure
plugins/shellexec/Makefile.am:3:   its definition is in aclocal's search path.
plugins/shn/Makefile.am:3: Libtool library used but `LIBTOOL' is undefined
plugins/shn/Makefile.am:3:   The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
plugins/shn/Makefile.am:3:   to `configure.ac' and run `aclocal' and `autoconf' again.
plugins/shn/Makefile.am:3:   If `AC_PROG_LIBTOOL' is in `configure.ac', make sure
plugins/shn/Makefile.am:3:   its definition is in aclocal's search path.
plugins/sid/Makefile.am:8: Libtool library used but `LIBTOOL' is undefined
plugins/sid/Makefile.am:8:   The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
plugins/sid/Makefile.am:8:   to `configure.ac' and run `aclocal' and `autoconf' again.
plugins/sid/Makefile.am:8:   If `AC_PROG_LIBTOOL' is in `configure.ac', make sure
plugins/sid/Makefile.am:8:   its definition is in aclocal's search path.
plugins/sndfile/Makefile.am:3: Libtool library used but `LIBTOOL' is undefined
plugins/sndfile/Makefile.am:3:   The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
plugins/sndfile/Makefile.am:3:   to `configure.ac' and run `aclocal' and `autoconf' again.
plugins/sndfile/Makefile.am:3:   If `AC_PROG_LIBTOOL' is in `configure.ac', make sure
plugins/sndfile/Makefile.am:3:   its definition is in aclocal's search path.
plugins/supereq/Makefile.am:3: Libtool library used but `LIBTOOL' is undefined
plugins/supereq/Makefile.am:3:   The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
plugins/supereq/Makefile.am:3:   to `configure.ac' and run `aclocal' and `autoconf' again.
plugins/supereq/Makefile.am:3:   If `AC_PROG_LIBTOOL' is in `configure.ac', make sure
plugins/supereq/Makefile.am:3:   its definition is in aclocal's search path.
plugins/tta/Makefile.am:6: Libtool library used but `LIBTOOL' is undefined
plugins/tta/Makefile.am:6:   The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
plugins/tta/Makefile.am:6:   to `configure.ac' and run `aclocal' and `autoconf' again.
plugins/tta/Makefile.am:6:   If `AC_PROG_LIBTOOL' is in `configure.ac', make sure
plugins/tta/Makefile.am:6:   its definition is in aclocal's search path.
plugins/vfs_curl/Makefile.am:3: Libtool library used but `LIBTOOL' is undefined
plugins/vfs_curl/Makefile.am:3:   The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
plugins/vfs_curl/Makefile.am:3:   to `configure.ac' and run `aclocal' and `autoconf' again.
plugins/vfs_curl/Makefile.am:3:   If `AC_PROG_LIBTOOL' is in `configure.ac', make sure
plugins/vfs_curl/Makefile.am:3:   its definition is in aclocal's search path.
plugins/vorbis/Makefile.am:3: Libtool library used but `LIBTOOL' is undefined
plugins/vorbis/Makefile.am:3:   The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
plugins/vorbis/Makefile.am:3:   to `configure.ac' and run `aclocal' and `autoconf' again.
plugins/vorbis/Makefile.am:3:   If `AC_PROG_LIBTOOL' is in `configure.ac', make sure
plugins/vorbis/Makefile.am:3:   its definition is in aclocal's search path.
plugins/vtx/Makefile.am:3: Libtool library used but `LIBTOOL' is undefined
plugins/vtx/Makefile.am:3:   The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
plugins/vtx/Makefile.am:3:   to `configure.ac' and run `aclocal' and `autoconf' again.
plugins/vtx/Makefile.am:3:   If `AC_PROG_LIBTOOL' is in `configure.ac', make sure
plugins/vtx/Makefile.am:3:   its definition is in aclocal's search path.
plugins/wavpack/Makefile.am:3: Libtool library used but `LIBTOOL' is undefined
plugins/wavpack/Makefile.am:3:   The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
plugins/wavpack/Makefile.am:3:   to `configure.ac' and run `aclocal' and `autoconf' again.
plugins/wavpack/Makefile.am:3:   If `AC_PROG_LIBTOOL' is in `configure.ac', make sure
plugins/wavpack/Makefile.am:3:   its definition is in aclocal's search path.
plugins/wildmidi/Makefile.am:6: Libtool library used but `LIBTOOL' is undefined
plugins/wildmidi/Makefile.am:6:   The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
plugins/wildmidi/Makefile.am:6:   to `configure.ac' and run `aclocal' and `autoconf' again.
plugins/wildmidi/Makefile.am:6:   If `AC_PROG_LIBTOOL' is in `configure.ac', make sure
plugins/wildmidi/Makefile.am:6:   its definition is in aclocal's search path.
shantiq@shantiq-desktop:~/deadbeef$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
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
checking minix/config.h usability... no
checking minix/config.h presence... no
checking for minix/config.h... no
checking whether it is safe to define __EXTENSIONS__... yes
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for ANSI C header files... (cached) yes
./configure: line 5433: AC_PROG_LIBTOOL: command not found
checking whether byte ordering is bigendian... no
./configure: line 5659: AM_GNU_GETTEXT: command not found
./configure: line 5661: syntax error near unexpected token `0.40.0'
./configure: line 5661: `IT_PROG_INTLTOOL(0.40.0)'
shantiq@shantiq-desktop:~/deadbeef$ 

```

---

### Post by Djzn.BR on 2010-09-07
[http://sourceforge.net/apps/mediawiki/deadbeef/index.php?title=Installing:Ubuntu](http://sourceforge.net/apps/mediawiki/deadbeef/index.php?title=Installing:Ubuntu)

Install build-essential package plus all the packages listed in first step in link above. After that, redo the git step you wrote.

---

### Post by shantiq on 2010-09-08
thank you djzn it was all solved on a [parallel post]("http://ubuntuforums.org/showthread.php?t=1551641")

---

