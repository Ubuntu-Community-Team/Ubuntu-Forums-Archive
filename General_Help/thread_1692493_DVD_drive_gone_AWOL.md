---
title: "DVD drive gone AWOL"
date: 2011-02-21
forum: General Help
---

### Post by electronictim on 2011-02-21
Hullo there.  A little while ago I installed lubuntu 10.04 on a partition on my (somewhat) old sony vaio desktop.  It's great, I do love it - only problem is that the DVD drive is not recognised - at least it doesn't show up in the file manager, and isn't listed when I do "ls -l /media".  Any clues?

Thanks.

---

### Post by bobcollard on 2011-02-21
> **electronictim said:**
> Hullo there.  A little while ago I installed lubuntu 10.04 on a partition on my (somewhat) old sony vaio desktop.  It's great, I do love it - only problem is that the DVD drive is not recognised - at least it doesn't show up in the file manager, and isn't listed when I do "ls -l /media".  Any clues?

Thanks.
No reason for it to show up in the file manager unless a disk is present.  As for the command it works on my Dell laptop so it is the correct one.  Have you tried to play a cd or a dvd?

---

### Post by electronictim on 2011-02-21
Oh dear - what an idiot!  I thought I'd tried that, but clearly I hadn't, because it showed up as soon as I put a disk in.  However, although I can open the VIDEO_TS and AUDIO_TS folders in file manager, both vlc and mplayer seem unable to play the disk.  They recognise what it contains, but half a second after pressing play, they stop.  Have tried with several DVDs...

---

### Post by bobcollard on 2011-02-21
> **electronictim said:**
> Oh dear - what an idiot!  I thought I'd tried that, but clearly I hadn't, because it showed up as soon as I put a disk in.  However, although I can open the VIDEO_TS and AUDIO_TS folders in file manager, both vlc and mplayer seem unable to play the disk.  They recognise what it contains, but half a second after pressing play, they stop.  Have tried with several DVDs...
Probably missing codecs.  Open Synaptic and search for "restricted" w/o quotes, then, according to which version you are using, install the restricted-extras

---

### Post by electronictim on 2011-02-21
Thanks for the advice.  Have installed as advised.  No change in VLC response: disc is recognised, but will not play.  Selecting 'No DVD Menus' returns error message 'DVDRead could not read block 0.'  (VLC uses its own codecs does it not?)

Mplayer seems to try harder: the disc spins, the laser moves, but ultimately the DVD tracks are skipped through quickly, with no audio or video output, until the following error message appears: 'Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory'.

I've made sure the necessary libvdpau files are installed in Synaptic...not sure what my next move should be...

---

### Post by heyho on 2011-02-21
Have you tried mplayer from terminal?  It might give more detailed output on the error.

```
mplayer dvd://1
```

---

### Post by electronictim on 2011-02-21
Thanks for the suggestion.  RUnning from terminal returns this:

```

theeb@Penfold:~$ mplayer dvd://1
MPlayer 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvd://1.
libdvdread: Encrypted DVD support unavailable.
************************************************
**                                            **
**  No css library available. See             **
**  /usr/share/doc/libdvdread4/README.Debian  **
**  for more information.                     **
**                                            **
************************************************
*** Zero check failed in /build/buildd/libdvdread-4.1.3/src/ifo_read.c:520
    for vmgi_mat->zero_6 = 0x0000000b00000000000000000000000000000000000000000000000000000000
There are 12 titles on this DVD.
There are 1 angles in this DVD title.
number of audio channels on disk: 0.
number of subtitles on disk: 0


Exiting... (End of file)
theeb@Penfold:~$ 

```

The readme file at /usr/share/doc/libdvdread4/README.Debian is this:


```
libdvdread for Debian
---------------------

Many DVDs use CSS[0]. To play these discs, a special library is needed to decode
them, libdvdcss. Due to legal problems in some particular countries, Debian does
not distribute libdvdcss.

If it is legal for you to use CSS in your juristiction, you can:

  * Install the packages from <http://unofficial.debian-maintainers.org/>.

  * Manually download and compile the source code from
    <http://www.videolan.org/developers/libdvdcss.html>.

 [0] <http://en.wikipedia.org/wiki/Content_Scramble_System>

 -- Daniel Baumann <daniel@debian.org>  Fri, 02 Oct 2009 16:10:06 +0200
```

I'm not sure what to do with the files available at the websites suggested - I'm new to linux.  (I had a look for libdvdread in synaptic: all 3 results returned are already installed)

Thanks again for the help.

---

### Post by electronictim on 2011-02-21
Okay, some success.  I downloaded the 'libdvdcss2_1.2.10-1_i386.deb' package and ran it.  Seems to have installed okay.  Now, if I open VLC and then open the disk, it plays!  Hurrah!  Many thanks.

However, if I try to play in Mplayer, no joy.  Running from terminal, I get this:


```
theeb@Penfold:~$ mplayer dvd://1
MPlayer 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvd://1.
libdvdread: Using libdvdcss version 1.2.10 for DVD access
*** Zero check failed in /build/buildd/libdvdread-4.1.3/src/ifo_read.c:520
    for vmgi_mat->zero_6 = 0x0000000b00000000000000000000000000000000000000000000000000000000
There are 12 titles on this DVD.
There are 1 angles in this DVD title.

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000170
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0000020f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00021347
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x000244ff
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0002454c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x0021e4c1
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x0021e50e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x00222456
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x002224b4
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x00222511
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x0022259d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x0022a2dd
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_0.VOB at 0x0022e121
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_1.VOB at 0x0022e135
libdvdread: Elapsed time 0
libdvdread: Found 9 VTS's
libdvdread: Elapsed time 0
number of audio channels on disk: 0.
number of subtitles on disk: 0
MPEG-PS file format detected.
MPEG: No audio stream found -> no sound.
VIDEO:  MPEG2  720x576  (aspect 2)  25.000 fps  8000.0 kbps (1000.0 kbyte/s)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
[VO_3DFX] Unable to open /dev/3dfx.
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
[vdpau] Error when calling vdp_device_create_x11: 1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffmpeg2] vfm: ffmpeg (FFmpeg MPEG-2)
==========================================================================
Audio: no sound
Starting playback...
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 720x576 => 768x576 Planar YV12 
[mpeg2video @ 0x674e760]Warning MVs not available
[mpeg2video @ 0x674e760]concealing 1530 DC, 1530 AC, 1530 MV errors
V:   0.6  11/ 11 ??% ??% ??,?% 0 0 

Exiting... (End of file)
theeb@Penfold:~$ ^C
theeb@Penfold:~$ 

```

And if I try to run it in VLC through the terminal, also no joy:

```
theeb@Penfold:~$ vlc dvd://1
VLC media player 1.1.4 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x851b914] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Blocked: call to setlocale(6, "")
Blocked: call to sigaction(17, 0xb737e0d4, 0xb737e048)
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
Blocked: call to setenv("ORBIT_SOCKETDIR", "/tmp/orbit-theeb", 1)
Warning: call to srand(1298542703)
Warning: call to rand()
Blocked: call to setlocale(6, "")

(process:9424): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
Warning: call to signal(13, 0x1)
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Can't stat 1
No such file or directory
libdvdnav: vm: failed to open/read the DVD
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Can't stat 1
No such file or directory
[0x87cd2ac] dvdread demux error: DVDRead cannot open source: 1
[0xb7400774] main input error: open of `dvd://1' failed: (null)
Warning: call to rand()
Warning: call to rand()
Warning: call to rand()
Warning: call to rand()
^C[0x85b3894] signals interface error: Caught Interrupt signal, exiting...
theeb@Penfold:~$ 
```

Anyway, the DVD's working now, which is the main thing.  I'm quite confused though...if anyone can shed light, I'd be most appreciative...

---

