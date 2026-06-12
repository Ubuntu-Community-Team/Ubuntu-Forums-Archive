---
title: "Windows Media Speech Decoder plugin - where do i get it?"
date: 2010-07-14
forum: General Help
---

### Post by QueenZ on 2010-07-14
MPlayer asked for Windows Media Speech Decoder plugin, it tried searching for the plugin but it wasn't found. I also couldn't find it in Synaptic Package manager... i wonder where and how i can get it...

---

### Post by QueenZ on 2010-07-14
VLC also said... "VLC does not support the audio or video format "wmas"."

---

### Post by QueenZ on 2010-07-14
any ideas...?

---

### Post by andrew.46 on 2010-07-14
Hi Queenz,

I wonder if you are using the totem player rather than MPlayer? A recent enough version of MPlayer will play these files natively. This file for example:

[http://samples.mplayerhq.hu/A-codecs/WMA9/WMAVoice/wmv3-wmaspeeech.wmv](http://samples.mplayerhq.hu/A-codecs/WMA9/WMAVoice/wmv3-wmaspeeech.wmv)

plays as follows:

```

andrew@skamandros~/Desktop$ mplayer -vfm ffmpeg wmv3-wmaspeeech.wmv 
MPlayer SVN-r31734-4.4.4 (C) 2000-2010 MPlayer Team

Playing wmv3-wmaspeeech.wmv.
ASF file format detected.
[asfheader] Audio stream found, -aid 1
[asfheader] Video stream found, -vid 2
VIDEO:  [WMV3]  176x144  24bpp  1000.000 fps   17.5 kbps ( 2.1 kbyte/s)
Clip info:
 title: test
==========================================================================
Trying to force video codec driver family ffmpeg...
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
[wmv3 @ 0x89eaec0]Extra data: 8 bits left, value: 0
Selected video codec: [ffwmv3] vfm: ffmpeg (FFmpeg WMV3/WMV9)
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 8000 Hz, 1 ch, floatle, 5.0 kbit/1.95% (ratio: 625->32000)
S**[COLOR="Red"]elected audio codec: [ffwmavoice] afm: ffmpeg (WMA Voice audio (FFmpeg))[/COLOR]**
==========================================================================
AO: [oss] 8000Hz 1ch s16le (2 bytes per sample)
Starting playback...
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 176x144 => 176x144 Planar YV12 
A:  12.7 V:  12.8 A-V: -0.080 ct:  0.065 131/131  0%  0%  0.5% 0 0 


Exiting... (End of file)
andrew@skamandros~/Desktop$ 

```

Mind you, a suitably compiled version of vlc with an up to date libavcodec will also play these files. I attach a screenshot of this happening with the same file.

Andrew

---

### Post by mc4man on 2010-07-14
A Big +1 for mplayer - get yourself a recent version, whether self built or from a ppa, pair it up with a frontend like gnome-mplayer or smplayer and you'll be in good shape.


From a gstreamer side, maverick by default handles most wm* pretty well.

For karmic and lucid adding this ppa and upgrading your gstremer plugins will also enable most wm* and bring you more up to date gstreamer wise.

[https://launchpad.net/~gstreamer-developers/+archive/ppa](https://launchpad.net/~gstreamer-developers/+archive/ppa)
The ppa's ffmpeg plugin uses  internal ffmpeg lib's, so what the system libs support is irrelevant.

Note that if on 32 bit and you installed that silly ubuntu-restricted-extras package then you should search gstreamer in synaptic and remove the gstreamer0.10-pitfdll package, it can interfere and is somewhat broken.


As an Ex. - with Andrew's sample - wmas audio and wmv3 video, with the ppa and pitfdll installed it would play with no audio. (totem

> doug@doug-desktop1:~$ gst-inspect |grep wma
pitfdll:  dmodec_wmadmodv1: DMO wmadmod decoder version 1
pitfdll:  dmodec_wmadmodv2: DMO wmadmod decoder version 2
pitfdll:  dmodec_wmadmodv3: DMO wmadmod decoder version 3
ffmpeg:  ffdec_wmavoice: FFmpeg Windows Media Audio Voice decoder
ffmpeg:  ffdec_wmav2: FFmpeg Windows Media Audio 2 decoder
ffmpeg:  ffdec_wmav1: FFmpeg Windows Media Audio 1 decoder
ffmpeg:  ffdec_wmapro: FFmpeg Windows Media Audio 9 Professional decoder
ffmpeg:  ffenc_wmav2: FFmpeg Windows Media Audio 2 encoder
ffmpeg:  ffenc_wmav1: FFmpeg Windows Media Audio 1 encoder


Removing pitfdll allowed both audio and video, plus you'll get wma3(pro) support in wmv3 video
> doug@doug-desktop1:~$ gst-inspect |grep wma
ffmpeg:  ffenc_wmav1: FFmpeg Windows Media Audio 1 encoder
ffmpeg:  ffenc_wmav2: FFmpeg Windows Media Audio 2 encoder
ffmpeg:  ffdec_wmapro: FFmpeg Windows Media Audio 9 Professional decoder
ffmpeg:  ffdec_wmav1: FFmpeg Windows Media Audio 1 decoder
ffmpeg:  ffdec_wmav2: FFmpeg Windows Media Audio 2 decoder
ffmpeg:  ffdec_wmavoice: FFmpeg Windows Media Audio Voice decoder
typefindfunctions: video/x-ms-asf: wmv, wma, wm, asf

doug@doug-desktop1:~$ gst-inspect |grep wmv
ffmpeg:  ffenc_wmv1: FFmpeg Windows Media Video 7 encoder
ffmpeg:  ffenc_wmv2: FFmpeg Windows Media Video 8 encoder
ffmpeg:  ffdec_wmv1: FFmpeg Windows Media Video 7 decoder
ffmpeg:  ffdec_wmv2: FFmpeg Windows Media Video 8 decoder
ffmpeg:  ffdec_wmv3: FFmpeg Windows Media Video 9 decoder
typefindfunctions: video/x-ms-asf: wmv, wma, wm, asf




(in maverick vlc will also support most wm* by default, though vp8 decoding is slightly broken  - whether it will be patched don't know

---

