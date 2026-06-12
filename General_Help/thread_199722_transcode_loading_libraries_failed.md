---
title: "transcode: loading libraries failed"
date: 2006-06-19
forum: General Help
---

### Post by Timokl on 2006-06-19
Hi,

I want to convert a divx file to an mpeg1 file to burn a vcd from it. However, transcode tells me it misses some lib's. Where can I find those lib's? With apt-get?

Here's my terminal log:

```
timo@ubuntu:~$ transcode -i Desktop/tokiohoteldurchdenmo.avi -y mpeg -V -k -F v,1,0 -o Desktop/tokiohoteldurchdenmo.mpg
*** WARNING: The option -V is deprecated. ***
*** Transcode internal frame handling is now in YV12 / YUV420 ***
*** format by default because most codecs can only handle this format, ***
*** otherwise leading to unnecessary time and quality wasting conversions. ***
*** If you want to have to "old" behaviour (RGB24 as internal format), ***
*** then please use the new -1/--use_rgb option ***
transcode v1.0.2 (C) 2001-2003 Thomas Oestreich, 2003-2004 T. Bitterberg
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Can't open file VIDEO_TS.IFO.
[transcode] (probe) suggested AV correction -D 0 (0 ms) | AV 0 ms | 0 ms
[transcode] auto-probing source Desktop/tokiohoteldurchdenmo.avi (ok)
[transcode] V: import format    | DivX RIFF data, AVI (V=ffmpeg|A=mp3)
[transcode] V: import frame     | 480x360  1.33:1
[transcode] V: rgb2bgr          | yes
[transcode] V: bits/pixel       | 0.417
[transcode] V: decoding fps,frc | 25.000,3
[transcode] V: Y'CbCr           | YV12/I420
[transcode] A: import format    | 0x55    MPEG layer-3 [44100,16,2]  128 kbps
[transcode] A: export format    | 0x50    MPEG layer-2 [44100,16,2]  128 kbps
[transcode] V: encoding fps,frc | 25.000,3
[transcode] A: bytes per frame  | 7056 (7056.000000)
[transcode] A: adjustment       | 0@1000
[transcode] V: IA32/AMD64 accel | sse3 (sse3 sse2 sse 3dnowext 3dnow mmxext mmx asm C)
tc_memcpy: using sse for memcpy
[transcode] V: video buffer     | 10 @ 480x360
[import_mp3.so] v0.1.4 (2003-08-04) (audio) MPEG
[import_ffmpeg.so] v0.1.12 (2004-05-07) (video) ffmpeg: MS MPEG4v1-3/MPEG4/MJPEG[transcode] warning : /usr/lib/transcode/export_mpeg.so: cannot open shared object file: No such file or directory
[transcode] warning : (dl_loader.c) loading "/usr/lib/transcode/export_mpeg.so" failed
[transcode] warning : (encoder.c) loading audio export module failed
[transcode] warning : failed to init export modules
[transcode] critical: plug-in initialization failed
timo@ubuntu:~$

```

Bye, Timo

---

### Post by Ikitt on 2006-06-27
[QUOTE=Timokl]Hi,

I want to convert a divx file to an mpeg1 file to burn a vcd from it. However, transcode tells me it misses some lib's. Where can I find those lib's? With apt-get?

Here's my terminal log:

```
timo@ubuntu:~$ transcode -i Desktop/tokiohoteldurchdenmo.avi -y mpeg -V -k -F v,1,0 -o Desktop/tokiohoteldurchdenmo.mpg
[snip]
/usr/lib/transcode/export_mpeg.so: cannot open shared object file: No such file or directory
[transcode] warning : (dl_loader.c) loading "/usr/lib/transcode/export_mpeg.so" failed
[transcode] warning : (encoder.c) loading audio export module failed
[transcode] warning : failed to init export modules
[transcode] critical: plug-in initialization failed
timo@ubuntu:~$

```
[/QUOTE]
Transcode don't have a 'mpeg' export module :)
You are probabily best served by 'ffmpeg' export module (-y ffmpeg) selecting mpeg1 encoder ( -F mpeg1 ). 'mpeg2enc' export module should be capable to do mpeg1 too, but I lack experience with this one.
Also take a look to --export_prof option, I think it may be very useful here.

HTH

---

