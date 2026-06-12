---
title: "how to view .mov files"
date: 2009-11-29
forum: General Help
---

### Post by P3t3r on 2009-11-29
Can one view .mov files (quicktime movies) in VLC or another video player? I have some .mov files I like to watch, but VLC errors > No suitable decoder module:
VLC does not support the audio or video format "WMV3". Unfortunately there is no way for you to fix this.

If not in vlc, what video players for kubuntu CAN view .mov files?

---

### Post by NoaHall on 2009-11-29
You need to download ubuntu-restricted-extras.

run ```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by arvevans on 2009-11-29
vlc, xine, & mplayer can all do many video formats, including .mov or quicktime movies.  The real issue is having the proper codecs, some of which are in the non-free repositories.

You might want to start with Graphics (universe) repository and look for a program called "vlc-data" as a starting place.

Arv
_._

---

### Post by P3t3r on 2009-11-30
> **NoaHall said:**
> You need to download ubuntu-restricted-extras.

run ```
sudo apt-get install ubuntu-restricted-extras
```
Added, still same error on quicktime movies. 

> **arvevans said:**
> vlc, xine, & mplayer can all do many video formats, including .mov or quicktime movies.  The real issue is having the proper codecs, some of which are in the non-free repositories.

You might want to start with Graphics (universe) repository and look for a program called "vlc-data" as a starting place.

Arv
_._vlc-data was already installed (maybe by the restricted-extras above), so not really working either...

---

### Post by mc4man on 2009-11-30
> VLC does not support the audio or video format "WMV3
The repo and ppa vlc builds depend directly on libavcodec and will decode wmv3 to the extent the installed libavcodec can.

Also if the wmv contains wma3 audio that is also a factor ( at present the ubuntu libavcodec cannot decode wma3, will decode wma2

mplayer and xine based players can decode wmv3 and if present wma3 thru w32codecs ( available from [medibuntu]("http://packages.medibuntu.org/")

If you wish to test your installed libavcodec then 
```
sudo apt-get install ffmpeg 
```

And if using pulse audio search libsdl in synaptic and install this (showing karmic version
libsdl1.2debian-pulseaudio

Then simply go in a terminal and see if decoding happens
ffplay /path/to/filename

Ex. of wmv3 with wma2 audio
> 
doug@doug-desktop:~$ ffplay '/home/doug/cxemm_earthclip01_480p.wmv' 
FFplay version SVN-r20627, Copyright (c) 2003-2009 Fabrice Bellard, et al.
  built on Nov 26 2009 22:48:25 with gcc 4.3.4
  configuration: --extra-cflags='-Wall -g ' --cc=gcc-4.3 --enable-gpl --enable-version3 --enable-nonfree --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libx264 --enable-libxvid --enable-x11grab --disable-vdpau --enable-postproc --enable-libopenjpeg --enable-libvorbis  --enable-libspeex --disable-altivec --disable-armv5te --disable-armv6 --disable-vis
  libavutil     50. 5. 1 / 50. 5. 1
  libavcodec    52.42. 0 / 52.42. 0
  libavformat   52.39. 2 / 52.39. 2
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0. 7. 2 /  0. 7. 2
  libpostproc   51. 2. 0 / 51. 2. 0
[wmv3 @ 0xa7fa3a0]Extra data: 8 bits left, value: 0
Input #0, asf, from '/home/doug/cxemm_earthclip01_480p.wmv':
  Duration: 00:01:25.58, start: 3.000000, bitrate: 2526 kb/s
    Stream #0.0: Audio: wmav2, 44100 Hz, 2 channels, s16, 256 kb/s
    Stream #0.1: Video: wmv3, yuv420p, 854x480, 2244 kb/s, PAR 1:1 DAR 427:240, 29.97 tbr, 1k tbn, 1k tbc

Ex. of how vlc works with wmv3/wma2
> [0x993e178] avcodec decoder debug: libavcodec initialized (interface 0x342a00)
[0x993e178] avcodec decoder debug: ffmpeg codec (Windows Media Audio 2) started
[0x992ffb8] avcodec decoder debug: using direct rendering
[0x992ffb8] avcodec decoder debug: ffmpeg codec (Windows Media Video 3) started
[0x992ffb8] main decoder debug: using decoder module "avcodec"


(( if ubuntu did a better job with vlc and ffmpeg then you'd have no issues with wma3 or wmal
> [0x99331f8] asf demux debug: added new audio stream(codec:0x162,ID:1)
[0x9a144a0] avcodec decoder debug: ffmpeg codec (Windows Media Audio Professional) started
[0x9a144a0] main decoder debug: using decoder module "avcodec"


> [0x9672308] asf demux debug: added new audio stream(codec:0x163,ID:1)
[0x967daf0] dmo decoder debug: DMO codec for wmal may work with dll=wma9dmod.dll
[0x967daf0] dmo decoder debug: DMO input type set


---

