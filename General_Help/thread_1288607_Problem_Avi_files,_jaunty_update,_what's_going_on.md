---
title: "Problem? Avi files, jaunty update, what's going on?"
date: 2009-10-11
forum: General Help
---

### Post by CD27 on 2009-10-11
Everytime I try to play an avi file it doesn't show the video. I don't know what the problem is, it hasn't got any real problems playing anything else. But it doesn't matter what playing I play it in, each gives me a different error or just doesn't show anything at all. I followed this tutorial:


[http://ubuntuforums.org/showthread.php?t=1081070](http://ubuntuforums.org/showthread.php?t=1081070)

To the "T" and when I open SMPlayer to play the video this is the error I get from it:

```

mplayer -noquiet -nofs -sub-fuzziness 1 -identify -slave -vo xv -ao alsa -zoom -nokeepaspect -framedrop -nodr -double -input conf=/usr/share/smplayer/input.conf -stop-xscreensaver -wid 65011727 -monitorpixelaspect 1 -*** -embeddedfonts -***-line-spacing 0 -***-font-scale 1 -***-styles /home/psinetic/.config/smplayer/styles.*** -fontconfig -font Arial -subcp ISO-8859-1 -vid 0 -aid 1 -subpos 100 -volume 40 -cache 2000 -ss 6 -osdlevel 0 -nocorrect-pts -vf-add screenshot -slices -channels 2 -af scaletempo,equalizer=0:0:0:0:0:0:0:0:0:0 /media/My Book_/Icons/jen.avi

MPlayer SVN-r29770-4.3.3 (C) 2000-2009 MPlayer Team
Terminal type `unknown' is not defined.

Playing /media/My Book_/Icons/jen.avi.

Cache fill:  0.00% (0 bytes)   
AVI file format detected.
ID_VIDEO_ID=0
[aviheader] Video stream found, -vid 0
ID_AUDIO_ID=1
[aviheader] Audio stream found, -aid 1
VIDEO:  [IV41]  1360x768  24bpp  200.000 fps  1631.7 kbps (199.2 kbyte/s)
ID_FILENAME=/media/My Book_/Icons/jen.avi
ID_DEMUXER=avi
ID_VIDEO_FORMAT=IV41
ID_VIDEO_BITRATE=1631704
ID_VIDEO_WIDTH=1360
ID_VIDEO_HEIGHT=768
ID_VIDEO_FPS=200.000
ID_VIDEO_ASPECT=0.0000
ID_AUDIO_FORMAT=85
ID_AUDIO_BITRATE=56000
ID_AUDIO_RATE=0
ID_AUDIO_NCH=0
ID_LENGTH=1209.68
ID_SEEKABLE=1
ID_CHAPTERS=0
[***] auto-open
Opening video filter: [screenshot]
[***] Init
[***] Updating font cache.
==========================================================================
Requested video codec family [indeo4] (vfm=vfw) not available.
Enable it at compilation.
Opening video decoder: [xanim] XAnim codecs
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
Movie-Aspect is undefined - no prescaling applied.
[swscaler @ 0x2ecbed0]using unscaled yuv410p -> yuv420p special converter
[swscaler @ 0x2ed3d60]No accelerated colorspace conversion found.
VO: [xv] 1360x768 => 1360x768 Planar YV12  [zoom]
X11 error: BadAccess during XSelectInput Call
X11 error: The 'ButtonPressMask' mask of specified window has probably already used by another appication (see man XSelectInput)
X11 error: MPlayer discards mouse control (reconfiguring)
xacodec: failed to dlopen /usr/lib/codecs/vid_iv41.xa while /usr/lib/codecs/vid_iv41.xa: wrong ELF class: ELFCLASS32
VDecoder init failed :(
Cannot find codec matching selected -vo and video format 0x31345649.
==========================================================================
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 22050 Hz, 2 ch, s16le, 56.0 kbit/7.94% (ratio: 7000->88200)
ID_AUDIO_BITRATE=56000
ID_AUDIO_RATE=22050
ID_AUDIO_NCH=2
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
[equalizer] Limiting the number of filters to 9 due to low sample rate.
[equalizer] Limiting the number of filters to 9 due to low sample rate.
[equalizer] Limiting the number of filters to 9 due to low sample rate.
AO: [alsa] 22050Hz 2ch floatle (4 bytes per sample)
[equalizer] Limiting the number of filters to 9 due to low sample rate.
[equalizer] Limiting the number of filters to 9 due to low sample rate.
ID_AUDIO_CODEC=mp3
[AO_ALSA] Unable to find simple control 'PCM',0.
[Mixer] No hardware mixing, inserting volume filter.
[equalizer] Limiting the number of filters to 9 due to low sample rate.
Video: no video
Starting playback...


MPlayer interrupted by signal 11 in module: seek
ID_SIGNAL=11
- MPlayer crashed by bad usage of CPU/FPU/RAM.
  Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
  disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.

```

Also when I run

```

sudo apt-get update

```


I get this at the end:

```

Hit http://wine.budgetdedicated.com jaunty/main Packages
Fetched 198B in 1s (117B/s)
Reading package lists... Done
W: GPG error: http://repository.cairo-dock.org intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1392A97E41317877
W: You may want to run apt-get update to correct these problems

```

does anyone have any ideas about this?

---

### Post by kortak on 2009-12-12
Hello,

I have exactly the same problem with jaunty.  although I have installed all the required plugins (non-free-codecs).  If I try to read an AVI and some mpgs as well, all the different player will send me out with a different behaviour.  With gxine I will get the sound only, mplyer will crash as well as vlc with a very strange error:

> 
VLC media player 0.9.9a Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.9a Grishenko - (c) 1996-2009 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintainer-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=2ubuntu1' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-realrtsp' '--disable-dv' '--enable-x264' '--enable-alsa' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[00000461] main access error: cannot resolve srv151.odsiebie.com port 80 : Name or service not known
[00000461] access_http access error: cannot connect to srv151.odsiebie.com:80
[????????] x11 video output error: X11 request 132.19 failed with error code 11:
 BadAlloc (insufficient resources for operation)
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  132 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  81
  Current serial number in output stream:  82



I have to tell that everything was working fine on 8.04

---

### Post by FearfulJesuit on 2009-12-12
CD27, the error report seems to state that you're missing something from vfm (video codec family). It is possible that you don't have an avi driver installed. Maybe try [http://code.google.com/p/coreavc-for-linux/wiki/MplayerInstallation](http://code.google.com/p/coreavc-for-linux/wiki/MplayerInstallation)

---

### Post by kortak on 2009-12-12
It seems that it is related to X11 and I am now able to have an AVI file running in VLC only by setting the video output to "X11 video output" in tools.

However I don't know how to setup this option for the other players

---

