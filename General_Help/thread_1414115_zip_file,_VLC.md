---
title: "zip file, VLC"
date: 2010-02-23
forum: General Help
---

### Post by motorhead_1 on 2010-02-23
I've downloaded a .zip file, it's wmv file. however when I try to open it I've got this message:   p, li { white-space: pre-wrap; }  [COLOR=#FF0000]No suitable decoder module:[/COLOR]
 [COLOR=#000000]VLC does not support the audio or video format "MSS2". Unfortunately there is no way for you to fix this.[/COLOR]
 [COLOR=#000000][/COLOR]

---

### Post by Ozymandias_117 on 2010-02-23
It may sound like a dumb question... But did you unzip the file?

---

### Post by Enigmapond on 2010-02-23
I'm afraid you are out of luck. A quick Google search indicates that the MSS2 video codec is   proprietary Microsoft code which has yet to be reverse engineered. There  is no standalone QuickTime codec for it. Neither **VLC**, **Perian**,  nor **Mplayer** can handle it. It's not a normal wmv file and there is no codec available in Linux for this.

Cheers!

---

### Post by motorhead_1 on 2010-02-23
I've actually tried to open unzip it with Archive Manager and I 've this error: 
Archive:  /home/daitarn/Desktop/scalping.zip
[/home/daitarn/Desktop/scalping.zip]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/daitarn/Desktop/scalping.zip or
          /home/daitarn/Desktop/scalping.zip.zip, and cannot find /home/daitarn/Desktop/scalping.zip.ZIP, period.

therefore I've used the Open with Archive Mounter and from the zip file I had a sort of zip file which can be accessed, however I cannot open the wmv file that is inside this 'mounted zip file'.

---

### Post by motorhead_1 on 2010-02-23
> **Enigmapond said:**
> I'm afraid you are out of luck. A quick Google search indicates that the MSS2 video codec is   proprietary Microsoft code which has yet to be reverse engineered. There  is no standalone QuickTime codec for it. Neither **VLC**, **Perian**,  nor **Mplayer** can handle it. It's not a normal wmv file and there is no codec available in Linux for this.

Cheers!
ouch! :( thanks anyway...

---

### Post by motorhead_1 on 2010-02-23
I guess there's no way to convert it and read it then...

---

### Post by mc4man on 2010-02-23
mplayer with w32codecs installed (on a 32 bit install) or a 32 bit mplayer installed  on a 64 bit system can playback MSS2 video

Ex.
> doug@doug-desktop:~$ mplayer '/home/doug/Videos/mss2_speech.wmv' 
MPlayer SVN-r30230-4.3.4 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/doug/Videos/mss2_speech.wmv.
ASF file format detected.
[asfheader] Audio stream found, -aid 1
[asfheader] Video stream found, -vid 2
VIDEO:  [MSS2]  800x600  24bpp  1000.000 fps   90.0 kbps (11.0 kbyte/s)
Clip info:
 title: ScreenCap Demo #3
 author: Joe Powell
 copyright: Microsoft Corporation 2002
 comments: Demo of the Windows Media Screen 9 Series codec.
==========================================================================
Opening video decoder: [dmo] DMO video codecs
DMO dll supports VO Optimizations 0 1
DMO dll might use previous sample when requested
Decoder supports the following formats: RGB8 RGB555 RGB565 RGB24 RGB32 
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
Movie-Aspect is undefined - no prescaling applied.
[swscaler @ 0xa8f3150]BICUBIC scaler, from bgra to yuv420p using MMX2
VO: [xv] 800x600 => 800x600 Planar YV12 
Selected video codec: [wmsdmod] vfm: dmo (Windows Media Screen Codec 2)
==========================================================================
==========================================================================
Opening audio decoder: [dmo] Win32/DMO decoders
AUDIO: 22050 Hz, 1 ch, s16le, 20.0 kbit/5.67% (ratio: 2500->44100)
Selected audio codec: [wma9spdmo] afm: dmo (Windows Media Audio 9 Speech DMO)
==========================================================================
AO: [alsa] 22050Hz 1ch s16le (2 bytes per sample)
Starting playback...


---

### Post by motorhead_1 on 2010-03-08
> **mc4man said:**
> mplayer with w32codecs installed (on a 32 bit install) or a 32 bit mplayer installed  on a 64 bit system can playback MSS2 video

Ex.
I've installed these codecs following [this]("http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-in-ubuntu-904-jaunty.html") but it seems that I still cannot play those MSS2 ....

[https://launchpad.net/~rvm/+archive/mplayer](https://launchpad.net/~rvm/+archive/mplayer)

---

### Post by andrew.46 on 2010-03-08
Hi Enigmapond,

> **Enigmapond said:**
> I'm afraid you are out of luck. A quick Google search indicates that the MSS2 video codec is   proprietary Microsoft code which has yet to be reverse engineered. There  is no standalone QuickTime codec for it. Neither **VLC**, **Perian**,  nor **Mplayer** can handle it.

Well, this is not entirely true as the 32 bit MPlayer can play these files by using an external windows codec. Using this file:

```
wget http://samples.mplayerhq.hu/V-codecs/MSS2/intro_windows.wmv
```

you can see MPlayer successfully open the file:

```

andrew@skamandros~/Desktop$ mplayer -vfm dmo intro_windows.wmv 
MPlayer SVN-r30860-4.3.3 (C) 2000-2010 MPlayer Team

Playing intro_windows.wmv.
ASF file format detected.
[asfheader] Audio stream found, -aid 1
[asfheader] Video stream found, -vid 2
**[COLOR="Red"]VIDEO:  [MSS2]  800x548  24bpp  1000.000 fps  250.0 kbps (30.5 kbyte/s)[/COLOR]**
==========================================================================
Trying to force video codec driver family dmo...
Opening video decoder: [dmo] DMO video codecs
DMO dll supports VO Optimizations 0 1
DMO dll might use previous sample when requested
Decoder supports the following formats: RGB8 RGB555 RGB565 RGB24 RGB32 
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
Movie-Aspect is undefined - no prescaling applied.
[swscaler @ 0x8ffddb0]BICUBIC scaler, from bgra to yuv420p using MMX2
VO: [xv] 800x548 => 800x548 Planar YV12 
**[COLOR="Red"]Selected video codec: [wmsdmod] vfm: dmo (Windows Media Screen Codec 2)[/COLOR]**
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 1 ch, s16le, 32.0 kbit/4.54% (ratio: 4006->88200)
Selected audio codec: [ffwmav2] afm: ffmpeg (DivX audio v2 (FFmpeg))
==========================================================================
AO: [oss] 44100Hz 1ch s16le (2 bytes per sample)
Starting playback...
A:  18.0 V:  18.0 A-V:  0.019 ct: -0.045  81/ 81  7%  6%  0.3% 0 0 

```

I attach a screenshot to demonstrate the file successfully playing...

Andrew

---

