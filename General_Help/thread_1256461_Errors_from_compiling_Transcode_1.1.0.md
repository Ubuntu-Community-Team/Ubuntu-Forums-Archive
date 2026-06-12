---
title: "Errors from compiling Transcode 1.1.0"
date: 2009-09-02
forum: General Help
---

### Post by jhcheslik21 on 2009-09-02
Hello.

I am trying to compile this transcode build, verison 1.1.0 from [http://www.transcoding.org/cgi-bin/transcode](http://www.transcoding.org/cgi-bin/transcode).

When I got to ./configure I got those errors ...

> ERROR: requirement failed: cannot compile ffmpeg/avformat.h
ffmpeg/avformat.h can be found in the following packages:
  libavformat  [http://www.ffmpeg.org/](http://www.ffmpeg.org/)

ERROR: requirement failed: cannot link against libavformat
libavformat can be found in the following packages:
  libavformat  [http://www.ffmpeg.org/](http://www.ffmpeg.org/)

ERROR: requirement failed: cannot compile mpeg2dec/mpeg2.h
mpeg2dec/mpeg2.h can be found in the following packages:
  mpeg2dec  [http://libmpeg2.sourceforge.net/](http://libmpeg2.sourceforge.net/)

ERROR: requirement failed: cannot link against libmpeg2
libmpeg2 can be found in the following packages:
  mpeg2dec  [http://libmpeg2.sourceforge.net/](http://libmpeg2.sourceforge.net/)

ERROR: option '--enable-libdvdread' failed: cannot link against libdvdread
libdvdread can be found in the following packages:
  libdvdread  [http://www.dtek.chalmers.se/groups/dvd/downloads.shtml](http://www.dtek.chalmers.se/groups/dvd/downloads.shtml)From what I read in the forum, it is said that I should uninstall and then compile my own ffmpeg and another such libraries, is that right? Also I'm confused about adding '--enable', why should I do that, what is its purpose? Can anyone help me with this one? Thanks.

Joe

---

### Post by Bachstelze on 2009-09-02
You need to install some dependencies:

```
sudo apt-get install libavformat-dev libmpeg2-4-dev libdvdread-dev
```

If that doesn't work, then yes, you'll probably need to compile ffmpeg. Don't worry though, it's not that hard. About the --enable options, as their name implies, they enable features of the program that are disabled by default.

---

### Post by jhcheslik21 on 2009-09-02
Okay, I did your sudo apt-get install ---

And now those are the only errors message I have left.

> ERROR: requirement failed: cannot compile ffmpeg/avformat.h
ffmpeg/avformat.h can be found in the following packages:
  libavformat  [http://www.ffmpeg.org/](http://www.ffmpeg.org/)

ERROR: requirement failed: cannot link against libavformat
libavformat can be found in the following packages:
  libavformat  [http://www.ffmpeg.org/](http://www.ffmpeg.org/)So, I think it is pretty obvious that I'll have to compile and build a new ffmpeg. I hope that'll work.

Thanks for fast reply.

Oh, by the way, should I uninstall the ffmpeg first? From the Synaptic Package Manager?

---

### Post by Bachstelze on 2009-09-02
> **jhcheslik21 said:**
> 
So, I think it is pretty obvious that I'll have to compile and build a new ffmpeg. I hope that'll work.

Actually, no, that probably won't work either. The configure script is looking for avformat.h in the wrong place. Please paste the output of

```
./configure --help
```

---

### Post by jhcheslik21 on 2009-09-02
Wow.

Long list. If that's what you needed...

```
`configure' configures transcode 1.1.0 to adapt to many kinds of systems.

Usage: ./configure [OPTION]... [VAR=VALUE]...

To assign environment variables (e.g., CC, CFLAGS...), specify them as
VAR=VALUE.  See below for descriptions of some of the useful variables.

Defaults for the options are specified in brackets.

Configuration:
  -h, --help              display this help and exit
      --help=short        display options specific to this package
      --help=recursive    display the short help of all the included packages
  -V, --version           display version information and exit
  -q, --quiet, --silent   do not print `checking...' messages
      --cache-file=FILE   cache test results in FILE [disabled]
  -C, --config-cache      alias for `--cache-file=config.cache'
  -n, --no-create         do not create output files
      --srcdir=DIR        find the sources in DIR [configure dir or `..']

Installation directories:
  --prefix=PREFIX         install architecture-independent files in PREFIX
              [/usr/local]
  --exec-prefix=EPREFIX   install architecture-dependent files in EPREFIX
              [PREFIX]

By default, `make install' will install all the files in
`/usr/local/bin', `/usr/local/lib' etc.  You can specify
an installation prefix other than `/usr/local' using `--prefix',
for instance `--prefix=$HOME'.

For better control, use the options below.

Fine tuning of the installation directories:
  --bindir=DIR           user executables [EPREFIX/bin]
  --sbindir=DIR          system admin executables [EPREFIX/sbin]
  --libexecdir=DIR       program executables [EPREFIX/libexec]
  --sysconfdir=DIR       read-only single-machine data [PREFIX/etc]
  --sharedstatedir=DIR   modifiable architecture-independent data [PREFIX/com]
  --localstatedir=DIR    modifiable single-machine data [PREFIX/var]
  --libdir=DIR           object code libraries [EPREFIX/lib]
  --includedir=DIR       C header files [PREFIX/include]
  --oldincludedir=DIR    C header files for non-gcc [/usr/include]
  --datarootdir=DIR      read-only arch.-independent data root [PREFIX/share]
  --datadir=DIR          read-only architecture-independent data [DATAROOTDIR]
  --infodir=DIR          info documentation [DATAROOTDIR/info]
  --localedir=DIR        locale-dependent data [DATAROOTDIR/locale]
  --mandir=DIR           man documentation [DATAROOTDIR/man]
  --docdir=DIR           documentation root [DATAROOTDIR/doc/transcode]
  --htmldir=DIR          html documentation [DOCDIR]
  --dvidir=DIR           dvi documentation [DOCDIR]
  --pdfdir=DIR           pdf documentation [DOCDIR]
  --psdir=DIR            ps documentation [DOCDIR]

Program names:
  --program-prefix=PREFIX            prepend PREFIX to installed program names
  --program-suffix=SUFFIX            append SUFFIX to installed program names
  --program-transform-name=PROGRAM   run sed PROGRAM on installed program names

X features:
  --x-includes=DIR    X include files are in DIR
  --x-libraries=DIR   X library files are in DIR

System types:
  --build=BUILD     configure for building on BUILD [guessed]
  --host=HOST       cross-compile to build programs to run on HOST [BUILD]
  --target=TARGET   configure for building compilers for TARGET [HOST]

Optional Features:
  --disable-FEATURE       do not include FEATURE (same as --enable-FEATURE=no)
  --enable-FEATURE[=ARG]  include FEATURE [ARG=yes]
  --enable-maintainer-mode  enable make rules and dependencies not useful
              (and sometimes confusing) to the casual installer
  --disable-dependency-tracking  speeds up one-time build
  --enable-dependency-tracking   do not reject slow dependency extractors
  --enable-static[=PKGS]  build static libraries [default=no]
  --enable-shared[=PKGS]  build shared libraries [default=yes]
  --enable-fast-install[=PKGS]
                          optimize for fast installation [default=yes]
  --disable-libtool-lock  avoid locking (might break parallel builds)
  --disable-largefile     omit support for large files
  --enable-mmx            enable MMX code portions (yes)
  --enable-3dnow          enable 3DNow code portions (yes)
  --enable-sse            enable SSE code portions (yes)
  --enable-sse2           enable SSE2 code portions (yes)
  --enable-altivec        enable Altivec code portions (yes)
  --enable-libavcodec     build with libavcodec support (optional)
  --enable-libavformat    build with libavformat support (optional)
  --enable-libavformat    build with libavformat support (required)
  --enable-libmpeg2       build with libmpeg2 support (required)
  --enable-experimental   enable new, experimental or even incomplete
                          transcode components (no)
  --enable-deprecated     enable deprecated or even broken transcode
                          components (no)
  --enable-statbuffer     enable internal static framebuffer support;
                          recommended (yes)
  --enable-v4l            enable v4l/v4l2 support (no)
  --enable-bktr           enable bktr support (no)
  --enable-sunau          enable sunau support (no)
  --enable-oss            enable OSS audio support (no)
  --enable-alsa           enable ALSA audio support (no)
  --enable-libpostproc    build with libpostproc support (no)
  --enable-freetype2      build with freetype2 support (no)
  --enable-lame           build with lame support (yes)
  --enable-xvid           build with xvid support (no)
  --enable-x264           build with x264 support (no)
  --enable-ogg            build with ogg support (no)
  --enable-vorbis         build with vorbis support (no)
  --enable-theora         build with theora support (no)
  --enable-libdvdread     build with libdvdread support (yes)
  --enable-pvm3           build with pvm3 support (no)
  --enable-libdv          build with libdv support (no)
  --enable-libquicktime   build with libquicktime support (no)
  --enable-lzo            build with lzo support (no)
  --enable-a52            build with a52 support (no)
  --enable-faac           build with faac support (no)
  --enable-libxml2        build with libxml2 support (no)
  --enable-ibp            enable ibp support (no)
  --enable-mjpegtools     build with mjpegtools support (no)
  --enable-sdl            build with sdl support (no)
  --enable-imagemagick    build with imagemagick support (no)
  --enable-libjpegmmx     build with libjpegmmx support (no)
  --enable-libjpeg        build with libjpeg support (yes)
  --enable-bsdav          build with bsdav support (no)
  --enable-iconv          build with iconv support (yes)
  --enable-pv3            enable PV3 support (no)
  --enable-nuv            enable NuppelVideo support (no)
  --enable-warnings-as-errors
                          treat warnings as errors

Optional Packages:
  --with-PACKAGE[=ARG]    use PACKAGE [ARG=yes]
  --without-PACKAGE       do not use PACKAGE (same as --with-PACKAGE=no)
  --with-gnu-ld           assume the C compiler uses GNU ld [default=no]
  --with-pic              try to use only PIC/non-PIC objects [default=use
                          both]
  --with-tags[=TAGS]      include additional configurations [automatic]
  --with-x                use the X Window System
  --with-libavcodec-prefix=PFX
                          prefix where libavcodec is installed (/usr)
  --with-libavcodec-includes=DIR
                          directory where libavcodec headers
                          (libavcodec/avcodec.h) are installed (/usr/include)
  --with-libavcodec-libs=DIR
                          directory where libavcodec libraries (libavcodec.so)
                          are installed (/usr/lib)
  --with-libavformat-prefix=PFX
                          prefix where libavformat is installed (/usr)
  --with-libavformat-includes=DIR
                          directory where libavformat headers
                          (libavformat/avformat.h) are installed
                          (/usr/include)
  --with-libavformat-libs=DIR
                          directory where libavformat libraries
                          (libavformat.so) are installed (/usr/lib)
  --with-libavformat-includes=DIR
                          directory where libavformat headers
                          (ffmpeg/avformat.h) are installed (/usr/include)
  --with-libmpeg2-prefix=PFX
                          prefix where libmpeg2 is installed (/usr)
  --with-libmpeg2-includes=DIR
                          directory where libmpeg2 headers (mpeg2dec/mpeg2.h)
                          are installed (/usr/include)
  --with-libmpeg2-libs=DIR
                          directory where libmpeg2 libraries (libmpeg2.so) are
                          installed (/usr/lib)
  --with-libpostproc-prefix=PFX
                          prefix where libpostproc is installed (/usr)
  --with-libpostproc-includes=DIR
                          directory where libpostproc headers
                          (libpostproc/postprocess.h) are installed
                          (/usr/include)
  --with-libpostproc-libs=DIR
                          directory where libpostproc libraries
                          (libpostproc.so) are installed (/usr/lib)
  --with-freetype2-prefix=PFX
                          prefix where freetype2 is installed (/usr)
  --with-freetype2-includes=DIR
                          directory where freetype2 headers (ft2build.h) are
                          installed (/usr/include)
  --with-freetype2-libs=DIR
                          directory where freetype2 libraries (libfreetype.so)
                          are installed (/usr/lib)
  --with-lame-prefix=PFX  prefix where lame is installed (/usr)
  --with-lame-includes=DIR
                          directory where lame headers (none) are installed
                          (/usr/include)
  --with-lame-libs=DIR    directory where lame libraries (libmp3lame.so) are
                          installed (/usr/lib)
  --with-xvid-prefix=PFX  prefix where xvid is installed (/usr)
  --with-xvid-includes=DIR
                          directory where xvid headers (xvid.h) are installed
                          (/usr/include)
  --with-xvid-libs=DIR    directory where xvid libraries (libxvidcore.so) are
                          installed (/usr/lib)
  --with-x264-prefix=PFX  prefix where x264 is installed (/usr)
  --with-x264-includes=DIR
                          directory where x264 headers (x264.h) are installed
                          (/usr/include)
  --with-x264-libs=DIR    directory where x264 libraries (libx264.so) are
                          installed (/usr/lib)
  --with-ogg-prefix=PFX   prefix where ogg is installed (/usr)
  --with-ogg-includes=DIR directory where ogg headers (ogg/ogg.h) are
                          installed (/usr/include)
  --with-ogg-libs=DIR     directory where ogg libraries (libogg.so) are
                          installed (/usr/lib)
  --with-vorbis-prefix=PFX
                          prefix where vorbis is installed (/usr)
  --with-vorbis-includes=DIR
                          directory where vorbis headers (vorbis/codec.h) are
                          installed (/usr/include)
  --with-vorbis-libs=DIR  directory where vorbis libraries (libvorbis.so) are
                          installed (/usr/lib)
  --with-theora-prefix=PFX
                          prefix where theora is installed (/usr)
  --with-theora-includes=DIR
                          directory where theora headers (theora/theora.h) are
                          installed (/usr/include)
  --with-theora-libs=DIR  directory where theora libraries (libtheora.so) are
                          installed (/usr/lib)
  --with-libdvdread-prefix=PFX
                          prefix where libdvdread is installed (/usr)
  --with-libdvdread-includes=DIR
                          directory where libdvdread headers (none) are
                          installed (/usr/include)
  --with-libdvdread-libs=DIR
                          directory where libdvdread libraries (libdvdread.so)
                          are installed (/usr/lib)
  --with-pvm3-prefix=PFX  prefix where pvm3 is installed (/usr)
  --with-pvm3-includes=DIR
                          directory where pvm3 headers (pvm3.h) are installed
                          (/usr/include)
  --with-pvm3-libs=DIR    directory where pvm3 libraries (libpvm3.so) are
                          installed (/usr/lib)
  --with-libdv-prefix=PFX prefix where libdv is installed (/usr)
  --with-libdv-includes=DIR
                          directory where libdv headers (libdv/dv.h) are
                          installed (/usr/include)
  --with-libdv-libs=DIR   directory where libdv libraries (libdv.so) are
                          installed (/usr/lib)
  --with-libquicktime-prefix=PFX
                          prefix where libquicktime is installed (/usr)
  --with-libquicktime-includes=DIR
                          directory where libquicktime headers (quicktime.h)
                          are installed (/usr/include)
  --with-libquicktime-libs=DIR
                          directory where libquicktime libraries
                          (libquicktime.so) are installed (/usr/lib)
  --with-lzo-prefix=PFX   prefix where lzo is installed (/usr)
  --with-lzo-includes=DIR directory where lzo headers (lzo/lzo1x.h) are
                          installed (/usr/include)
  --with-lzo-libs=DIR     directory where lzo libraries (liblzo2.so) are
                          installed (/usr/lib)
  --with-a52-prefix=PFX   prefix where a52 is installed (/usr)
  --with-a52-includes=DIR directory where a52 headers (a52dec/a52.h) are
                          installed (/usr/include)
  --with-a52-libs=DIR     directory where a52 libraries (liba52.so) are
                          installed (/usr/lib)
  --with-faac-prefix=PFX  prefix where faac is installed (/usr)
  --with-faac-includes=DIR
                          directory where faac headers (faac.h) are installed
                          (/usr/include)
  --with-faac-libs=DIR    directory where faac libraries (libfaac.so) are
                          installed (/usr/lib)
  --with-libxml2-prefix=PFX
                          prefix where libxml2 is installed (/usr)
  --with-libxml2-includes=DIR
                          directory where libxml2 headers (libxml/parser.h)
                          are installed (/usr/include)
  --with-libxml2-libs=DIR directory where libxml2 libraries (libxml2.so) are
                          installed (/usr/lib)
  --with-libfdr=DIR       base directory for libfdr
  --with-libibp=DIR       base directory for libibp
  --with-libexnode=DIR    base directory for libexnode
  --with-liblbone=DIR     base directory for liblbone
  --with-libend2end=DIR   base directory for libend2end
  --with-liblors=DIR      base directory for liblors
  --with-mjpegtools-prefix=PFX
                          prefix where mjpegtools is installed (/usr)
  --with-mjpegtools-includes=DIR
                          directory where mjpegtools headers
                          (mjpegtools/yuv4mpeg.h) are installed (/usr/include)
  --with-mjpegtools-libs=DIR
                          directory where mjpegtools libraries
                          (libmjpegutils.so) are installed (/usr/lib)
  --with-sdl-prefix=PFX   prefix where sdl is installed (/usr)
  --with-sdl-includes=DIR directory where sdl headers (SDL.h) are installed
                          (/usr/include)
  --with-sdl-libs=DIR     directory where sdl libraries (libSDL.so) are
                          installed (/usr/lib)
  --with-imagemagick-prefix=PFX
                          prefix where imagemagick is installed (/usr)
  --with-imagemagick-includes=DIR
                          directory where imagemagick headers (magick/api.h)
                          are installed (/usr/include)
  --with-imagemagick-libs=DIR
                          directory where imagemagick libraries (libnone.so)
                          are installed (/usr/lib)
  --with-libjpegmmx-prefix=PFX
                          prefix where libjpegmmx is installed (/usr)
  --with-libjpegmmx-includes=DIR
                          directory where libjpegmmx headers (jpeglib.h) are
                          installed (/usr/include)
  --with-libjpegmmx-libs=DIR
                          directory where libjpegmmx libraries
                          (libjpeg-mmx.so) are installed (/usr/lib)
  --with-libjpeg-prefix=PFX
                          prefix where libjpeg is installed (/usr)
  --with-libjpeg-includes=DIR
                          directory where libjpeg headers (jpeglib.h) are
                          installed (/usr/include)
  --with-libjpeg-libs=DIR directory where libjpeg libraries (libjpeg.so) are
                          installed (/usr/lib)
  --with-bsdav-prefix=PFX prefix where bsdav is installed (/usr)
  --with-bsdav-includes=DIR
                          directory where bsdav headers (bsdav.h) are
                          installed (/usr/include)
  --with-bsdav-libs=DIR   directory where bsdav libraries (libbsdav.so) are
                          installed (/usr/lib)
  --with-iconv-prefix=PFX prefix where iconv is installed (/usr)
  --with-iconv-includes=DIR
                          directory where iconv headers (iconv.h) are
                          installed (/usr/include)
  --with-iconv-libs=DIR   directory where iconv libraries (libnone.so) are
                          installed (/usr/lib)
  --with-mod-path         where export/import modules are installed
                          (${libdir}/transcode)
  --with-prof-path        where export profiles data are installed
                          (${datadir}/transcode/profiles)

Some influential environment variables:
  CC          C compiler command
  CFLAGS      C compiler flags
  LDFLAGS     linker flags, e.g. -L<lib dir> if you have libraries in a
              nonstandard directory <lib dir>
  LIBS        libraries to pass to the linker, e.g. -l<library>
  CPPFLAGS    C/C++/Objective C preprocessor flags, e.g. -I<include dir> if
              you have headers in a nonstandard directory <include dir>
  CPP         C preprocessor
  CCAS        assembler compiler command (defaults to CC)
  CCASFLAGS   assembler compiler flags (defaults to CFLAGS)
  CXXCPP      C++ preprocessor
  XMKMF       Path to xmkmf, Makefile generator for X Window System

Use these variables to override the choices made by `configure' or to help
it to find libraries and programs with nonstandard names/locations.
```There you go.

---

### Post by Bachstelze on 2009-09-02
Actually, I've just tried it and it worked for me. Which Ubuntu version are you using?

---

### Post by jhcheslik21 on 2009-09-02
I'm using 9.04.

Its probably that I didn't compile ffmpeg right in first place then?

---

### Post by Bachstelze on 2009-09-02
> **jhcheslik21 said:**
> I'm using 9.04.

Its probably that I didn't compile ffmpeg right in first place then?

So you did compile ffmpeg? It works without compiling it here, 9.04 too.

---

### Post by jhcheslik21 on 2009-09-02
Yeah, I followed this thread.. 

[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

---

### Post by Bachstelze on 2009-09-02
> **jhcheslik21 said:**
> Yeah, I followed this thread.. 

[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

Then uninstall ffmpeg and try again with the packages from the repos. It definitely works here.

---

### Post by jhcheslik21 on 2009-09-02
Wow.

That worked. I installed the proper ffmpeg from the package manager and it worked.

I noticed that there is a transcode package in there as well. Only that it's 1.0.7 version.

Anyway, thank you very much for your help! :)

---

### Post by jhcheslik21 on 2009-09-02
Oh, I would like to add, Ubuntu is awesome! :D

---

### Post by FakeOutdoorsman on 2009-09-02
> **jhcheslik21 said:**
> Yeah, I followed this thread.. 

[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

Compiled FFmpeg may work if you add "--enable-shared" to the FFmpeg configuration line, and then running "sudo ldconfig" after FFmpeg installation, but this is just a guess and I didn't get to test this.

---

### Post by andrew.46 on 2009-09-02
Hi jhcheslik21,

> **jhcheslik21 said:**
> I noticed that there is a transcode package in there as well. Only that it's 1.0.7 version.

Just to add to the confusion I believe you are compiling a slightly older version of Transcode, although we are talking point upgrades here:

```
wget http://download.berlios.de/tcforge/transcode-1.1.4.tar.bz2
```

I am a little curious as to why you are compiling Transcode, are there some extra options that you are after? Don't get me wrong I compile Transcode myself on another distro, but I am more than aware that it is a slightly difficult one to get set correctly...

**Edit:** I have been discreetly corrected here as it looks like 1.1.4 came out on August 23rd :-). 

Andrew

---

### Post by jhcheslik21 on 2009-09-02
Yeah,

I never looked in the Package Manager until now. I didn't think that transcode package would exist. So, that doesn't matter, I went on and compiled it. I just wanted to learn something about how to use linux for first time. (Been using it in last 5 days.)

So yeah, I was not really after some extra options over the older version. :P

Joe

---

### Post by andrew.46 on 2009-09-02
Hi Joe,

> **jhcheslik21 said:**
> I never looked in the Package Manager until now. I didn't think that transcode package would exist. So, that doesn't matter, I went on and compiled it. I just wanted to learn something about how to use linux for first time. (Been using it in last 5 days.)

You have jumped into the deep end well and truly :-). You may already know that you can assess your efforts by looking at the import and export modules available to you:

**Import:**

```

andrew@skamandros~$ **[COLOR="Red"]ls -1 $( tcmodinfo -p )/import*.so[/COLOR]**
/usr/lib/transcode/import_ac3.so
/usr/lib/transcode/import_alsa.so
/usr/lib/transcode/import_avi.so
/usr/lib/transcode/import_bsdav.so
/usr/lib/transcode/import_dv.so
/usr/lib/transcode/import_dvd.so
/usr/lib/transcode/import_ffmpeg.so
/usr/lib/transcode/import_framegen.so
/usr/lib/transcode/import_im.so
/usr/lib/transcode/import_imlist.so
/usr/lib/transcode/import_lzo.so
/usr/lib/transcode/import_mov.so
/usr/lib/transcode/import_mp3.so
/usr/lib/transcode/import_mpeg2.so
/usr/lib/transcode/import_mplayer.so
/usr/lib/transcode/import_null.so
/usr/lib/transcode/import_nuv.so
/usr/lib/transcode/import_ogg.so
/usr/lib/transcode/import_pvn.so
/usr/lib/transcode/import_raw.so
/usr/lib/transcode/import_v4l.so
/usr/lib/transcode/import_v4l2.so
/usr/lib/transcode/import_vag.so
/usr/lib/transcode/import_vnc.so
/usr/lib/transcode/import_vob.so
/usr/lib/transcode/import_x11.so
/usr/lib/transcode/import_xml.so
/usr/lib/transcode/import_xvid.so
/usr/lib/transcode/import_yuv4mpeg.so

```

**Export:**

```

andrew@skamandros~$ **[COLOR="Red"]ls -1 $( tcmodinfo -p )/export*.so[/COLOR]**
/usr/lib/transcode/export_ac3.so
/usr/lib/transcode/export_divx5.so
/usr/lib/transcode/export_dv.so
/usr/lib/transcode/export_dvraw.so
/usr/lib/transcode/export_ffmpeg.so
/usr/lib/transcode/export_im.so
/usr/lib/transcode/export_jpg.so
/usr/lib/transcode/export_lame.so
/usr/lib/transcode/export_lzo.so
/usr/lib/transcode/export_mov.so
/usr/lib/transcode/export_mp2.so
/usr/lib/transcode/export_mp2enc.so
/usr/lib/transcode/export_mpeg2enc.so
/usr/lib/transcode/export_null.so
/usr/lib/transcode/export_ogg.so
/usr/lib/transcode/export_pcm.so
/usr/lib/transcode/export_ppm.so
/usr/lib/transcode/export_pvn.so
/usr/lib/transcode/export_raw.so
/usr/lib/transcode/export_tcaud.so
/usr/lib/transcode/export_toolame.so
/usr/lib/transcode/export_wav.so
/usr/lib/transcode/export_xvid.so
/usr/lib/transcode/export_xvid4.so
/usr/lib/transcode/export_yuv4mpeg.so

```

This is about as complete an installation as I could manage myself although I suspect I will not even use many of these modules :-).

Andrew

---

