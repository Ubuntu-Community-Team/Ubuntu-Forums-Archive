---
title: "Can not play DVD with Mplayer !? (read a lot of posts!)"
date: 2006-04-22
forum: General Help
---

### Post by sha_man on 2006-04-22
Hello

I have:
Breezy, P4 3 Ghz, 768 MBram, ATI radeon 9800

I want to play a DVD(my region code) with mplayer, doesn't work ! :mad: :mad: :mad:  I get no sound, the video is *very* slow/choppy/jumping, I can NOT click on any menu and not acces the movie, etc....

Here the error code (command line):
```
 mplayer -channels 6 -ao alsa:mmap:noblock:device=hw=0.1 /dev/hdb

MPlayer dev-CVS--4.0.2 (C) 2000-2005 MPlayer Team
CPU: Intel Pentium 4/Xeon/Celeron Northwood (Family: 8, Stepping: 3)
Detected cache-line size is 64 bytes
MMX2 supported but disabled [COLOR="Red"]<--WHY ?[/COLOR]
SSE2 supported but disabled [COLOR="Red"]<--WHY?[/COLOR]
CPUflags:  MMX: 1 MMX2: 0 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 0
Compiled for x86 CPU with extensions: MMX SSE



86 audio & 200 video codecs
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0 : No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory [COLOR="Red"]<-- ???[/COLOR]
Failed to open LIRC support.
You will not be able to use your remote control.
Playing /dev/hdb.
Cache fill:  0.00% (0 bytes)    MPEG-PS file format detected.

Too many video packets in the buffer: (4096 in 8273565 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
MPEG: No audio stream found -> no sound. [COLOR="Red"]<-- DVD DOES have Audio![/COLOR]
VIDEO:  MPEG2  720x576  (aspect 2)  25.000 fps  9800.0 kbps (1225.0 kbyte/s)
vo: X11 running at 1280x1024 with depth 24 and 32 bpp (":0.0" => local display)
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 576 (preferred csp: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec. [COLOR="Red"]<-- Got everything from apt-get !?[/COLOR]
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm:libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
Audio: no sound
Starting playback...
VDec: vo config request - 720 x 576 (preferred csp: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [x11] 720x576 => 768x576 Planar YV12
SwScaler: using unscaled Planar YV12 -> BGRA special converter
No bind found for key MOUSE_BTN0 [COLOR="Red"]<-- Why not found??? I do have a mouse.[/COLOR]
No bind found for key MOUSE_BTN2
No bind found for key MOUSE_BTN2
No bind found for key MOUSE_BTN0

```

However, clicking on menus and so watch the movie does work with VLC Player, but the video choppy too and without sound.
I can't install the fglrx drivers (still not working :mad: ), that may cause the slowness of playback... 
I have no surround 5.1, only the 2 front speakers worked at the beginning, then I managed to playback with 4 (2 front + subwoofer + center), but not 6 ...:(  with the help of this guide: [http://gentoo-wiki.com/HOWTO_Surround_Sound](http://gentoo-wiki.com/HOWTO_Surround_Sound)

The 2 most important things (Video & Sound) do **NOT** work correctly, despite my efforts... :mad: 

So, I begin to ask me: [SIZE="4"]What does actually work as it should (for me) in Ubuntu (Linux)?!? [/SIZE] (It's not only the fault of ubuntu/linux, I know that!)
Still, I didn't have *any* of these problems with Windows! Surround working PERFECTLY, Video (ati) with maximal acceleration, optimal use of it (altough this is more the fault of ATI).

---

