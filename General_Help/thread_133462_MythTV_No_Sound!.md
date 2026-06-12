---
title: "MythTV: No Sound!"
date: 2006-02-20
forum: General Help
---

### Post by foof on 2006-02-20
Hi!

I have installed MythTV 0.18 and can successfully watch TV with my Asus 7134 card. I also have a Creative Audigy2 ZS sound card and I get sound if I put in an audio-CD and play it with a player, but I get no sound at all in MythTV, what can be wrong? I've tried to set everything to max in KMix, but nothing!
I have connected the little audio cable from my TV-card to Aux on the sound card.

Please help!

---

### Post by foof on 2006-02-20
This is the output from MythTV when choosing "Watch TV":
```

2006-02-20 15:00:04.782 Using protocol version 15
2006-02-20 15:00:04.787 MainServer::HandleAnnounce Playback
2006-02-20 15:00:04.787 adding: htpc as a client (events: 0)
2006-02-20 15:00:04.800 MainServer::HandleAnnounce Playback
2006-02-20 15:00:04.800 adding: htpc as a client (events: 0)
2006-02-20 15:00:04.807 adding: htpc as a remote ringbuffer
2006-02-20 15:00:04.816 Changing from None to WatchingLiveTV
2006-02-20 15:00:04.851 Unknown video codec
2006-02-20 15:00:04.851 Please go into the TV Settings, Recording Profiles and
2006-02-20 15:00:04.852 setup the four 'Software Encoders' profiles.
2006-02-20 15:00:04.852 Assuming RTjpeg for now.
2006-02-20 15:00:04.852 NVR: Error, unknown audio codec
cannot open vbi device
2006-02-20 15:00:04.877 NVR: Can't open vbi device: /dev/vbi
2006-02-20 15:00:04.896 Disable DPMS
2006-02-20 15:00:05.210 Opening audio device '/dev/dsp'.
2006-02-20 15:00:05.210 Opening OSS audio device '/dev/dsp'.
2006-02-20 15:00:05.282 Using XV port 61
2006-02-20 15:00:05.565 Changing from None to WatchingLiveTV
2006-02-20 15:00:05.583 Using realtime priority.
2006-02-20 15:00:05.610 Video timing method: USleep with busy wait

```

---

### Post by foof on 2006-02-23
I installed TV-Time and both picture and sound works great!
The image quality is also much better and TV-Time also automatically searches for available channels and the feel of the program is quick and easy!
Why can't MythTV be like this? I need MythTV because I want to be able to record tv programs. 

In mythtv-setup, what should I enter as sound device under capture card?
It now says /dev/dsp is this correct?

---

### Post by Michael Matthews on 2006-03-17
Yea, tvtime works great. Maybe the only multi-media ubuntu app that does for me.
I tried myth TV and seems to have screwed up my sound, mixer app no longer works. May have to uninstall.

I have tried transcode which has tv capture example but modules won't link,
transcode v1.0.1 (C) 2001-2003 Thomas Oestreich, 2003-2004 T. Bitterberg
[transcode] auto-probing source /dev/video0 (failed)
[transcode] V: import format    | unknown  (V=v4l2|A=(null))
[transcode] V: AV demux/sync    | (2) initial MPEG sequence / enforce frame rate[transcode] V: import frame     | 720x480  1.50:1
[transcode] V: de-interlace     | (mode=1) interpolate scanlines (fast)
[transcode] V: bits/pixel       | 0.217
[transcode] V: decoding fps,frc | 23.976,1
[transcode] V: Y'CbCr           | YV12/I420
[transcode] A: import format    | 0x2000  AC3          [48000,16,2]
[transcode] A: export format    | 0x55    MPEG layer-3 [48000,16,2]  128 kbps
[transcode] V: encoding fps,frc | 23.976,1
[transcode] A: bytes per frame  | 8008 (8008.000000)
[transcode] A: adjustment       | 0@1000
[transcode] V: IA32/AMD64 accel | sse2 (sse2 sse mmxext mmx asm C)
tc_memcpy: using sse for memcpy
[transcode] V: video buffer     | 100 @ 720x480
[import_v4l2.so] v1.3.5 (2005-03-11) (video) v4l2 | (audio) pcm
[transcode] warning : /usr/lib/transcode/export_ffmpeg.so: undefined symbol: dts_init
[transcode] warning : (dl_loader.c) loading "/usr/lib/transcode/export_ffmpeg.so" failed
[transcode] warning : (encoder.c) loading audio export module failed
[transcode] warning : failed to init export modules
[transcode] critical: plug-in initialization failed



 ffmpeg gets mediocre picture with no sound. No examples available of v4l tv capture. Try figuring that out.

/usr/bin/ffmpeg  -t 30 -s 720x480 -vd /dev/video0 -ad /dev/dsp -tvstd NTSC  tv.avi

blurry picture, no sound. Have no idea what most of the options mean and find the web site completely unhelpful.

No love :(

---

