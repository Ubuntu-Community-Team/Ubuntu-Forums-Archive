---
title: "VC-1 on AMD64"
date: 2010-03-23
forum: General Help
---

### Post by ZRotheohv on 2010-03-23
I've been lurking around these forums for years now, and every problem I've had has been answered by a simple search. But I'm finally at a loss. 

I have an mkv file that contains a VC-1 video track and (from what I gather) it won't work on an AMD64 machine with anything out of the box. Many threads have been hopeful, but patches and downloads are hopelessly out of date and files don't exist anymore. Even the code is for way back in the Breezy times. 

My goal really isn't even to play the file, but to use mencoder to make it an mpeg4 file (which I could do if I had a codec). But I assume if mencoder can encode it, mplayer can play it. So, is there any way to get mplayer/mencoder to understand a VC-1 video on an AMD64 machine? 

Thanks a lot these forums are amazing!

---

### Post by andrew.46 on 2010-03-23
Hi ZRotheohv,

I tested a sample vc-1 file:

```
wget http://samples.mplayerhq.hu/V-codecs/WVC1/Test_1440x576_WVC1_6Mbps.wmv
```

and it can be played under MPlayer with *ffvc1*, thus making it possible to play under 64bit or 32bit as long as the version of libavcodec is modern enough:

```

andrew@skamandros~/Desktop$ **[COLOR="Red"]mplayer -vc ffvc1 Test_1440x576_WVC1_6Mbps.wmv [/COLOR]**
MPlayer SVN-r30947-4.3.3 (C) 2000-2010 MPlayer Team

Playing Test_1440x576_WVC1_6Mbps.wmv.
ASF file format detected.
[asfheader] Video stream found, -vid 1
VIDEO:  [WVC1]  1440x576  24bpp  1000.000 fps  6000.0 kbps (732.4 kbyte/s)
==========================================================================
Forced video codec: ffvc1
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffvc1] vfm: ffmpeg (FFmpeg WVC1)
==========================================================================
Audio: no sound
Starting playback...
Movie-Aspect is 2.50:1 - prescaling to correct movie aspect.
VO: [xv] 1440x576 => 1440x576 Planar YV12 
V:  63.0 1450/1450 43%  2%  0.0% 0 0 

Exiting... (End of file)


```
You can check your own version of MPlayer as follows:

```

andrew@skamandros~$ **[COLOR="Red"]mplayer -vc help | grep 'vc1'[/COLOR]**

ffvc1       ffmpeg    problems  FFmpeg WVC1  [vc1]
ffvc1vdpau  ffmpeg    problems  FFmpeg WVC1 (VDPAU)  [vc1_vdpau]
wmvvc1dmo   dmo       working   Windows Media Video (VC-1) Advanced Profile  [wvc1dmod.dll]

```

It should not be difficult to transcode from here with MEncoder or even better use a modern version of FFmpeg...

All the best,

Andrew

---

### Post by ZRotheohv on 2010-03-24
Thanks for the sample video! It worked like a charm (and I even trained my eyes to cross so I could see it in 3D) but my mkv still doesn't want to show video. Here's the output I get when using your file:

```

zack@zack-desktop:~$ mplayer -vc ffvc1 Test_1440x576_WVC1_6Mbps.wmv
MPlayer UNKNOWN-4.4.1 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing Test_1440x576_WVC1_6Mbps.wmv.
ASF file format detected.
[asfheader] Video stream found, -vid 1
VIDEO:  [WVC1]  1440x576  24bpp  1000.000 fps  6000.0 kbps (732.4 kbyte/s)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Forced video codec: ffvc1
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffvc1] vfm: ffmpeg (FFmpeg WVC1)
==========================================================================
Audio: no sound
Starting playback...
VDec: vo config request - 1440 x 576 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 2.50:1 - prescaling to correct movie aspect.
VO: [xv] 1440x576 => 1440x576 Planar YV12 
V:  63.0 1450/1450 41%  2%  0.0% 0 0 

Exiting... (End of file)


```

And the grep:

```

zack@zack-desktop:~$ mplayer -vc help | grep 'vc1'

ffvc1       ffmpeg    problems  FFmpeg WVC1  [vc1]
ffvc1vdpau  ffmpeg    problems  FFmpeg WVC1 (VDPAU)  [vc1_vdpau]
wmvvc1dmo   dmo       working   Windows Media Video (VC-1) Advanced Profile  [wvc1dmod.dll]


```

But when I play my file using the same command as yours I get this:

```

zack@zack-desktop:~$ mplayer -vc ffvc1 /home/zack/Desktop/video.mkv
MPlayer UNKNOWN-4.4.1 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/zack/Desktop/video.mkv.
[mkv] Track ID 1: video (V_MS/VFW/FOURCC), -vid 0
[mkv] Track ID 2: audio (A_AC3) "3/2+1", -aid 0, -alang eng
[mkv] Track ID 3: audio (A_AC3) "1/0", -aid 1, -alang fra
[mkv] Subtitle type 'S_HDMV/PGS' is not supported.
[mkv] Track ID 4: subtitles (S_HDMV/PGS), -sid 0, -slang eng
[mkv] Subtitle type 'S_HDMV/PGS' is not supported.
[mkv] Track ID 6: subtitles (S_HDMV/PGS), -sid 1, -slang eng
[mkv] Subtitle type 'S_HDMV/PGS' is not supported.
[mkv] Track ID 8: subtitles (S_HDMV/PGS), -sid 2, -slang fra
[mkv] Subtitle type 'S_HDMV/PGS' is not supported.
[mkv] Track ID 10: subtitles (S_HDMV/PGS), -sid 3, -slang spa
[mkv] Will play video track 1.
Matroska file format detected.
VIDEO:  [WVC1]  1920x1080  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Forced video codec: ffvc1
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
[vc1 @ 0x7fbfe59eea80]Incomplete extradata
Could not open codec.
VDecoder init failed :(
Cannot find codec matching selected -vo and video format 0x31435657.
Read DOCS/HTML/en/codecs.html!
==========================================================================
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 640.0 kbit/41.67% (ratio: 80000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
[pulse] working around probably broken pause functionality,
        see [http://www.pulseaudio.org/ticket/440](http://www.pulseaudio.org/ticket/440)
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:   7.0 (06.9) of 10179.8 ( 2:49:39.7)  2.1% 

MPlayer interrupted by signal 2 in module: key_events
A:   7.0 (06.9) of 10179.8 ( 2:49:39.7)  2.1% 
Exiting... (Quit)


```

From what I see I have "Incomplete extradata". The audio plays fine, however. Thanks again for your help!

---

### Post by andrew.46 on 2010-03-24
Hi ZRotheohv,

> **ZRotheohv said:**
> From what I see I have "Incomplete extradata". The audio plays fine, however. Thanks again for your help!

Looks like this is a bug that has been fixed in libavcodec:

[http://lists.mplayerhq.hu/pipermail/ffmpeg-devel/2009-October/076695.html](http://lists.mplayerhq.hu/pipermail/ffmpeg-devel/2009-October/076695.html)

Unfortunately your copy of MPlayer is too old to take advantage of the fix and I am not completely sure if the various PPA's have versions of MPlayer that contain this fix from October/November 2009.

Andrew

---

