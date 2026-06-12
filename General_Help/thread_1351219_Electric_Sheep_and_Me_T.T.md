---
title: "Electric Sheep and Me T.T"
date: 2009-12-10
forum: General Help
---

### Post by edward fish on 2009-12-10
Running Ubuntu 8.04 trying to get electric sheep installed and running.

Using following commands in terminal:

sudo wget electricsheep.org/makesheep.sh
sh makesheep.sh

gives me this output:

edward@Cthulhu:~$ sudo wget electricsheep.org/makesheep.sh
[sudo] password for edward: 
--12:11:28--  [http://electricsheep.org/makesheep.sh](http://electricsheep.org/makesheep.sh)
           => `makesheep.sh.2'
Resolving electricsheep.org... 74.207.243.94
Connecting to electricsheep.org|74.207.243.94|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 533 [text/x-sh]

100%[====================================>] 533           --.--K/s             

12:11:29 (27.16 MB/s) - `makesheep.sh.2' saved [533/533]

edward@Cthulhu:~$ sh makesheep.sh
mkdir: cannot create directory `electricsheep-2009-12-10': File exists
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mplayer is already the newest version.
curl is already the newest version.
subversion is already the newest version.
libtool is already the newest version.
Note, selecting libjpeg62-dev instead of libjpeg-dev
libjpeg62-dev is already the newest version.
The following packages were automatically installed and are no longer required:
  libnspr4-dev
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdbus-glib-1-dev is already the newest version.
libgconf2-dev is already the newest version.
libavformat-dev is already the newest version.
The following packages were automatically installed and are no longer required:
  libnspr4-dev
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgnome-menu-dev is already the newest version.
libglade2-dev is already the newest version.
libgnomeui-dev is already the newest version.
The following packages were automatically installed and are no longer required:
  libnspr4-dev
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Checked out revision 1310.
Checked out revision 865.
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
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
checking dependency style of gcc... none
checking for a BSD-compatible install... /usr/bin/install -c
checking whether make sets $(MAKE)... (cached) yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 98304
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for ar... ar
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking how to run the C preprocessor... gcc -E
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
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... no
checking whether to build static libraries... yes
checking for ANSI C header files... (cached) yes
checking for an ANSI C-conforming const... yes
checking for size_t... yes
checking whether time.h and sys/time.h may both be included... yes
checking for deflateInit_ in -lz... yes
checking for png_write_image in -lpng... yes
checking for xmlParseFile in -lxml2... yes
checking whether gcc knows 32-bit __sync_bool_compare_and_swap()... yes
checking whether gcc knows 64-bit __sync_bool_compare_and_swap()... no - try specifying CFLAGS=-march={your_arch}
checking for pthread_create in -lpthread... yes
checking for jpeg_start_compress in -ljpeg... yes
checking for xml2-config... /usr/bin/xml2-config
configure: creating ./config.status
config.status: creating Makefile
config.status: creating flam3.pc
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing libtool commands
make: *** No rule to make target `m4/libtool.m4', needed by `Makefile.in'.  Stop.
make: *** No rule to make target `m4/libtool.m4', needed by `Makefile.in'.  Stop.
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
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
checking dependency style of gcc... none
checking for a BSD-compatible install... /usr/bin/install -c
checking whether make sets $(MAKE)... (cached) yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for X... libraries , headers 
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for an ANSI C-conforming const... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for size_t... yes
checking whether time.h and sys/time.h may both be included... yes
checking sys/mount.h usability... yes
checking sys/mount.h presence... yes
checking for sys/mount.h... yes
checking sys/vfs.h usability... yes
checking sys/vfs.h presence... yes
checking for sys/vfs.h... yes
checking sys/statvfs.h usability... yes
checking sys/statvfs.h presence... yes
checking for sys/statvfs.h... yes
checking for XML_ParserCreate in -lexpat... yes
checking whether setpgrp takes no argument... yes
checking for setproctitle... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for libglade... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating electricsheep.desktop
config.status: creating electricsheep.xml
config.status: creating electricsheep.spec
config.status: creating electricsheep.man
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
make  all-am
make[1]: Entering directory `/home/edward/electricsheep-2009-12-10/client'
gcc -DHAVE_CONFIG_H -I.    -DPACKAGE_DATA_DIR=\"/usr/local/share/electricsheep\" -g -O2 -c electricsheep.c
electricsheep.c:46:35: error: libavformat/avformat.h: No such file or directory
electricsheep.c:133: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
electricsheep.c: In function ‘copy_out_file’:
electricsheep.c:635: error: ‘AVOutputFormat’ undeclared (first use in this function)
electricsheep.c:635: error: (Each undeclared identifier is reported only once
electricsheep.c:635: error: for each function it appears in.)
electricsheep.c:635: error: ‘ofmt’ undeclared (first use in this function)
electricsheep.c:636: error: ‘AVFormatContext’ undeclared (first use in this function)
electricsheep.c:636: error: ‘ictx’ undeclared (first use in this function)
electricsheep.c:664: error: ‘AVCodecContext’ undeclared (first use in this function)
electricsheep.c:664: error: ‘enc’ undeclared (first use in this function)
electricsheep.c:665: error: ‘CODEC_TYPE_VIDEO’ undeclared (first use in this function)
electricsheep.c:675: error: ‘output_ctx’ undeclared (first use in this function)
electricsheep.c:676: error: ‘codec’ undeclared (first use in this function)
electricsheep.c:676: error: ‘icodec’ undeclared (first use in this function)
electricsheep.c:677: error: ‘AVStream’ undeclared (first use in this function)
electricsheep.c:677: error: ‘st’ undeclared (first use in this function)
electricsheep.c:718: error: ‘URL_WRONLY’ undeclared (first use in this function)
electricsheep.c:727: error: ‘AVPacket’ undeclared (first use in this function)
electricsheep.c:727: error: expected ‘;’ before ‘ipkt’
electricsheep.c:728: error: expected ‘;’ before ‘opkt’
electricsheep.c:729: error: ‘ipkt’ undeclared (first use in this function)
electricsheep.c:730: error: ‘opkt’ undeclared (first use in this function)
electricsheep.c:733: error: ‘PKT_FLAG_KEY’ undeclared (first use in this function)
electricsheep.c:734: error: ‘av_destruct_packet’ undeclared (first use in this function)
make[1]: *** [electricsheep.o] Error 1
make[1]: Leaving directory `/home/edward/electricsheep-2009-12-10/client'
make: *** [all] Error 2
gcc -DHAVE_CONFIG_H -I.    -DPACKAGE_DATA_DIR=\"/usr/local/share/electricsheep\" -g -O2 -c electricsheep.c
electricsheep.c:46:35: error: libavformat/avformat.h: No such file or directory
electricsheep.c:133: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
electricsheep.c: In function ‘copy_out_file’:
electricsheep.c:635: error: ‘AVOutputFormat’ undeclared (first use in this function)
electricsheep.c:635: error: (Each undeclared identifier is reported only once
electricsheep.c:635: error: for each function it appears in.)
electricsheep.c:635: error: ‘ofmt’ undeclared (first use in this function)
electricsheep.c:636: error: ‘AVFormatContext’ undeclared (first use in this function)
electricsheep.c:636: error: ‘ictx’ undeclared (first use in this function)
electricsheep.c:664: error: ‘AVCodecContext’ undeclared (first use in this function)
electricsheep.c:664: error: ‘enc’ undeclared (first use in this function)
electricsheep.c:665: error: ‘CODEC_TYPE_VIDEO’ undeclared (first use in this function)
electricsheep.c:675: error: ‘output_ctx’ undeclared (first use in this function)
electricsheep.c:676: error: ‘codec’ undeclared (first use in this function)
electricsheep.c:676: error: ‘icodec’ undeclared (first use in this function)
electricsheep.c:677: error: ‘AVStream’ undeclared (first use in this function)
electricsheep.c:677: error: ‘st’ undeclared (first use in this function)
electricsheep.c:718: error: ‘URL_WRONLY’ undeclared (first use in this function)
electricsheep.c:727: error: ‘AVPacket’ undeclared (first use in this function)
electricsheep.c:727: error: expected ‘;’ before ‘ipkt’
electricsheep.c:728: error: expected ‘;’ before ‘opkt’
electricsheep.c:729: error: ‘ipkt’ undeclared (first use in this function)
electricsheep.c:730: error: ‘opkt’ undeclared (first use in this function)
electricsheep.c:733: error: ‘PKT_FLAG_KEY’ undeclared (first use in this function)
electricsheep.c:734: error: ‘av_destruct_packet’ undeclared (first use in this function)
make: *** [electricsheep.o] Error 1



Can anyone help?

---

### Post by spotspot on 2009-12-13
edit electricsheep.c at line 43 to read:
43
44 #include "ffmpeg/avformat.h"
45
46 /* #include "libavformat/avformat.h" */

---

### Post by t0p on 2009-12-13
Alternatively you can install it from the repositories.  Go to **System > Administration > Synaptic Package Manager** and search for "electricsheep".  Or open a terminal and type in

```
sudo apt-get install electricsheep
```

---

### Post by edward fish on 2009-12-13
Thanks for the help, application has been installed. 

edward@Cthulhu:~$ sudo apt-get install electricsheep
[sudo] password for edward: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libnspr4-dev
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libjpeg-progs xloadimage
The following NEW packages will be installed:
  electricsheep libjpeg-progs xloadimage
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 2917kB of archives.
After this operation, 4014kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main libjpeg-progs 6b-14 [79.4kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe xloadimage 4.1-16 [112kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe electricsheep 2.6.8-9ubuntu1 [2726kB]
Fetched 2917kB in 5s (508kB/s)          
Selecting previously deselected package libjpeg-progs.
(Reading database ... 129469 files and directories currently installed.)
Unpacking libjpeg-progs (from .../libjpeg-progs_6b-14_i386.deb) ...
Selecting previously deselected package xloadimage.
Unpacking xloadimage (from .../xloadimage_4.1-16_i386.deb) ...
Selecting previously deselected package electricsheep.
Unpacking electricsheep (from .../electricsheep_2.6.8-9ubuntu1_i386.deb) ...
Setting up libjpeg-progs (6b-14) ...
Setting up xloadimage (4.1-16) ...

Setting up electricsheep (2.6.8-9ubuntu1) ...


Howerver, in System-> Pref. -> Screensavers it wont show up on the preview, and when the screensaver becomes active it is a blank screen? Any suggestions?

---

### Post by edward fish on 2009-12-13
edward@Cthulhu:~$ electricsheep
please be patient while the first sheep is downloaded...
curl: (6) Couldn't resolve host 'v2d6.sheepserver.net'
lost contact with v2d6.sheepserver.net, cannot retrieve sheep.

---

### Post by spotspot on 2009-12-21
The one in the repositories is obsolete, we have filed this bug to try to get it updated but nothing has happened...??

[https://bugs.launchpad.net/ubuntu/+source/electricsheep/+bug/372040](https://bugs.launchpad.net/ubuntu/+source/electricsheep/+bug/372040)

in the meantime you can compile from source or use the unofficial PPA:

[http://community.electricsheep.org/node/51](http://community.electricsheep.org/node/51)

---

