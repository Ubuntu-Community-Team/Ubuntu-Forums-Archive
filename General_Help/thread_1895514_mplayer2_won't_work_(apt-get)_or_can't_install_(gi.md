---
title: "mplayer2 won't work (apt-get) or can't install (git)"
date: 2011-12-14
forum: General Help
---

### Post by nstgc379 on 2011-12-14
I want to use mplayer2 since it seems to be better, but its nothing but hate. I first tried to install from source, as I typically do for anything that is performance sensative (games, players, and SciLab) however, this has been a very unpleasant experiance. After that I tried installing with sudo apt-get install mplayer2, ad while it did install, it also won't play any video files (which play just fine with mplayer). Here is some output.

```
$ ./configure
Checking for cc version ... 4.6.1 
Detected operating system: Linux
Detected host architecture: x86_64
Checking for host cc ... cc 
Checking for cross compilation ... no 
Checking for CPU vendor ... GenuineIntel (6:42:7) 
Checking for CPU type ...  Intel(R) Core(TM) i5-2500K CPU @ 3.30GHz 
Checking for kernel support of mmx ... yes 
Checking for kernel support of mmxext ... yes 
Checking for kernel support of sse ... yes 
Checking for kernel support of sse2 ... yes 
Checking for kernel support of ssse3 ... yes 
Checking for kernel support of cmov ... yes 
Checking for mtrr support ... yes 
Checking for GCC & CPU optimization abilities ... native 
Checking for byte order ... little-endian 
Checking for extern symbol prefix ...  
Checking for assembler support of -pipe option ... yes 
Checking for compiler support of named assembler arguments ... yes 
Checking for PIC ... no 
Checking for .align is a power of two ... no 
Checking for 10 assembler operands ... yes 
Checking for ebx availability ... yes 
Checking for yasm ... yasm 
Checking for bswap ... yes 
Checking for -lposix ... no 
Checking for -lm ... yes 
Checking for langinfo ... yes 
Checking for translation support ... no 
Checking for language ... messages (en+):  - man pages: en - documentation: en 
Checking for enable sighandler ... yes 
Checking for runtime cpudetection ... no 
Checking for restrict keyword ... restrict 
Checking for __builtin_expect ... yes 
Checking for kstat ... no 
Checking for posix4 ... no 
Checking for exp2 ... yes 
Checking for exp2f ... yes 
Checking for llrint ... yes 
Checking for log2 ... yes 
Checking for log2f ... yes 
Checking for lrint ... yes 
Checking for lrintf ... yes 
Checking for round ... yes 
Checking for roundf ... yes 
Checking for truncf ... yes 
Checking for mkstemp ... yes 
Checking for nanosleep ... yes 
Checking for socklib ... yes 
Checking for arpa/inet.h ... yes 
Checking for inet_pton() ... yes 
Checking for inet_aton() ... yes 
Checking for socklen_t ... yes 
Checking for closesocket() ... no 
Checking for networking ... yes 
Checking for inet6 ... yes 
Checking for gethostbyname2 ... yes 
Checking for inttypes.h (required) ... yes 
Checking for malloc.h ... yes 
Checking for memalign() ... yes 
Checking for posix_memalign() ... yes 
Checking for alloca.h ... yes 
Checking for fastmemcpy ... yes 
Checking for mman.h ... yes 
Checking for dynamic loader ... yes 
Checking for dynamic a/v plugins support ... no 
Checking for pthread ... yes (using -lpthread)
Checking for w32threads ... no (using pthread instead)
Checking for rpath ... no 
Checking for iconv ... yes 
Checking for soundcard.h ... yes (sys/soundcard.h)
Checking for sys/dvdio.h ... no 
Checking for sys/cdio.h ... no 
Checking for linux/cdrom.h ... yes 
Checking for dvd.h ... no 
Checking for termcap ... yes (using -lncurses)
Checking for termios ... yes (using termios.h)
Checking for shm ... yes 
Checking for strsep() ... yes 
Checking for vsscanf() ... yes 
Checking for swab() ... yes 
Checking for POSIX select() ... yes 
Checking for audio select() ... yes 
Checking for gettimeofday() ... yes 
Checking for glob() ... yes 
Checking for setenv() ... yes 
Checking for setmode() ... no 
Checking for sys/sysinfo.h ... yes 
Checking for Apple IR ... yes 
Checking for pkg-config ... yes 
Checking for Samba support (libsmbclient) ... no 
Checking for tdfxfb ... no 
Checking for s3fb ... no 
Checking for wii ... no 
Checking for tdfxvid ... no 
Checking for xvr100 ... no 
Checking for tga ... yes 
Checking for md5sum support ... yes 
Checking for yuv4mpeg support ... yes 
Checking for bl ... no 
Checking for DirectFB ... no 
Checking for X11 headers presence ... yes 
Checking for X11 ... yes 
Checking for Xss screensaver extensions ... no 
Checking for DPMS ... yes (using Xdpms 4)
Checking for Xv ... yes 
Checking for XvMC ... no 
Checking for VDPAU ... yes 
Checking for Xinerama ... yes 
Checking for Xxf86vm ... no 
Checking for XF86keysym ... yes 
Checking for DGA ... no 
Checking for 3dfx ... no 
Checking for GGI ... no 
Checking for GGI extension: libggiwmh ... no 
Checking for AA ... yes 
Checking for CACA ... yes 
Checking for SVGAlib ... no 
Checking for FBDev ... yes 
Checking for DVB ... yes 
Checking for PNG support ... yes 
Checking for MNG support ... no 
Checking for JPEG support ... no 
Checking for PNM support ... yes 
Checking for GIF support ... no 
Checking for VESA support ... no 
Checking for SDL ... yes 
Checking for OpenGL ... yes (backends: x11 sdl)
Checking for MatrixView ... yes 
Checking for DXR3/H+ ... no 
Checking for IVTV TV-Out (pre linux-2.6.24) ... no 
Checking for V4L2 MPEG Decoder ... yes 
Checking for OSS Audio ... yes 
Checking for aRts ... no 
Checking for EsounD ... yes 
Checking for esd_get_latency() ... yes 
Checking for NAS ... yes 
Checking for pulse ... yes 
Checking for JACK ... yes 
Checking for OpenAL ... no 
Checking for ALSA audio ... yes (using alsa 1.0.x and alsa/asoundlib.h)
Checking for Sun audio ... no 
Checking for VCD support ... yes 
Checking for Blu-ray support ... no 
Checking for dvdread ... no 
Checking for internal libdvdcss ... no 
Checking for cdparanoia ... no 
Checking for libcdio ... no 
Checking for bitmap font support ... yes 
Checking for freetype >= 2.0.9 ... yes 
Checking for fontconfig ... yes 
Checking for SSA/*** support ... yes 
Checking for fribidi with charsets ... no 
Checking for ENCA ... yes 
Checking for zlib ... yes 
Checking for RTC ... yes 
Checking for mad support ... no 
Checking for OggVorbis support ... yes (libvorbis)
Checking for libspeex (version >= 1.1 required) ... no 
Checking for OggTheora support ... yes 
Checking for mp3lib support ... yes 
Checking for mpg123 support ... no 
Checking for liba52 support ... no 
Checking for libdca support ... no 
Checking for libmpcdec (musepack, version >= 1.2.1 required) ... no 
Checking for FAAD2 support ... no 
Checking for LADSPA plugin support ... no 
Checking for libbs2b audio filter support ... no 
Checking for Win32 codecs ... no 
Checking for XAnim codecs ... yes (dynamic loader support needed)
Checking for RealPlayer codecs ... yes (dynamic loader support needed)
Checking for QuickTime codecs ... auto 
Checking for Nemesi Streaming Media libraries ... no 
Checking for LIVE555 Streaming Media libraries ... no 
Checking for FFmpeg (libavutil libavcodec libavformat libswscale libpostproc) ... yes 
Checking for libdv-0.9.5+ ... no 
Checking for Xvid ... no 
Checking for libnut ... no 
Checking for /dev/mga_vid ... no 
Checking for xmga ... no 
Checking for UnRAR executable ... yes 
Checking for TV interface ... yes 
Checking for DirectShow TV interface ... no 
Checking for Video 4 Linux TV interface ... no 
Checking for Video 4 Linux 2 TV interface ... yes 
Checking for Radio interface ... no 
Checking for Capture for Radio interface ... no 
Checking for Video 4 Linux 2 Radio interface ... no 
Checking for Video 4 Linux Radio interface ... no 
Checking for Video 4 Linux 2 MPEG PVR interface ... yes 
Checking for ftp ... yes 
Checking for vstream client ... no 
Checking for OSD menu ... no 
Checking for Subtitles sorting ... yes 
Checking for XMMS inputplugin support ... no 
Checking for automatic gdb attach ... no 
Checking for compiler support for noexecstack ... yes 
Checking for linker support for --nxcompat --no-seh --dynamicbase ... no 
Checking for joystick ... no 
Checking for lirc ... no 
Checking for lircc ... no 
Checking for DVD support (libdvdnav) ... no 
Creating config.mak
Creating config.h

Config files successfully generated by ./configure  !

  Install prefix: /usr/local
  Data directory: /usr/local/share/mplayer
  Config direct.: /usr/local/etc/mplayer

  Byte order: little-endian
  Optimizing for: native

  Languages:
    Messages (in addition to English): 
    Manual pages: en
    Documentation: en

  Enabled optional drivers:
    Input: ftp pvr tv-v4l2 tv vcd dvb networking 
    Codecs: ffmpeg real xanim mp3lib(internal) libtheora libvorbis 
    Audio output: alsa jack pulse nas esd oss v4l2 sdl mpegpes(dvb) 
    Video output: v4l2 matrixview opengl sdl pnm mpegpes(dvb) fbdev caca aa vdpau xv x11 xover yuv4mpeg md5sum tga 

  Disabled optional drivers:
    Input: dvdnav vstream radio tv-v4l1 tv-dshow live555 nemesi cddb cdda libdvdcss(internal) dvdread bluray smb 
    Codecs: xvid libdv qtx win32 faad2 musepack libdca liba52 mpg123 speex libmad gif 
    Audio output: sun openal arts ivtv 
    Video output: xmga mga ivtv dxr3 vesa gif89a jpeg svga ggi 3dfx dga xvmc directfb dfbmga bl xvr100 tdfx_vid wii s3fb tdfxfb 

'config.h' and 'config.mak' contain your configuration options.
Note: If you alter theses files (for instance CFLAGS) MPlayer may no longer
      compile *** DO NOT REPORT BUGS if you tweak these files ***

'make' will now compile MPlayer and 'make install' will install it.
Note: On non-Linux systems you might need to use 'gmake' instead of 'make'.

Please check mtrr settings at /proc/mtrr (see DOCS/HTML/en/video.html#mtrr)

NOTE: Win32 codec DLLs are not supported on your CPU (x86_64) or your
operating system (Linux). You may encounter a few files that cannot
be played due to missing open source video/audio codec support.

Check config.log if you wonder why an autodetection failed (make sure
development headers/packages are installed).

NOTE: The --enable-* parameters unconditionally force options on, completely
skipping autodetection. This behavior is unlike what you may be used to from
autoconf-based configure scripts that can decide to override you. This greater
level of control comes at a price. You may have to provide the correct compiler
and linker flags yourself.
If you used one of these options (except --enable-menu and similar ones that
turn on internal features) and experience a compilation or linking failure,
make sure you have passed the necessary compiler/linker flags to configure.

If you suspect a bug, please read DOCS/HTML/en/bugreports.html.

```

Everything looks fine to be there, but then I make.

```
$ make -j 4
./version.sh
cc -MD -MP -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I.  -D_REENTRANT -I/usr/include/     -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include/freetype2     -I/usr/local/include   -c -o command.o command.c
cc -MD -MP -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I.  -D_REENTRANT -I/usr/include/     -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include/freetype2     -I/usr/local/include   -c -o m_property.o m_property.c
cc -MD -MP -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I.  -D_REENTRANT -I/usr/include/     -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include/freetype2     -I/usr/local/include   -c -o mixer.o mixer.c
cc -MD -MP -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I.  -D_REENTRANT -I/usr/include/     -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include/freetype2     -I/usr/local/include   -c -o mplayer.o mplayer.c
command.c: In function 'mp_property_sub':
command.c:1608:9: warning: format not a string literal and no format arguments [-Wformat-security]
command.c:1608:9: warning: format not a string literal and no format arguments [-Wformat-security]
cc -MD -MP -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I.  -D_REENTRANT -I/usr/include/     -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include/freetype2     -I/usr/local/include   -c -o parser-mpcmd.o parser-mpcmd.c
command.c:1523:22: warning: variable 'reset_spu' set but not used [-Wunused-but-set-variable]
command.c: In function 'mp_property_sub_source':
command.c:1746:13: warning: format not a string literal and no format arguments [-Wformat-security]
command.c:1746:13: warning: format not a string literal and no format arguments [-Wformat-security]
command.c:1749:13: warning: format not a string literal and no format arguments [-Wformat-security]
command.c:1749:13: warning: format not a string literal and no format arguments [-Wformat-security]
command.c:1752:13: warning: format not a string literal and no format arguments [-Wformat-security]
command.c:1752:13: warning: format not a string literal and no format arguments [-Wformat-security]
command.c:1755:13: warning: format not a string literal and no format arguments [-Wformat-security]
command.c:1755:13: warning: format not a string literal and no format arguments [-Wformat-security]
command.c: In function 'mp_property_sub_by_type':
command.c:1846:9: warning: format not a string literal and no format arguments [-Wformat-security]
command.c:1846:9: warning: format not a string literal and no format arguments [-Wformat-security]
mplayer.c: In function 'parse_cfgfiles':
mplayer.c:912:12: warning: ignoring return value of 'write', declared with attribute warn_unused_result [-Wunused-result]
cc -MD -MP -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I.  -D_REENTRANT -I/usr/include/     -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include/freetype2     -I/usr/local/include   -c -o input/input.o input/input.c
mplayer.c: In function 'run_playloop':
mplayer.c:3412:23: warning: ignoring return value of 'system', declared with attribute warn_unused_result [-Wunused-result]
cc -MD -MP -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I.  -D_REENTRANT -I/usr/include/     -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include/freetype2     -I/usr/local/include   -c -o libao2/ao_mpegpes.o libao2/ao_mpegpes.c
cc -MD -MP -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I.  -D_REENTRANT -I/usr/include/     -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include/freetype2     -I/usr/local/include   -c -o libao2/ao_null.o libao2/ao_null.c
cc -MD -MP -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I.  -D_REENTRANT -I/usr/include/     -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include/freetype2     -I/usr/local/include   -c -o libao2/ao_pcm.o libao2/ao_pcm.c
cc -MD -MP -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I.  -D_REENTRANT -I/usr/include/     -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include/freetype2     -I/usr/local/include   -c -o libao2/audio_out.o libao2/audio_out.c
cc -MD -MP -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I.  -D_REENTRANT -I/usr/include/     -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include/freetype2     -I/usr/local/include   -c -o libvo/aspect.o libvo/aspect.c
cc -MD -MP -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I.  -D_REENTRANT -I/usr/include/     -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include/freetype2     -I/usr/local/include   -c -o libvo/geometry.o libvo/geometry.c
cc -MD -MP -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I.  -D_REENTRANT -I/usr/include/     -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include/freetype2     -I/usr/local/include   -c -o libvo/old_vo_wrapper.o libvo/old_vo_wrapper.c
cc -MD -MP -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I.  -D_REENTRANT -I/usr/include/     -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include/freetype2     -I/usr/local/include   -c -o libvo/video_out.o libvo/video_out.c
cc -MD -MP -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I.  -D_REENTRANT -I/usr/include/     -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include/freetype2     -I/usr/local/include   -c -o libvo/vo_mpegpes.o libvo/vo_mpegpes.c
cc -MD -MP -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I.  -D_REENTRANT -I/usr/include/     -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include/freetype2     -I/usr/local/include   -c -o libvo/vo_null.o libvo/vo_null.c
cc -MD -MP -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I.  -D_REENTRANT -I/usr/include/     -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include/freetype2     -I/usr/local/include   -c -o libvo/vo_aa.o libvo/vo_aa.c
cc -MD -MP -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I.  -D_REENTRANT -I/usr/include/     -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include/freetype2     -I/usr/local/include   -c -o libao2/ao_alsa.o libao2/ao_alsa.c
libvo/vo_aa.c: In function 'draw_frame':
libvo/vo_aa.c:352:3: warning: passing argument 2 of 'sws_scale' from incompatible pointer type [enabled by default]
/usr/local/include/libswscale/swscale.h:238:5: note: expected 'const uint8_t * const*' but argument is of type 'uint8_t **'
libvo/vo_aa.c: In function 'draw_slice':
libvo/vo_aa.c:372:3: warning: passing argument 2 of 'sws_scale' from incompatible pointer type [enabled by default]
/usr/local/include/libswscale/swscale.h:238:5: note: expected 'const uint8_t * const*' but argument is of type 'uint8_t **'
libvo/vo_aa.c: In function 'preinit':
libvo/vo_aa.c:671:17: warning: variable 'major' set but not used [-Wunused-but-set-variable]
libvo/vo_aa.c: In function 'uninit':
libvo/vo_aa.c:503:9: warning: ignoring return value of 'freopen', declared with attribute warn_unused_result [-Wunused-result]
libvo/vo_aa.c: In function 'preinit':
libvo/vo_aa.c:719:9: warning: ignoring return value of 'freopen', declared with attribute warn_unused_result [-Wunused-result]
cc -MD -MP -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I.  -D_REENTRANT -I/usr/include/     -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include/freetype2     -I/usr/local/include   -c -o input/appleir.o input/appleir.c
cc -MD -MP -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I.  -D_REENTRANT -I/usr/include/     -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include/freetype2     -I/usr/local/include   -c -o libvo/vo_caca.o libvo/vo_caca.c
libao2/ao_alsa.c: In function 'try_open_device':
libao2/ao_alsa.c:314:23: warning: 'err' may be used uninitialized in this function [-Wuninitialized]
cc -MD -MP -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I.  -D_REENTRANT -I/usr/include/     -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include/freetype2     -I/usr/local/include   -c -o libao2/ao_esd.o libao2/ao_esd.c
cc -MD -MP -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I.  -D_REENTRANT -I/usr/include/     -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include/freetype2     -I/usr/local/include   -c -o libvo/vo_fbdev.o libvo/vo_fbdev.c
cc -MD -MP -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I.  -D_REENTRANT -I/usr/include/     -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include/freetype2     -I/usr/local/include   -c -o libvo/vo_fbdev2.o libvo/vo_fbdev2.c
libao2/ao_esd.c: In function 'init':
libao2/ao_esd.c:245:14: warning: 'lag_net' may be used uninitialized in this function [-Wuninitialized]
cc -MD -MP -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I.  -D_REENTRANT -I/usr/include/     -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include/freetype2     -I/usr/local/include   -c -o libvo/vo_png.o libvo/vo_png.c
libvo/vo_fbdev.c: In function 'config':
libvo/vo_fbdev.c:749:9: warning: unused variable 'zoom' [-Wunused-variable]
libvo/vo_fbdev.c: In function 'vt_set_textarea':
libvo/vo_fbdev.c:738:14: warning: ignoring return value of 'write', declared with attribute warn_unused_result [-Wunused-result]
libvo/vo_png.c: In function 'preinit':
libvo/vo_png.c:169:5: warning: 'avcodec_alloc_context' is deprecated (declared at /usr/local/include/libavcodec/avcodec.h:3945) [-Wdeprecated-declarations]
libvo/vo_png.c:170:5: warning: 'avcodec_open' is deprecated (declared at /usr/local/include/libavcodec/avcodec.h:4074) [-Wdeprecated-declarations]
cc -MD -MP -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I.  -D_REENTRANT -I/usr/include/     -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include/freetype2     -I/usr/local/include   -c -o libvo/gl_common.o libvo/gl_common.c
cc -MD -MP -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I.  -D_REENTRANT -I/usr/include/     -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include/freetype2     -I/usr/local/include   -c -o libvo/vo_gl.o libvo/vo_gl.c
libvo/vo_gl.c: In function 'update_yuvconv':
libvo/vo_gl.c:272:12: warning: ignoring return value of 'fread', declared with attribute warn_unused_result [-Wunused-result]
cc -MD -MP -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I.  -D_REENTRANT -I/usr/include/     -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include/freetype2     -I/usr/local/include   -c -o libvo/vo_gl2.o libvo/vo_gl2.c
cc -MD -MP -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I.  -D_REENTRANT -I/usr/include/     -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include/freetype2     -I/usr/local/include   -c -o libvo/sdl_common.o libvo/sdl_common.c
libvo/vo_gl2.c: In function 'control':
libvo/vo_gl2.c:915:7: warning: passing argument 2 of 'vo_x11_set_equalizer' discards 'const' qualifier from pointer target type [enabled by default]
libvo/x11_common.h:133:10: note: expected 'char *' but argument is of type 'const char *'
libvo/vo_gl2.c:920:7: warning: passing argument 1 of 'vo_x11_get_equalizer' discards 'const' qualifier from pointer target type [enabled by default]
libvo/x11_common.h:134:10: note: expected 'char *' but argument is of type 'const char *'
cc -MD -MP -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I.  -D_REENTRANT -I/usr/include/     -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include/freetype2     -I/usr/local/include   -c -o libvo/x11_common.o libvo/x11_common.c
libvo/x11_common.c: In function 'vo_x11_classhint':
libvo/x11_common.c:714:22: warning: assignment discards 'const' qualifier from pointer target type [enabled by default]
cc -MD -MP -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I.  -D_REENTRANT -I/usr/include/     -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include/freetype2     -I/usr/local/include   -c -o libvo/vo_matrixview.o libvo/vo_matrixview.c
cc -MD -MP -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I.  -D_REENTRANT -I/usr/include/     -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include/freetype2     -I/usr/local/include   -c -o libvo/matrixview.o libvo/matrixview.c
cc -MD -MP -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I.  -D_REENTRANT -I/usr/include/     -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include/freetype2     -I/usr/local/include   -c -o libao2/ao_jack.o libao2/ao_jack.c
libvo/vo_matrixview.c: In function 'draw_slice':
libvo/vo_matrixview.c:191:5: warning: passing argument 2 of 'sws_scale' from incompatible pointer type [enabled by default]
/usr/local/include/libswscale/swscale.h:238:5: note: expected 'const uint8_t * const*' but argument is of type 'uint8_t **'
cc -MD -MP -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I.  -D_REENTRANT -I/usr/include/     -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include/freetype2     -I/usr/local/include   -c -o libvo/vo_md5sum.o libvo/vo_md5sum.c
libao2/ao_jack.c: In function 'init':
libao2/ao_jack.c:277:3: warning: 'jack_port_get_total_latency' is deprecated (declared at /usr/include/jack/jack.h:1179) [-Wdeprecated-declarations]
cc -MD -MP -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I.  -D_REENTRANT -I/usr/include/     -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include/freetype2     -I/usr/local/include   -c -o libao2/ao_nas.o libao2/ao_nas.c
cc -MD -MP -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I.  -D_REENTRANT -I/usr/include/     -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include/freetype2     -I/usr/local/include   -c -o libao2/ao_oss.o libao2/ao_oss.c
cc -MD -MP -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I.  -D_REENTRANT -I/usr/include/     -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include/freetype2     -I/usr/local/include   -c -o libvo/vo_pnm.o libvo/vo_pnm.c
libao2/ao_oss.c: In function 'init':
libao2/ao_oss.c:417:12: warning: ignoring return value of 'write', declared with attribute warn_unused_result [-Wunused-result]
cc -MD -MP -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I.  -D_REENTRANT -I/usr/include/     -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include/freetype2     -I/usr/local/include   -c -o libao2/ao_pulse.o libao2/ao_pulse.c
cc -MD -MP -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I.  -D_REENTRANT -I/usr/include/     -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include/freetype2     -I/usr/local/include   -c -o libao2/ao_sdl.o libao2/ao_sdl.c
cc -MD -MP -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I.  -D_REENTRANT -I/usr/include/     -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include/freetype2     -I/usr/local/include   -c -o libvo/vo_sdl.o libvo/vo_sdl.c
cc -MD -MP -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I.  -D_REENTRANT -I/usr/include/     -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include/freetype2     -I/usr/local/include   -c -o libvo/vo_tga.o libvo/vo_tga.c
libvo/vo_sdl.c: In function 'erase_rectangle':
libvo/vo_sdl.c:1194:30: warning: dereferencing type-punned pointer will break strict-aliasing rules [-Wstrict-aliasing]
libvo/vo_sdl.c:1208:30: warning: dereferencing type-punned pointer will break strict-aliasing rules [-Wstrict-aliasing]
cc -MD -MP -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I.  -D_REENTRANT -I/usr/include/     -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include/freetype2     -I/usr/local/include   -c -o libvo/vo_v4l2.o libvo/vo_v4l2.c
cc -MD -MP -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I.  -D_REENTRANT -I/usr/include/     -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include/freetype2     -I/usr/local/include   -c -o libao2/ao_v4l2.o libao2/ao_v4l2.c
cc -MD -MP -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I.  -D_REENTRANT -I/usr/include/     -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include/freetype2     -I/usr/local/include   -c -o libvo/vo_vdpau.o libvo/vo_vdpau.c
cc -MD -MP -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I.  -D_REENTRANT -I/usr/include/     -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include/freetype2     -I/usr/local/include   -c -o libvo/vo_x11.o libvo/vo_x11.c
cc -MD -MP -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I.  -D_REENTRANT -I/usr/include/     -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include/freetype2     -I/usr/local/include   -c -o libvo/vo_xover.o libvo/vo_xover.c
libvo/vo_x11.c: In function 'config':
libvo/vo_x11.c:315:19: warning: variable 'xswamask' set but not used [-Wunused-but-set-variable]
libvo/vo_x11.c:314:26: warning: variable 'xswa' set but not used [-Wunused-but-set-variable]
libvo/vo_x11.c:312:22: warning: variable 'bg' set but not used [-Wunused-but-set-variable]
libvo/vo_x11.c:312:18: warning: variable 'fg' set but not used [-Wunused-but-set-variable]
libvo/vo_x11.c: In function 'draw_slice':
libvo/vo_x11.c:556:5: warning: passing argument 2 of 'sws_scale' from incompatible pointer type [enabled by default]
/usr/local/include/libswscale/swscale.h:238:5: note: expected 'const uint8_t * const*' but argument is of type 'uint8_t **'
libvo/vo_x11.c: In function 'control':
libvo/vo_x11.c:675:17: warning: passing argument 2 of 'vo_x11_set_equalizer' discards 'const' qualifier from pointer target type [enabled by default]
libvo/x11_common.h:133:10: note: expected 'char *' but argument is of type 'const char *'
libvo/vo_x11.c:680:17: warning: passing argument 1 of 'vo_x11_get_equalizer' discards 'const' qualifier from pointer target type [enabled by default]
libvo/x11_common.h:134:10: note: expected 'char *' but argument is of type 'const char *'
libvo/video_out_internal.h:43:12: warning: 'query_format' declared 'static' but never defined [-Wunused-function]
cc -MD -MP -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I.  -D_REENTRANT -I/usr/include/     -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include/freetype2     -I/usr/local/include   -c -o libvo/vo_xv.o libvo/vo_xv.c
cc -MD -MP -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I.  -D_REENTRANT -I/usr/include/     -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include/freetype2     -I/usr/local/include   -c -o libvo/vo_yuv4mpeg.o libvo/vo_yuv4mpeg.c
cc -MD -MP -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I.  -D_REENTRANT -I/usr/include/     -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include/freetype2     -I/usr/local/include   -c -o asxparser.o asxparser.c
libvo/vo_xv.c: In function 'draw_image':
libvo/vo_xv.c:530:28: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
libvo/vo_xv.c: In function 'get_image':
libvo/vo_xv.c:606:21: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
libvo/vo_xv.c: In function 'control':
libvo/vo_xv.c:803:13: warning: passing argument 3 of 'vo_xv_set_eq' discards 'const' qualifier from pointer target type [enabled by default]
libvo/x11_common.h:148:5: note: expected 'char *' but argument is of type 'const char *'
libvo/vo_xv.c:808:13: warning: passing argument 3 of 'vo_xv_get_eq' discards 'const' qualifier from pointer target type [enabled by default]
libvo/x11_common.h:149:5: note: expected 'char *' but argument is of type 'const char *'
cc -MD -MP -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I.  -D_REENTRANT -I/usr/include/     -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include/freetype2     -I/usr/local/include   -c -o av_log.o av_log.c
av_log.c: In function 'extract_msg_type_from_ctx':
av_log.c:59:35: error: 'CODEC_TYPE_AUDIO' undeclared (first use in this function)
av_log.c:59:35: note: each undeclared identifier is reported only once for each function it appears in
av_log.c:62:42: error: 'CODEC_TYPE_VIDEO' undeclared (first use in this function)
av_log.c: At top level:
av_log.c:105:6: warning: no previous prototype for 'set_av_log_callback' [-Wmissing-prototypes]
make: *** [av_log.o] Error 1
make: *** Waiting for unfinished jobs....

```

Whoops, there's an error!

```
$ sudo make install
./version.sh
cc -MD -MP -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I.  -D_REENTRANT -I/usr/include/     -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include/freetype2     -I/usr/local/include   -c -o av_log.o av_log.c
av_log.c: In function 'extract_msg_type_from_ctx':
av_log.c:59:35: error: 'CODEC_TYPE_AUDIO' undeclared (first use in this function)
av_log.c:59:35: note: each undeclared identifier is reported only once for each function it appears in
av_log.c:62:42: error: 'CODEC_TYPE_VIDEO' undeclared (first use in this function)
av_log.c: At top level:
av_log.c:105:6: warning: no previous prototype for 'set_av_log_callback' [-Wmissing-prototypes]
make: *** [av_log.o] Error 1

```

[edit] By the way, I also tried configuring with "--cc=gcc-4.4" Still no luck.

w00t more errors.

Whats going on?

---

### Post by Perfect Storm on 2011-12-14
Tried with PPA instead?

```
sudo add-apt-repository ppa:ripps818/coreavc
sudo apt-get update
sudo apt-get install mplayer
```

---

