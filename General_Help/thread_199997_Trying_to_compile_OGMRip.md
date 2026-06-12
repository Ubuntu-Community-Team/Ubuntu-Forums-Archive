---
title: "Trying to compile OGMRip"
date: 2006-06-19
forum: General Help
---

### Post by reclusivemonkey on 2006-06-19
I am trying to compile OGMRip. I've insalled build-essential, and all the necessary packages via synaptic. After ./configure, I get no errors, but after make I get;

```

cc1: warnings being treated as errors
ogmrip-backend.c: In function 'ogmrip_backend_wav_command':
ogmrip-backend.c:328: warning: pointer targets in passing argument 2 of 'ogmrip_codec_get_chapters' differ in signedness
ogmrip-backend.c:328: warning: pointer targets in passing argument 3 of 'ogmrip_codec_get_chapters' differ in signedness
ogmrip-backend.c:353:5: error: missing binary operator before token "2"
ogmrip-backend.c: In function 'ogmrip_backend_acopy_command':
ogmrip-backend.c:397: warning: pointer targets in passing argument 2 of 'ogmrip_codec_get_chapters' differ in signedness
ogmrip-backend.c:397: warning: pointer targets in passing argument 3 of 'ogmrip_codec_get_chapters' differ in signedness
ogmrip-backend.c:417:5: error: missing binary operator before token "2"
ogmrip-backend.c: In function 'ogmrip_backend_xvid_command':
ogmrip-backend.c:692: warning: pointer targets in passing argument 2 of 'ogmrip_codec_get_chapters' differ in signedness
ogmrip-backend.c:692: warning: pointer targets in passing argument 3 of 'ogmrip_codec_get_chapters' differ in signedness
ogmrip-backend.c:711:5: error: missing binary operator before token "2"
ogmrip-backend.c: In function 'ogmrip_backend_lavc_command':
ogmrip-backend.c:798: warning: pointer targets in passing argument 2 of 'ogmrip_codec_get_chapters' differ in signedness
ogmrip-backend.c:798: warning: pointer targets in passing argument 3 of 'ogmrip_codec_get_chapters' differ in signedness
ogmrip-backend.c:817:5: error: missing binary operator before token "2"
ogmrip-backend.c: In function 'ogmrip_backend_x264_command':
ogmrip-backend.c:897: warning: pointer targets in passing argument 2 of 'ogmrip_codec_get_chapters' differ in signedness
ogmrip-backend.c:897: warning: pointer targets in passing argument 3 of 'ogmrip_codec_get_chapters' differ in signedness
ogmrip-backend.c:916:5: error: missing binary operator before token "2"
ogmrip-backend.c:1096:5: error: missing binary operator before token "2"
ogmrip-backend.c: In function 'ogmrip_backend_vobsub_command':
ogmrip-backend.c:1440: warning: pointer targets in passing argument 2 of 'ogmrip_codec_get_chapters' differ in signedness
ogmrip-backend.c:1440: warning: pointer targets in passing argument 3 of 'ogmrip_codec_get_chapters' differ in signedness
ogmrip-backend.c:1453:5: error: missing binary operator before token "2"
make[2]: *** [ogmrip-backend.lo] Error 1
make[2]: Leaving directory `/usr/local/src/ogmrip-0.9.0/libogmrip'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/usr/local/src/ogmrip-0.9.0'
make: *** [all] Error 2

```

Can anyone help me here?

---

### Post by vigleik on 2006-06-19
I'm no expert, but I remember getting similar warnings, and then an error, when compiling other things with the "wrong" c compiler. Here "wrong" means too new. Try installing an older version of gcc and compile against that.

Vigleik

---

### Post by reclusivemonkey on 2006-06-19
[QUOTE=vigleik]I'm no expert, but I remember getting similar warnings, and then an error, when compiling other things with the "wrong" c compiler. Here "wrong" means too new. Try installing an older version of gcc and compile against that.

Vigleik[/QUOTE]

Thanks for the post dude, but I just spent about four hours on IRC with the "Ubuntu Masters of the Universe" and got nowhere. Back to Slack I think for me.

---

### Post by ap9er on 2006-06-28
Yeah, I seem to be getting a similar error. Tried downgrading GCC to older versions to no avail.
Anyone can help?

```
make[2]: Leaving directory `/home/andreas/ogmrip-0.10.0-rc1/libogmjob'
Making all in libogmrip
make[2]: Entering directory `/home/andreas/ogmrip-0.10.0-rc1/libogmrip'
if /bin/sh ../libtool --mode=compile gcc-4.0 -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/local/include/glib-2.0 -I/usr/local/lib/glib-2.0/include -I/usr/include/libxml2    -I../libogmjob -I../libogmdvd -DOGMRIP_DATA_DIR=\""/usr/local/share"\"  -I/usr/local/include  -g -O2 -I/usr/local/include -I.. -Wall -Werror -MT ogmrip-backend.lo -MD -MP -MF ".deps/ogmrip-backend.Tpo" -c -o ogmrip-backend.lo ogmrip-backend.c; \
        then mv -f ".deps/ogmrip-backend.Tpo" ".deps/ogmrip-backend.Plo"; else rm -f ".deps/ogmrip-backend.Tpo"; exit 1; fi
 gcc-4.0 -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/local/include/glib-2.0 -I/usr/local/lib/glib-2.0/include -I/usr/include/libxml2 -I../libogmjob -I../libogmdvd -DOGMRIP_DATA_DIR=\"/usr/local/share\" -I/usr/local/include -g -O2 -I/usr/local/include -I.. -Wall -Werror -MT ogmrip-backend.lo -MD -MP -MF .deps/ogmrip-backend.Tpo -c ogmrip-backend.c  -fPIC -DPIC -o .libs/ogmrip-backend.o
ogmrip-backend.c:590:5: error: missing binary operator before token "2"
ogmrip-backend.c:669:5: error: missing binary operator before token "2"
ogmrip-backend.c:1019:5: error: missing binary operator before token "2"
ogmrip-backend.c:1135:5: error: missing binary operator before token "2"
ogmrip-backend.c:1243:5: error: missing binary operator before token "2"
ogmrip-backend.c:1472:5: error: missing binary operator before token "2"
ogmrip-backend.c:1994:5: error: missing binary operator before token "2"
make[2]: *** [ogmrip-backend.lo] Error 1
make[2]: Leaving directory `/home/andreas/ogmrip-0.10.0-rc1/libogmrip'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/andreas/ogmrip-0.10.0-rc1'
make: *** [all] Error 2

```

---

### Post by billl on 2006-07-06
Hi,

This is so because OGMRip cannot figure out the version of mplayer. If you run mplayer without options, you'll get something starting with "MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team" which is neither how official mplayer releases nor CVS/SVN versions are numbered. I can provide a fix, but I'd like to make the correction almost generic. I then need to know the rules the maintainers use to number mplayer versions on ubuntu.

Cheers,

Olivier

---

### Post by reclusivemonkey on 2006-07-07
> **billl said:**
> Hi,

This is so because OGMRip cannot figure out the version of mplayer. If you run mplayer without options, you'll get something starting with "MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team" which is neither how official mplayer releases nor CVS/SVN versions are numbered. I can provide a fix, but I'd like to make the correction almost generic. I then need to know the rules the maintainers use to number mplayer versions on ubuntu.

Cheers,

Olivier

Wow! I couldn't of hoped for a better expert to reply on OGMRip! :-) Thanks for taking the time to post Oliver. Whenever I compiled on Slack I used to use a standard version of MPlayer as per your instructions. I didn't really want to try compiling my own MPlayer on Ubuntu as this defeats the object of Ubuntu for me. If you head over to the Ubuntu Masters of the Universe IRC channel, I am pretty sure they will be able to fill you in on the information you need. Again, many thanks for replying to my thread. OGMRip is a fantastic application which many more people need to be made aware of.

---

### Post by guillaume1 on 2006-07-08
Hi Billl,
An honnor to have you around!
I come from the french forum and tried to compile **ogmrip** on my machine. I managed to build a **deb** but I can't find any axecutable.
The **./configure** shown above tells I won't have a **GUI**:

```
gui@home:~/deb-tar-gz-codecs/OGMRIP/ogmrip_10.0-rc1/ogmrip-0.10.0-rc1$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
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
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... g77
checking whether we are using the GNU Fortran 77 compiler... yes
checking whether g77 accepts -g... yes
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking for correct ltmain.sh version... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking for g77 option to produce PIC... -fPIC
checking if g77 PIC flag -fPIC works... yes
checking if g77 static flag -static works... yes
checking if g77 supports -c -o file.o... yes
checking whether the g77 linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking for ANSI C header files... (cached) yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking sys/statvfs.h usability... yes
checking sys/statvfs.h presence... yes
checking for sys/statvfs.h... yes
checking mntent.h usability... yes
checking mntent.h presence... yes
checking for mntent.h... yes
checking sys/mnttab.h usability... no
checking sys/mnttab.h presence... no
checking for sys/mnttab.h... no
checking sys/vfstab.h usability... no
checking sys/vfstab.h presence... no
checking for sys/vfstab.h... no
checking sys/cdio.h usability... no
checking sys/cdio.h presence... no
checking for sys/cdio.h... no
checking for statvfs... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for OGMRIP... yes
checking for gsed... no
checking for sed... /bin/sed
checking for GUI... checking for HAL... checking for ENCHANT... checking for cam_open_spec_device in -lcam... no
checking for DVDOpen in -ldvdread... yes
checking for mplayer... /usr/local/bin/mplayer
checking for mencoder... /usr/local/bin/mencoder
checking for ogmmerge... /usr/bin/ogmmerge
checking for ogmsplit... /usr/bin/ogmsplit
checking for oggenc... /usr/local/bin/oggenc
checking for lame... /usr/bin/lame
checking for XviD support... yes
checking for Lavc support... yes
checking for x264 support... no
checking for Lavf support... no
checking for DTS support... yes
checking for faac... no
checking for mkvmerge... no
checking for THEORA... yes
checking for gocr... /usr/bin/gocr
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
checking for dcgettext... no
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for catalogs to be installed...  fr en pl de
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for iconv... /usr/bin/iconv
checking for msgfmt... /usr/bin/msgfmt
checking for msgmerge... /usr/bin/msgmerge
checking for xgettext... /usr/bin/xgettext
checking for glib-genmarshal... /usr/bin/glib-genmarshal
checking for gconftool-2... /usr/bin/gconftool-2
Using config source xml:merged:/etc/gconf/gconf.xml.defaults for schema installation
Using $(sysconfdir)/gconf/schemas as install directory for schema files
configure: creating ./config.status
config.status: creating src/Makefile
config.status: creating subrip/Makefile
config.status: creating dvdcpy/Makefile
config.status: creating theoraenc/Makefile
config.status: creating libogmdvd/Makefile
config.status: creating libogmdvd-gtk/Makefile
config.status: creating libogmjob/Makefile
config.status: creating libogmrip/Makefile
config.status: creating libbacon/Makefile
config.status: creating data/Makefile
config.status: creating data/ogmdvd.pc
config.status: creating data/ogmjob.pc
config.status: creating data/ogmrip.pc
config.status: creating po/Makefile.in
config.status: creating Makefile
config.status: creating config.h
config.status: executing depfiles commands
config.status: executing default-1 commands
config.status: executing intltool commands
config.status: executing libogmrip/ogmrip.h commands
config.status: executing po/stamp-it commands
configure: OGMRip was configured with the following options:
configure:    The GUI will not be build
configure:    HAL support disabled
configure:    Matroska support disabled
configure:    Lavf support disabled
configure:    X264 support disabled
configure: ** Theora support enabled
configure: ** DTS support enabled
configure:    AAC support disabled
configure: ** SRT support enabled
configure:    Enchant support disabled
gui@home:~/deb-tar-gz-codecs/OGMRIP/ogmrip_10.0-rc1/ogmrip-0.10.0-rc1$

```

I don't understand, and **synaptic** shows a properly installed **deb**. I'd love to have **ogmrip** on my **Dapper** though!

---

### Post by guillaume1 on 2006-07-10
Hi evrybody,

I finally managed to force **./configure** to provide **ogmrip** with a **GUI**, but now I have a new error in **make**:

```
cc1: warnings being treated as errors
ogmrip-main.c: Dans la fonction «ogmrip_main_mklog» :
ogmrip-main.c:227: attention : implicit declaration of function «ogmrip_get_vide o_codec_type»
make[2]: *** [ogmrip-main.o] Erreur 1
make[2]: quittant le répertoire « /home/gui/deb-tar-gz-codecs/OGMRIP/ogmrip_0.10 .0-rc2/ogmrip-0.10.0-rc2/src »
make[1]: *** [all-recursive] Erreur 1
make[1]: quittant le répertoire « /home/gui/deb-tar-gz-codecs/OGMRIP/ogmrip_0.10 .0-rc2/ogmrip-0.10.0-rc2 »
make: *** [all] Erreur 2

```

and in **ogmrip-main.c** line 227 I have:
**type = ogmrip_get_video_codec_type (codec);**

Can you help me ?

---

### Post by billl on 2006-07-10
This was a bug, actually. It's been fixed in subversion.

Cheers,

Olivier

---

### Post by guillaume1 on 2006-07-10
Thanks for the hint. It works fine now. I am actally encoding a dvd and feverishly waiting for the result. I still have one problem though: I can't select two different languages. I can see the **+** sign beside the language selection but it refuses to work.
missed something ?

cheers,

Guillaume.

---

### Post by billl on 2006-07-10
AVI and MP4 only support one audio stream and one subtitles streams. OGM and matroska supports several streams of each kind.

Cheers,

Olivier

---

### Post by guillaume1 on 2006-07-10
Thanks again.
I have just finished encoding a dvd. It took 3 hours and gives an AVI file of good quality but without any sound. I chose the mp3 option. (I know mp3 is evil but it was for testing :D ).

It's late already and I'll have a closer look tomorrow.

An other point: the Guillaume1 you meet on this forum is the same you have helped on the french forum. I'd rather have this exchange continued on the french side since my english is kink of poor and I am much at ease in my native language.

Last point before bed: I have on my posession a couple of Bivx (two audio streams) and in my "youth" I use Rippack under windows that provided AVIs with two audio streams. I am not an expert on the matter but I think it can be possible. 

Meet you abroad.

Good night.

Guillaume.

---

### Post by billl on 2006-07-11
> **guillaume1 said:**
> I have just finished encoding a dvd. It took 3 hours and gives an AVI file of good quality but without any sound. I chose the mp3 option. (I know mp3 is evil but it was for testing :D ).
There is a bug in rc2. Mp3 encoding does not work most of the time. There is a fix in subversion.

> **guillaume1 said:**
> An other point: the Guillaume1 you meet on this forum is the same you have helped on the french forum. I'd rather have this exchange continued on the french side since my english is kink of poor and I am much at ease in my native language.
No problemo.

> **guillaume1 said:**
> Last point before bed: I have on my posession a couple of Bivx (two audio streams) and in my "youth" I use Rippack under windows that provided AVIs with two audio streams. I am not an expert on the matter but I think it can be possible.
True, but it is something like a hack.

Cheers,

Olivier

---

### Post by guillaume1 on 2006-07-11
Hello,

To Reclusivemonkey: There is a deb available at
[http://prdownloads.sourceforge.net/ogmrip/ogmrip_0.10.0-rc2-1_i386.deb?download]("http://prdownloads.sourceforge.net/ogmrip/ogmrip_0.10.0-rc2-1_i386.deb?download")

**Hugh Chen** did it. Thanks to him.

Thanks to you too Bill for making it possible.

bye.
Guillaume.

---

### Post by !nkubus on 2006-07-11
I tryed it and it dosen't read the DVD directly I had to tak the video_ts (wasn't much of a trouble). And the encoding never start it crash at some point but dosen't warn the user. The cropping window dosen't work either. So I say wait a bit more. I'm sure it's a Mplayer version issue as the one in ubuntu is a bit outdated :(

---

### Post by billl on 2006-07-12
The ubuntu dapper package does not seem to be completely functional. I'm in touch with the package maintainer to try to fix things.

Cheers,

Olivier

---

### Post by reclusivemonkey on 2006-07-12
> **guillaume1 said:**
> Hello,

To Reclusivemonkey: There is a deb available at
[http://prdownloads.sourceforge.net/ogmrip/ogmrip_0.10.0-rc2-1_i386.deb?download]("http://prdownloads.sourceforge.net/ogmrip/ogmrip_0.10.0-rc2-1_i386.deb?download")

**Hugh Chen** did it. Thanks to him.

Thanks to you too Bill for making it possible.

bye.
Guillaume.

Many thanks for letting me know guillaume. Viva La France! :D

---

### Post by billl on 2006-07-13
A new deb is available here: [http://prdownloads.sourceforge.net/ogmrip/ogmrip_0.10.0-rc2-3_i386.deb?download](http://prdownloads.sourceforge.net/ogmrip/ogmrip_0.10.0-rc2-3_i386.deb?download), thanks to Hugh Chen.

Cheers,

Olivier

---

