---
title: "unable to play WVC1 1920x1080 wmv files in ubuntu 11.10"
date: 2011-12-17
forum: General Help
---

### Post by Senny04 on 2011-12-17
Hello...
i searched the forum and everywhere but havent found a solution yet:
using Ubuntu 64bit 11.10 i cannot play the real HD 1920x1080 wmv files that are encoded with WVC1 .. no player i installed plays anything nor VLC...
I get max sound but no picture at all.
Error messages are always like "unable to decode frame" or "too many dropped frames"....
Lower resoultion with WVC1 for example this demo file which was reffered to in onother thread: ```
wget http://samples.mplayerhq.hu/V-codecs/WVC1/Test_1440x576_WVC1_6Mbps.wmv 
```  or 1920x1080 with wmv9 do work though.

```
dpkg -s mplayer | grep Version
Version: 2:1.0~rc4.dfsg1+svn33713-1

```

---

### Post by andrew.46 on 2011-12-17
Can you post the troublesome file somewhere?

---

### Post by Senny04 on 2011-12-17
It is not 1 troublesome file but every file with WVC1 encoding and 1920x1080 resolution...
Well, not every it seems... while trying to find a file to share i came across this one which works:
[Elephant's Dream 10-25 Mbps]("http://www.microsoft.com/download/en/details.aspx?id=24559")

trying to find a free to download file that doesnt work right now... any suggestions are welcome i will try

---

### Post by Senny04 on 2012-01-08
OK I tried more again... I installed the probably missing w32 and w64codecs as described here:
_[ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-on-ubuntu-11-04-natty]("http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-on-ubuntu-11-04-natty.html")_
Which all went fine... just that I am still unable to play these WVC1 videos :(
Here is the output from the commandline when i try to play such a file with mplayer:
```

user@ubuntu:~$ mplayer '/home/user/videos/VideoWVC1.wmv' 
MPlayer SVN-r33713-4.6.1 (C) 2000-2011 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/user/videos/VideoWVC1.wmv.
ASF file format detected.
[asfheader] Audio stream found, -aid 1
[asfheader] Video stream found, -vid 2
VIDEO:  [WVC1]  1920x1080  24bpp  1000.000 fps  5000.0 kbps (610.4 kbyte/s)
Clip info:
 title: VideoWVC1
 author:  
 copyright: ©  
 comments: 
Load subtitles in /home/user/videos/
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: Permission denied.
[VO_3DFX] Unable to open /dev/3dfx.
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
[vdpau] Error when calling vdp_device_create_x11: 1
==========================================================================
Requested video codec family [wmvvc1dmo] (vfm=dmo) not available.
Enable it at compilation.
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Unsupported PixelFormat 61
Unsupported PixelFormat 53
Unsupported PixelFormat 61
Unsupported PixelFormat 53
Selected video codec: [ffvc1] vfm: ffmpeg (FFmpeg WVC1)
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 6 ch, floatle, 384.0 kbit/4.17% (ratio: 48000->1152000)
Selected audio codec: [ffwmapro] afm: ffmpeg (WMA Pro audio (FFmpeg))
==========================================================================
AO: [pulse] 48000Hz 2ch floatle (4 bytes per sample)
Starting playback...
[vc1 @ 0x7fa23c1a54c0]Interlaced WVC1 support is not implemented
Error while decoding frame!
Error while decoding frame!
Error while decoding frame!
Error while decoding frame!
Error while decoding frame!
Error while decoding frame!
Error while decoding frame!
Error while decoding frame!
Error while decoding frame!
A:   3.0 V:   3.3 A-V: -0.277 ct:  0.000   9/  9 ??% ??% ??,?% 0 0 
Error while decoding frame!
A:   3.1 V:   3.4 A-V: -0.278 ct: -0.004  10/ 10 ??% ??% ??,?% 0 0 
Error while decoding frame!
A:   3.1 V:   3.4 A-V: -0.274 ct: -0.008  11/ 11 ??% ??% ??,?% 0 0 
Error while decoding frame!
A:   3.2 V:   3.4 A-V: -0.270 ct: -0.012  12/ 12 ??% ??% ??,?% 0 0 
Error while decoding frame!
A:   3.2 V:   3.5 A-V: -0.266 ct: -0.016  13/ 13 ??% ??% ??,?% 0 0 
Error while decoding frame!
A:   3.3 V:   3.5 A-V: -0.262 ct: -0.020  14/ 14  0%  0%  0.2% 0 0 
Error while decoding frame!
A:   3.3 V:   3.6 A-V: -0.258 ct: -0.024  15/ 15  0%  0%  0.2% 0 0 
Error while decoding frame!
A:   3.3 V:   3.6 A-V: -0.254 ct: -0.028  16/ 16  0%  0%  0.1% 0 0 
Error while decoding frame!
A:   3.4 V:   3.6 A-V: -0.250 ct: -0.032  17/ 17  0%  0%  0.1% 0 0 
Error while decoding frame!
A:   3.4 V:   3.7 A-V: -0.246 ct: -0.036  18/ 18  0%  0%  0.2% 0 0 
Error while decoding frame!
A:   3.5 V:   3.7 A-V: -0.242 ct: -0.040  19/ 19  0%  0%  0.1% 0 0 
Error while decoding frame!
.
.
.
MPlayer interrupted by signal 2 in module: sleep_timer
A:   9.2 V:   9.2 A-V:  0.004 ct: -0.238 155/155  0%  0%  0.2% 0 0 

Exiting... (Quit)


```

One line seems to show the reason for the issue:
**[vc1 @ 0x7fa23c1a54c0]Interlaced WVC1 support is not implemented**
But how can I solve this?
Please... someone has to have the same issue and some smart guy has to have a solution.

---

### Post by andrew.46 on 2012-01-09
Perhaps you can post the file VideoWVC1.wmv somewhere?

---

### Post by Senny04 on 2012-01-09
Someone posted a file which i am not able to play as well on the VLC forum cause he had the same problem:
_[Video Problems]("http://forum.videolan.org/viewtopic.php?f=2&t=89226&p=294076&hilit=wmv+vc1#p294076")_ You find the file to be downloaded from fileserve in the 10th reply of the topic. (I dont know what video that is as i cannot watch it!)
found those:
Easier and VERY small, this file gives the same Error:
[http://www.megaupload.com/?d=9H5BE78C]("http://www.megaupload.com/?d=9H5BE78C")
and this one as well:
[http://www.rhintl.ch/example.zip]("http://www.rhintl.ch/example.zip")

---

### Post by Senny04 on 2012-01-09
[http://www.megaupload.com/?d=9H5BE78C]("http://www.megaupload.com/?d=9H5BE78C") = t2 2009_06_11_23_02_36.wmv
```

user@ubuntu:~$ mplayer '/home/user/videos/t2 2009_06_11_23_02_36.wmv' 
MPlayer SVN-r33713-4.6.1 (C) 2000-2011 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/user/videos/t2 2009_06_11_23_02_36.wmv.
ASF file format detected.
[asfheader] Audio stream found, -aid 1
[asfheader] Video stream found, -vid 2
VIDEO:  [WVC1]  720x576  24bpp  1000.000 fps  4000.0 kbps (488.3 kbyte/s)
Clip info:
 title: t2
Load subtitles in /home/user/videos/
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: Permission denied.
[VO_3DFX] Unable to open /dev/3dfx.
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
[vdpau] Error when calling vdp_device_create_x11: 1
==========================================================================
Requested video codec family [wmvvc1dmo] (vfm=dmo) not available.
Enable it at compilation.
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Unsupported PixelFormat 61
Unsupported PixelFormat 53
Unsupported PixelFormat 61
Unsupported PixelFormat 53
Selected video codec: [ffvc1] vfm: ffmpeg (FFmpeg WVC1)
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16002->192000)
Selected audio codec: [ffwmav2] afm: ffmpeg (DivX audio v2 (FFmpeg))
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
[vc1 @ 0x7fe39afcc4c0]Interlaced WVC1 support is not implemented
Error while decoding frame!
Error while decoding frame!
Error while decoding frame!
Error while decoding frame!
Error while decoding frame!
Error while decoding frame!
Error while decoding frame!
Error while decoding frame!
Error while decoding frame!
A:   5.0 V:   5.3 A-V: -0.362 ct:  0.000   9/  9 ??% ??% ??,?% 0 0 
Error while decoding frame!
A:   5.0 V:   5.4 A-V: -0.362 ct: -0.004  10/ 10 ??% ??% ??,?% 0 0 
Error while decoding frame!
A:   5.0 V:   5.4 A-V: -0.358 ct: -0.008  11/ 11 ??% ??% ??,?% 0 0 
Error while decoding frame!
A:   5.1 V:   5.4 A-V: -0.355 ct: -0.012  12/ 12 ??% ??% ??,?% 0 0 
Error while decoding frame!
A:   5.1 V:   5.5 A-V: -0.351 ct: -0.016  13/ 13 ??% ??% ??,?% 0 0 
Error while decoding frame!
A:   5.2 V:   5.5 A-V: -0.347 ct: -0.020  14/ 14  0%  0%  0.1% 0 0 
Error while decoding frame!
A:   5.2 V:   5.6 A-V: -0.342 ct: -0.024  15/ 15  0%  0%  0.1% 0 0 
Error while decoding frame!
A:   5.3 V:   5.6 A-V: -0.338 ct: -0.028  16/ 16  0%  0%  0.1% 0 0 
Error while decoding frame!
A:   5.3 V:   5.6 A-V: -0.334 ct: -0.032  17/ 17  0%  0%  0.1% 0 0 
Error while decoding frame!
A:   5.3 V:   5.7 A-V: -0.331 ct: -0.036  18/ 18  0%  0%  0.1% 0 0 
Error while decoding frame!
A:   5.4 V:   5.7 A-V: -0.327 ct: -0.040  19/ 19  0%  0%  0.1% 0 0 
Error while decoding frame!
A:   5.4 V:   5.8 A-V: -0.323 ct: -0.044  20/ 20  0%  0%  0.1% 0 0 
Error while decoding frame!
A:   5.5 V:   5.8 A-V: -0.319 ct: -0.048  21/ 21  0%  0%  0.1% 0 0 
Error while decoding frame!
A:   5.5 V:   5.8 A-V: -0.315 ct: -0.052  22/ 22  0%  0%  0.1% 0 0 
Error while decoding frame!
A:   5.6 V:   5.9 A-V: -0.311 ct: -0.056  23/ 23  0%  0%  0.1% 0 0 
Error while decoding frame!
A:   5.6 V:   5.9 A-V: -0.307 ct: -0.060  24/ 24  0%  0%  0.1% 0 0 
Error while decoding frame!
A:   5.7 V:   6.0 A-V: -0.303 ct: -0.064  25/ 25  0%  0%  0.1% 0 0 
Error while decoding frame!
A:   5.7 V:   6.0 A-V: -0.299 ct: -0.068  26/ 26  0%  0%  0.1% 0 0 
Error while decoding frame!
A:   5.7 V:   6.0 A-V: -0.295 ct: -0.072  27/ 27  0%  0%  0.1% 0 0 
Error while decoding frame!
A:   5.8 V:   6.1 A-V: -0.291 ct: -0.076  28/ 28  0%  0%  0.1% 0 0 
Error while decoding frame!
A:   5.8 V:   6.1 A-V: -0.287 ct: -0.080  29/ 29  0%  0%  0.1% 0 0 
Error while decoding frame!
A:   5.9 V:   6.2 A-V: -0.283 ct: -0.084  30/ 30  0%  0%  0.1% 0 0 
Error while decoding frame!
A:   5.9 V:   6.2 A-V: -0.279 ct: -0.088  31/ 31  0%  0%  0.1% 0 0 
Error while decoding frame!
A:   6.0 V:   6.2 A-V: -0.275 ct: -0.092  32/ 32  0%  0%  0.1% 0 0 
Error while decoding frame!
A:   6.0 V:   6.3 A-V: -0.271 ct: -0.100  33/ 33  0%  0%  0.1% 0 0 


Exiting... (End of file)

```


[http://www.rhintl.ch/example.zip]("http://www.rhintl.ch/example.zip") = example.asf
```
user@ubuntu:~$ mplayer '/home/user/videos/example.asf' 
MPlayer SVN-r33713-4.6.1 (C) 2000-2011 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/stefan/Downloads/example.asf.
ASF file format detected.
[asfheader] Audio stream found, -aid 1
[asfheader] Video stream found, -vid 2
VIDEO:  [WVC1]  720x576  24bpp  1000.000 fps  4000.0 kbps (488.3 kbyte/s)
Clip info:
 title: LM8
Load subtitles in /home/user/videos/
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: Permission denied.
[VO_3DFX] Unable to open /dev/3dfx.
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
[vdpau] Error when calling vdp_device_create_x11: 1
[VO_XV] Could not grab port 143.
==========================================================================
Requested video codec family [wmvvc1dmo] (vfm=dmo) not available.
Enable it at compilation.
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Unsupported PixelFormat 61
Unsupported PixelFormat 53
Unsupported PixelFormat 61
Unsupported PixelFormat 53
Selected video codec: [ffvc1] vfm: ffmpeg (FFmpeg WVC1)
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16002->192000)
Selected audio codec: [ffwmav2] afm: ffmpeg (DivX audio v2 (FFmpeg))
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
[vc1 @ 0x7f14f5c494c0]Interlaced WVC1 support is not implemented
Error while decoding frame!
Error while decoding frame!
Error while decoding frame!
Error while decoding frame!
Error while decoding frame!
Error while decoding frame!
Error while decoding frame!
Error while decoding frame!
Error while decoding frame!
A:   5.1 V:   5.3 A-V: -0.186 ct:  0.000   9/  9 ??% ??% ??,?% 0 0 
Error while decoding frame!
A:   5.2 V:   5.4 A-V: -0.187 ct: -0.004  10/ 10 ??% ??% ??,?% 0 0 
Error while decoding frame!
A:   5.2 V:   5.4 A-V: -0.183 ct: -0.008  11/ 11 ??% ??% ??,?% 0 0 
Error while decoding frame!
A:   5.3 V:   5.4 A-V: -0.179 ct: -0.012  12/ 12 ??% ??% ??,?% 0 0 
Error while decoding frame!
A:   5.3 V:   5.5 A-V: -0.175 ct: -0.016  13/ 13 ??% ??% ??,?% 0 0 
Error while decoding frame!
A:   5.3 V:   5.5 A-V: -0.171 ct: -0.020  14/ 14  0%  0%  0.1% 0 0 
Error while decoding frame!
A:   5.4 V:   5.6 A-V: -0.167 ct: -0.024  15/ 15  0%  0%  0.1% 0 0 
Error while decoding frame!
A:   5.4 V:   5.6 A-V: -0.163 ct: -0.028  16/ 16  0%  0%  0.1% 0 0 
Error while decoding frame!
A:   5.5 V:   5.6 A-V: -0.159 ct: -0.032  17/ 17  0%  0%  0.1% 0 0 
Error while decoding frame!
A:   5.5 V:   5.7 A-V: -0.155 ct: -0.036  18/ 18  0%  0%  0.1% 0 0 
Error while decoding frame!
A:   5.6 V:   5.7 A-V: -0.151 ct: -0.040  19/ 19  0%  0%  0.1% 0 0 
Error while decoding frame!
A:   5.6 V:   5.8 A-V: -0.128 ct: -0.044  20/ 20  0%  0%  0.1% 0 0 
Error while decoding frame!
A:   5.7 V:   5.8 A-V: -0.124 ct: -0.048  21/ 21  0%  0%  0.1% 0 0 
Error while decoding frame!
A:   5.7 V:   5.8 A-V: -0.120 ct: -0.052  22/ 22  0%  0%  0.1% 0 0 
Error while decoding frame!
A:   5.8 V:   5.9 A-V: -0.116 ct: -0.056  23/ 23  0%  0%  0.1% 0 0 
Error while decoding frame!
A:   5.8 V:   5.9 A-V: -0.131 ct: -0.060  24/ 24  0%  0%  0.1% 0 0 
Error while decoding frame!
A:   5.8 V:   6.0 A-V: -0.127 ct: -0.064  25/ 25  0%  0%  0.1% 0 0 
Error while decoding frame!
A:   5.9 V:   6.0 A-V: -0.123 ct: -0.068  26/ 26  0%  0%  0.1% 0 0 
Error while decoding frame!
A:   5.9 V:   6.0 A-V: -0.119 ct: -0.072  27/ 27  0%  0%  0.1% 0 0 
Error while decoding frame!
A:   6.0 V:   6.1 A-V: -0.115 ct: -0.076  28/ 28  0%  0%  0.1% 0 0 
Error while decoding frame!
A:   6.0 V:   6.1 A-V: -0.114 ct: -0.080  29/ 29  0%  0%  0.1% 0 0 
Error while decoding frame!
A:   6.0 V:   6.2 A-V: -0.114 ct: -0.084  30/ 30  0%  0%  0.1% 0 0 
Error while decoding frame!
A:   6.1 V:   6.2 A-V: -0.114 ct: -0.088  31/ 31  0%  0%  0.1% 0 0 
Error while decoding frame!
A:   6.1 V:   6.2 A-V: -0.114 ct: -0.092  32/ 32  0%  0%  0.1% 0 0 
Error while decoding frame!
A:   6.2 V:   6.3 A-V: -0.114 ct: -0.096  33/ 33  0%  0%  0.1% 0 0 
Error while decoding frame!
A:   6.2 V:   6.3 A-V: -0.119 ct: -0.100  34/ 34  0%  0%  0.1% 0 0 
Error while decoding frame!
A:   6.2 V:   6.4 A-V: -0.159 ct: -0.104  35/ 35  0%  0%  0.1% 0 0 
Error while decoding frame!
A:   6.2 V:   6.4 A-V: -0.199 ct: -0.108  36/ 36  0%  0%  0.1% 0 0 
Error while decoding frame!
A:   6.2 V:   6.4 A-V: -0.239 ct: -0.116  37/ 37  0%  0%  0.1% 0 0 


Exiting... (End of file)

```

---

### Post by andrew.46 on 2012-01-10
Thanks for taking the trouble to post those files. As the vlc thread pointed out you will need windows codecs to play these files:

```

andrew@skamandros~$ **[COLOR="Red"]mplayer -xy 420 example.asf[/COLOR]** 
MPlayer SVN-r34526-4.6.2 (C) 2000-2012 MPlayer Team

Playing example.asf.
libavformat version 53.29.100 (internal)
ASF file format detected.
[asfheader] Audio stream found, -aid 1
[asfheader] Video stream found, -vid 2
VIDEO:  [WVC1]  720x576  24bpp  1000.000 fps  4000.0 kbps (488.3 kbyte/s)
Clip info:
 title: LM8
Load subtitles in ./
==========================================================================
Opening video decoder: [dmo] DMO video codecs
DMO dll supports VO Optimizations 0 1
DMO dll might use previous sample when requested
Decoder supports the following formats: YV12 YUY2 UYVY YVYU RGB8 RGB555 RGB565 RGB24 RGB32 
Decoder is capable of YUV output (flags 0x1b)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 720x576 => 420x336 Planar YV12 
**[COLOR="Red"]Selected video codec: [wmvvc1dmo] vfm: dmo (Windows Media Video (VC-1) Advanced Profile)[/COLOR]**
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
libavcodec version 53.54.100 (internal)
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16002->192000)
Selected audio codec: [ffwmav2] afm: ffmpeg (DivX audio v2 (FFmpeg))
==========================================================================
AO: [oss] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
A:   6.3 V:   6.4 A-V: -0.155 ct:  0.105  37/ 37 22%  2%  0.5% 0 0 


Exiting... (End of file)

```

and for this I am afraid you will need the so-called win32 codecs and a 32bit installation of MPlayer :(.

---

### Post by Senny04 on 2012-01-10
Well... thanks for the info... so... how do i do this?
i can download the w32codecs just not "install" 
but i can extract and copy them anywhere i want?
Just ... how to get/use 32bit mplayer? i am a bit clueless for that...
There seems to be something weird with the codec packs at all:
[http://packages.medibuntu.org/oneiric/w64codecs.html](http://packages.medibuntu.org/oneiric/w64codecs.html)
w64 codecs are 210kb but [w32codecs]("http://packages.medibuntu.org/oneiric/w32codecs.html") are 26mb?  
also no issue to get the 32bit version of MPlayer... but how do i install/run it on my 64bit oneiric system?

---

### Post by andrew.46 on 2012-01-10
Unfortunately the 64bit codecs are essentially useless :(. It is *possible* to compile a 32bit MPlayer on a 64bit environment but I am afraid I have only ever looked briefly at this and would not be the best person to advise you. Hopefully someone else in this thread can assist?

---

