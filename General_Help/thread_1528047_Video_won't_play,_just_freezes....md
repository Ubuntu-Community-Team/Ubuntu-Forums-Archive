---
title: "Video won't play, just freezes..."
date: 2010-07-10
forum: General Help
---

### Post by inameiname on 2010-07-10
For some reason an update in the past month or two has caused the following issue to occur, and only on one of my computers, which use the exact same custom DVD:

When I try and play any and all video, whether it's a video DVD, avi, mpeg4, or whatever, in Totem Movie Player, Mplayer, Smplayer, and Gnome-Mplayer it doesn't play. All it does is open as if it was starting, but the time never progresses past 0:00. And when I move the progress thingy to any point on the film, still nothing. It does movie the image to a paused part of the video just fine, but won't play. It jumps for have a second like it's trying to play and progress, but just stays frozen. 

Anybody have any idea?

One potential solution I tried was installing VLC player just to see if it will also fail, and lo and behold, it opens and plays it all just fine. However, there is no sound. 

So while there is no sound, it seems work. Not sure why it works yet all the others don't. 

Oh, and it seems the no sound has occurred for all regardless of player or video. Not sure why that happened, as everybody's hooked up just fine, as before, just nothing. 

Anybody?

---

### Post by ankspo71 on 2010-07-10
Hi,
I'm not sure which update could have caused this problem, but try checking to see if your codecs are still installed. You might even want to try reinstalling them to see if it helps. Sometimes when we install new or update existing packages, some other installed packages need to get removed in the process, due to incompatabilty reasons.

Also, try running your video players by launching them from the terminal to see if they produce any errors. Sometimes this will report missing or broken codecs.
Hope this helps.

---

### Post by inameiname on 2010-07-10
What codecs should I remove and then reinstall? Would any of these be them?: libdvdread4 libdvdcss2 w32codecs non-free-codecs 

What's weird though is if that is the case, why would it have no effect on the other computer, but does on the one I'm having the problem with?

And as for opening the apps in the terminal, good idea. I forgot about trying that, thanks.

---

### Post by ankspo71 on 2010-07-10
Hi,
Yes those are all codec & audio-video related packages. It looks to me that most of those are from medibuntu. Do you have ubuntu-restricted-extras installed too? This package includes things like java, adobe flash, several codecs for audio and video, extra fonts, etc. 

To reinstall any of these, you can go into Synaptic Package Manager and right click on each of those packages and select "mark for reinstallation", then click apply. I don't think it would be necessary to remove them first, but that possibly might help too. 
Hope this helps.

---

### Post by inameiname on 2010-07-11
Yes, I have ubuntu-restricted-extras installed. 

How would I reinstall through the terminal? I usually just remove then install again if and when need be through it. Never use synaptic package manager. I'm a terminal dieharder I guess. :P

---

### Post by ankspo71 on 2010-07-11
Hi,

Before installing or reinstalling any packages, it is a good idea to reload the package repository cache first so newer versions of programs can be installed:
```
sudo apt-get update
```

Here is a command to reinstall ubuntu-restricted-extras:
```
sudo apt-get install --reinstall ubuntu-restricted-extras
```

For more detailed information on apt-get you can type "man apt-get" in the terminal. Or you could visit a link like this: [http://www.ubuntugeek.com/ubuntu-package-management-from-command-line-using-apt-advanced-packaging-tool.html#more-1062](http://www.ubuntugeek.com/ubuntu-package-management-from-command-line-using-apt-advanced-packaging-tool.html#more-1062)

I'm not sure what else the problem could be... does anyone have other advice for the original poster?

---

### Post by inameiname on 2010-07-12
Yeah, I always do that before I install anything.

Thanks. I just couldn't remember the "install --reinstall" part.

---

### Post by inameiname on 2010-09-17
Bump....


I still haven't found a solution for this issue. It sucks as this computer is the one I have attached to my tv-out so I can watch streaming stuff from online on the bigger screen. However, due to this problem, I haven't been able to do that in a couple months now.

---

### Post by inameiname on 2010-09-17
Bump.

---

### Post by inameiname on 2010-09-18
Also, running it through the terminal, no errors are shown or given, so  that sadly didn't help to narrow down just what the issue is. I just  don't get why it's only on this one computer, to which uses the exact  same Remastersys custom dvd image as two others, including the one I  always use. Thus, it's definitely a hardware thing. Although, I don't  understand why it worked just fine until an update a few months back. So  it's obviously some sort of update that now no longer works well with  the hardware inside. Maybe when Maverick comes out it'll work.

---

### Post by FahadMKS on 2010-09-18
I also have the same issue.
Some of the CD's is not playing with the Ubuntu.

But the same CD's plays with the VLC in windows.

What exactly is the same cause of this.

---

### Post by inameiname on 2010-09-19
Strange. So just some of your cds (do you also mean dvds?) don't work? Sadly, all video, from discs to avi files, and various other types just won't play. I just don't get it. And as mentioned, if I use VLC, it doesn't have sound.

---

### Post by inameiname on 2010-09-21
Bump

---

### Post by no2498 on 2010-09-21
write down your setting just in case you would like to set them back and try this
5.1 should help you 5.2 is for mac users

5.1.&#8195;The video is sluggish/has a slow response. What can I do?


      You may have set "ximagesink" ("X Window System (No Xv)") as video-output.
      This means, that your cpu is doing all the work. Change it to "xvimagesink"
      ("X Window System (X11/XShm/Xv)") in order to let your graphics card do the work.
    


      To change the settings, run "gstreamer-properties", click the Video tab
      and change the appropriate settings.
    
5.2.&#8195;I have a Mac with iSight and a ATI graphics card, and the colors are weird.


      This is a problem with the ATI graphics card, though there is a work around.
      Change the video-output to custom and insert the following: "ffmpegcolorspace !
      video/x-raw-yuv,format=(fourcc)YV12 ! ffmpegcolorspace ! xvimagesink".
    


      To change the settings, run "gstreamer-properties", click the Video tab
      and select custom from the drop down menu.

---

### Post by no2498 on 2010-09-21
write down your setting just in case you would like to set them back and try this
5.1 should help you 5.2 is for mac users

5.1.&#8195;The video is sluggish/has a slow response. What can I do?


      You may have set "ximagesink" ("X Window System (No Xv)") as video-output.
      This means, that your cpu is doing all the work. Change it to "xvimagesink"
      ("X Window System (X11/XShm/Xv)") in order to let your graphics card do the work.
    


      To change the settings, run "gstreamer-properties", click the Video tab
      and change the appropriate settings.
    
5.2.&#8195;I have a Mac with iSight and a ATI graphics card, and the colors are weird.


      This is a problem with the ATI graphics card, though there is a work around.
      Change the video-output to custom and insert the following: "ffmpegcolorspace !
      video/x-raw-yuv,format=(fourcc)YV12 ! ffmpegcolorspace ! xvimagesink".
    


      To change the settings, run "gstreamer-properties", click the Video tab
      and select custom from the drop down menu.

---

### Post by inameiname on 2010-09-22
Thanks for the suggestion...

It's not really that my video is sluggish, but that it is frozen entirely. There is no movement of picture at all.

Anyway, it's an interesting theory. Would this be the reason why (using the same exact Custom Remastersys DVD) my main laptop works just fine, which is a core duo and thus, fast cpu power, while the old desktop that isn't running the video fails with the video....because it's crappy celeron ancient thing that can't handle things?

So I'll look into "gstreamer-properties". 
    
And I'm guessing that since I am not using a Mac, the "Change the video-output to custom and insert the following: "ffmpegcolorspace !
      video/x-raw-yuv,format=(fourcc)YV12 ! ffmpegcolorspace ! xvimagesink"." doesn't apply?

---

### Post by inameiname on 2010-09-22
When I open "gstreamer-properties", it shows it's set on 'Autodetect' as the Default Output, with the pipeline being 'autovideosink'. Is that where it should be set automatically? Why would it not be correct, or have changed with some update?

Anyway, so if I change it to "xvimagesink" ("X Window System (X11/XShm/Xv)"), it should work just fine? Does 'Autodetect' automatically keep it set on "ximagesink" ("X Window System (No Xv)") as video-output. If this often brings issues, why is that?

Also, is "xvimagesink" ("X Window System (X11/XShm/Xv)" mean it only works with the graphics card, or that it uses both the graphics card and the cpu to handle videos and multimedia?

I'll get back with you and let you know if this solves my issue.

Oh, and if it does work, would it be okay to leave it set to "xvimagesink" ("X Window System (X11/XShm/Xv)") on both machines, the laptop (which just as a basic integrated graphics card that works just fine currently) and the desktop, that is the one having the video woes? Would this setting mess up with the laptop's performance? Just curious.

---

### Post by inameiname on 2010-09-22
Nevermind. Sadly, it didn't work or help. I tried changing the settings over and over and even restarting the computer, but nothing worked. :(

It's just so strange, as the issue isn't it being slow or sluggish, or really any hardware issues at all (especially as it worked just fine prior to some updates a few months back), but that it just won't play. 

Why won't it play anything? It just lays frozen on whatever frame that is currently 'playing'. And moving to another place on the video just moves the image to another frame. It jumps a fraction of a second, or a frame or two, but then it continues to stay frozen.

I just don't get why in the world it'd do this. And it's not an issue with my Ubuntu OS, as I've redone the computer a couple of times, from scratch with a fresh install, and this issue still persists.

---

### Post by SeijiSensei on 2010-09-22
You might try playing a problematic file with mplayer from the command line and see what it reports.  Open a Terminal and type "mplayer moviefilename".  Often the error is fairly obvious.  If you can't tell what's wrong, you can enable verbose error reporting by using "mplayer -v moviefilename" but I'll warn you there's a *lot* of output.

If the problem isn't obvious, post the results of the first test (without -v), and maybe one of us will see it.

---

### Post by inameiname on 2010-09-23
Here is the readout in the terminal using 'mplayer moviename':

```

mplayer test.avi
MPlayer 1.0rc4-4.4.3 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing test.avi.
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [XVID]  624x352  12bpp  23.976 fps  851.3 kbps (103.9 kbyte/s)
Clip info:
 Software: Nandub v1.0rc2
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: Permission denied.
[VO_3DFX] Unable to open /dev/3dfx.
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
[vdpau] Error when calling vdp_device_create_x11: 1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
Movie-Aspect is 1.77:1 - prescaling to correct movie aspect.
VO: [xv] 624x352 => 624x352 Planar YV12 
A:   0.6 V:   0.7 A-V: -0.102 ct: -0.041  17/ 17 34% 26%  2.2% 6 0 
Exiting... (Quit)

```Here is the readout in the terminal using 'mplayer -v moviename':

```

mplayer -v test.avi
MPlayer 1.0rc4-4.4.3 (C) 2000-2010 MPlayer Team
CPU vendor name: GenuineIntel  max cpuid level: 2
CPU: Intel(R) Celeron(R) CPU 2.00GHz (Family: 15, Model: 2, Stepping: 7)
extended cpuid-level: 4
Detected cache-line size is 64 bytes
Testing OS support for SSE... yes.
Tests of OS support for SSE passed.
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNowExt: 0 SSE: 1 SSE2: 1 SSSE3: 0
Compiled with runtime CPU detection.
get_path('codecs.conf') -> '/home/me/.mplayer/codecs.conf'
Reading /home/me/.mplayer/codecs.conf: Can't open '/home/me/.mplayer/codecs.conf': No such file or directory
Reading /etc/mplayer/codecs.conf: Can't open '/etc/mplayer/codecs.conf': No such file or directory
Using built-in default codecs.conf.
Configuration: --prefix=/usr --confdir=/etc/mplayer --enable-xvmc --enable-menu --disable-arts --enable-largefiles --language=all --disable-libdvdcss-internal --disable-dvdread-internal --disable-libavutil_a --disable-libavcodec_a --disable-libavformat_a --disable-libpostproc_a --disable-libswscale_a --target=i586-linux --enable-runtime-cpudetection --enable-debug --enable-mga --enable-3dfx --enable-tdfxfb --disable-gui
CommandLine: '-v' 'test.avi'
init_freetype
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
get_path('fonts') -> '/home/me/.mplayer/fonts'
Using nanosleep() timing
get_path('input.conf') -> '/home/me/.mplayer/input.conf'
Can't open input config file /home/me/.mplayer/input.conf: No such file or directory
Parsing input config file /etc/mplayer/input.conf
Input config file /etc/mplayer/input.conf parsed: 91 binds
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
get_path('test.avi.conf') -> '/home/me/.mplayer/test.avi.conf'

Playing test.avi.
get_path('sub/') -> '/home/me/.mplayer/sub/'
[file] File size is 734179328 bytes
STREAM: [file] test.avi
STREAM: Description: File
STREAM: Author: Albeu
STREAM: Comment: based on the code from ??? (probably Arpi)
LAVF_check: AVI format
AVI file format detected.
list_end=0x2292
======= AVI Header =======
us/frame: 41708  (fps=23.976)
max bytes/sec: 0
padding: 0
MainAVIHeader.dwFlags: (272) HAS_INDEX IS_INTERLEAVED
frames  total: 141969   initial: 0
streams: 2
Suggested BufferSize: 0
Size:  624 x 352
==========================
list_end=0x10F4
==> Found video stream: 0
[aviheader] Video stream found, -vid 0
====== STREAM Header =====
Type: vids   FCC: xvid (64697678)
Flags: 0
Priority: 0   Language: 0
InitialFrames: 0
Rate: 2997/125 = 23.976
Start: 0   Len: 141969
Suggested BufferSize: 85604
Quality 10000
Sample size: 0
==========================
Found 'bih', 40 bytes of 40
======= VIDEO Format ======
  biSize 40
  biWidth 624
  biHeight 352
  biPlanes 1
  biBitCount 12
  biCompression 1145656920='XVID'
  biSizeImage 1317888
===========================
Regenerating keyframe table for MPEG-4 video.
list_end=0x2186
==> Found audio stream: 1
[aviheader] Audio stream found, -aid 1
====== STREAM Header =====
Type: auds   FCC:  (0)
Flags: 0
Priority: 0   Language: 0
InitialFrames: 0
Rate: 48000/1152 = 41.667
Start: 0   Len: 246659
Suggested BufferSize: 960
Quality -1
Sample size: 0
==========================
Found 'wf', 30 bytes of 18
======= WAVE Format =======
Format Tag: 85 (0x55)
Channels: 2
Samplerate: 48000
avg byte/sec: 15991
Block align: 1152
bits/sample: 0
cbSize: 12
mp3.wID=1
mp3.fdwFlags=0x2
mp3.nBlockSize=383
mp3.nFramesPerBlock=1
mp3.nCodecDelay=0
==========================================================================
list_end=0x2292
AVI: dmlh found (size=248) (total_frames=141969)
list_end=0x22B6
hdr=Software  size=15
Software  : Nandub v1.0rc2
list_end=0x2B63CABA
Found movie at 0x280C - 0x2B63CABA
Reading INDEX block, 388628 chunks for 141969 frames (fpos=727960258).
AVI index offset: 0x2808 (movi=0x280C idx0=0x4 idx1=0x978)
Auto-selected AVI video ID = 0
Auto-selected AVI audio ID = 1
AVI: Searching for audio stream (id:1)
XXX initial  v_pts=0.000  a_pos=0 (0.000) 
AVI video size=630103388 (141969) audio size=94666464 (246659)
VIDEO:  [XVID]  624x352  12bpp  23.976 fps  851.3 kbps (103.9 kbyte/s)
Auto-selected AVI audio ID = 1
[V] filefmt:3  fourcc:0x44495658  size:624x352  fps:23.976  ftime:=0.0417
Clip info:
 Software: Nandub v1.0rc2
get_path('sub/') -> '/home/me/.mplayer/sub/'
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: Permission denied.
[VO_3DFX] Unable to open /dev/3dfx.
X11 opening display: :0.0
vo: X11 color mask:  FFFFFF  (R:FF0000 G:FF00 B:FF)
vo: X11 running at 1024x768 with depth 24 and 32 bpp (":0.0" => local display)
[x11] Detected wm supports NetWM.
[x11] Detected wm supports FULLSCREEN state.
[x11] Detected wm supports ABOVE state.
[x11] Detected wm supports BELOW state.
[x11] Current fstype setting honours FULLSCREEN ABOVE BELOW X atoms
Disabling DPMS
DPMSDisable stat: 1
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
[vdpau] Error when calling vdp_device_create_x11: 1
[VO_XV] Using Xv Adapter #0 (Radeon Textured Video)
[xv common] Drawing no colorkey.
[xv common] Maximum source image dimensions: 2048x2048
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
INFO: libavcodec init OK!
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
dec_audio: Allocating 4608 + 65536 = 70144 bytes for output buffer.
mp3lib: using SSE optimized decore!
MP3lib: init layer2&3 finished, tables done
MPEG 1.0, Layer III, 48000 Hz 128 kbit Joint-Stereo, BPF: 384
Channels: 2, copyright: No, original: Yes, CRC: Yes, emphasis: 0
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
Building audio filter chain for 48000Hz/2ch/s16le -> 0Hz/0ch/??...
[libaf] Adding filter dummy 
[dummy] Was reinitialized: 48000Hz/2ch/s16le
[dummy] Was reinitialized: 48000Hz/2ch/s16le
Trying preferred audio driver 'pulse', options '[none]'
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
AO: Description: PulseAudio audio output
AO: Author: Lennart Poettering
Building audio filter chain for 48000Hz/2ch/s16le -> 48000Hz/2ch/s16le...
[dummy] Was reinitialized: 48000Hz/2ch/s16le
[dummy] Was reinitialized: 48000Hz/2ch/s16le
Starting playback...
Increasing filtered audio buffer size from 0 to 50048
[ffmpeg] aspect_ratio: 1.772727
VDec: vo config request - 624 x 352 (preferred colorspace: Planar YV12)
Trying filter chain: vo
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.77:1 - prescaling to correct movie aspect.
VO Config (624x352->624x352,flags=0,'MPlayer',0x32315659)
VO: [xv] 624x352 => 624x352 Planar YV12 
VO: Description: X11/Xv
VO: Author: Gerd Knorr <kraxel@goldbach.in-berlin.de> and others
Xvideo image format: 0x32595559 (YUY2) packed
Xvideo image format: 0x32315659 (YV12) planar
Xvideo image format: 0x30323449 (I420) planar
Xvideo image format: 0x59565955 (UYVY) packed
using Xvideo port 63 for hw scaling
*** [vo] Allocating (slices) mp_image_t, 624x352x12bpp YUV planar, 329472 bytes
*** [vo] Allocating (slices) mp_image_t, 624x352x12bpp YUV planar, 329472 bytes
Unicode font: 5025 glyphs.
Unicode font: 5025 glyphs.
*** [vo] Allocating (slices) mp_image_t, 624x352x12bpp YUV planar, 329472 bytes
Uninit audio filters...-0.088 ct: -0.042  18/ 18 44% 18%  0.8% 4 0 
[libaf] Removing filter dummy 
Uninit audio: mp3lib
Uninit video: ffmpeg
Successfully enabled DPMS
vo: uninit ...

Exiting... (Quit)

```

---

### Post by inameiname on 2010-09-23
Curious, I tried the very same commands and video on my laptop, which uses the exact same custom Remastersys dvd, and DOES work, and here is the readout of those two commands on it:

        Here is the readout in the terminal using 'mplayer moviename' on my laptop that WORKS:

```

mplayer test.avi
MPlayer 1.0rc4-4.4.3 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing test.avi.
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [XVID]  624x352  12bpp  23.976 fps  851.3 kbps (103.9 kbyte/s)
Clip info:
 Software: Nandub v1.0rc2
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: Permission denied.
[VO_3DFX] Unable to open /dev/3dfx.
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
[vdpau] Error when calling vdp_device_create_x11: 1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
Movie-Aspect is 1.77:1 - prescaling to correct movie aspect.
VO: [xv] 624x352 => 624x352 Planar YV12 
A:   2.5 V:   2.5 A-V:  0.004 ct: -0.062  60/ 60  4%  0%  0.5% 0 0 
Exiting... (Quit)

```Here is the readout in the terminal using 'mplayer -v moviename' on my laptop, that WORKS:

```

mplayer -v test.avi
MPlayer 1.0rc4-4.4.3 (C) 2000-2010 MPlayer Team
CPU vendor name: GenuineIntel  max cpuid level: 10
CPU: Intel(R) Core(TM)2 Duo CPU     T5250  @ 1.50GHz (Family: 6, Model: 15, Stepping: 13)
extended cpuid-level: 8
extended cache-info: 134242368
Detected cache-line size is 64 bytes
Testing OS support for SSE... yes.
Tests of OS support for SSE passed.
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNowExt: 0 SSE: 1 SSE2: 1 SSSE3: 1
Compiled with runtime CPU detection.
get_path('codecs.conf') -> '/home/me/.mplayer/codecs.conf'
Reading /home/me/.mplayer/codecs.conf: Can't open '/home/me/.mplayer/codecs.conf': No such file or directory
Reading /etc/mplayer/codecs.conf: Can't open '/etc/mplayer/codecs.conf': No such file or directory
Using built-in default codecs.conf.
Configuration: --prefix=/usr --confdir=/etc/mplayer --enable-xvmc --enable-menu --disable-arts --enable-largefiles --language=all --disable-libdvdcss-internal --disable-dvdread-internal --disable-libavutil_a --disable-libavcodec_a --disable-libavformat_a --disable-libpostproc_a --disable-libswscale_a --target=i586-linux --enable-runtime-cpudetection --enable-debug --enable-mga --enable-3dfx --enable-tdfxfb --disable-gui
CommandLine: '-v' 'test.avi'
init_freetype
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
get_path('fonts') -> '/home/me/.mplayer/fonts'
Using nanosleep() timing
get_path('input.conf') -> '/home/me/.mplayer/input.conf'
Can't open input config file /home/me/.mplayer/input.conf: No such file or directory
Parsing input config file /etc/mplayer/input.conf
Input config file /etc/mplayer/input.conf parsed: 91 binds
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
get_path('test.avi.conf') -> '/home/me/.mplayer/test.avi.conf'

Playing test.avi.
get_path('sub/') -> '/home/me/.mplayer/sub/'
[file] File size is 734179328 bytes
STREAM: [file] test.avi
STREAM: Description: File
STREAM: Author: Albeu
STREAM: Comment: based on the code from ??? (probably Arpi)
LAVF_check: AVI format
AVI file format detected.
list_end=0x2292
======= AVI Header =======
us/frame: 41708  (fps=23.976)
max bytes/sec: 0
padding: 0
MainAVIHeader.dwFlags: (272) HAS_INDEX IS_INTERLEAVED
frames  total: 141969   initial: 0
streams: 2
Suggested BufferSize: 0
Size:  624 x 352
==========================
list_end=0x10F4
==> Found video stream: 0
[aviheader] Video stream found, -vid 0
====== STREAM Header =====
Type: vids   FCC: xvid (64697678)
Flags: 0
Priority: 0   Language: 0
InitialFrames: 0
Rate: 2997/125 = 23.976
Start: 0   Len: 141969
Suggested BufferSize: 85604
Quality 10000
Sample size: 0
==========================
Found 'bih', 40 bytes of 40
======= VIDEO Format ======
  biSize 40
  biWidth 624
  biHeight 352
  biPlanes 1
  biBitCount 12
  biCompression 1145656920='XVID'
  biSizeImage 1317888
===========================
Regenerating keyframe table for MPEG-4 video.
list_end=0x2186
==> Found audio stream: 1
[aviheader] Audio stream found, -aid 1
====== STREAM Header =====
Type: auds   FCC:  (0)
Flags: 0
Priority: 0   Language: 0
InitialFrames: 0
Rate: 48000/1152 = 41.667
Start: 0   Len: 246659
Suggested BufferSize: 960
Quality -1
Sample size: 0
==========================
Found 'wf', 30 bytes of 18
======= WAVE Format =======
Format Tag: 85 (0x55)
Channels: 2
Samplerate: 48000
avg byte/sec: 15991
Block align: 1152
bits/sample: 0
cbSize: 12
mp3.wID=1
mp3.fdwFlags=0x2
mp3.nBlockSize=383
mp3.nFramesPerBlock=1
mp3.nCodecDelay=0
==========================================================================
list_end=0x2292
AVI: dmlh found (size=248) (total_frames=141969)
list_end=0x22B6
hdr=Software  size=15
Software  : Nandub v1.0rc2
list_end=0x2B63CABA
Found movie at 0x280C - 0x2B63CABA
Reading INDEX block, 388628 chunks for 141969 frames (fpos=727960258).
AVI index offset: 0x2808 (movi=0x280C idx0=0x4 idx1=0x978)
Auto-selected AVI video ID = 0
Auto-selected AVI audio ID = 1
AVI: Searching for audio stream (id:1)
XXX initial  v_pts=0.000  a_pos=0 (0.000) 
AVI video size=630103388 (141969) audio size=94666464 (246659)
VIDEO:  [XVID]  624x352  12bpp  23.976 fps  851.3 kbps (103.9 kbyte/s)
Auto-selected AVI audio ID = 1
[V] filefmt:3  fourcc:0x44495658  size:624x352  fps:23.976  ftime:=0.0417
Clip info:
 Software: Nandub v1.0rc2
get_path('sub/') -> '/home/me/.mplayer/sub/'
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: Permission denied.
[VO_3DFX] Unable to open /dev/3dfx.
X11 opening display: :0.0
vo: X11 color mask:  FFFFFF  (R:FF0000 G:FF00 B:FF)
vo: X11 running at 1280x800 with depth 24 and 32 bpp (":0.0" => local display)
[x11] Detected wm supports NetWM.
[x11] Detected wm supports FULLSCREEN state.
[x11] Detected wm supports ABOVE state.
[x11] Detected wm supports BELOW state.
[x11] Current fstype setting honours FULLSCREEN ABOVE BELOW X atoms
Disabling DPMS
DPMSDisable stat: 1
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
[vdpau] Error when calling vdp_device_create_x11: 1
[VO_XV] Using Xv Adapter #0 (Intel(R) Textured Video)
[xv common] Drawing no colorkey.
[xv common] Maximum source image dimensions: 2048x2048
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
INFO: libavcodec init OK!
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
dec_audio: Allocating 4608 + 65536 = 70144 bytes for output buffer.
mp3lib: using SSE optimized decore!
MP3lib: init layer2&3 finished, tables done
MPEG 1.0, Layer III, 48000 Hz 128 kbit Joint-Stereo, BPF: 384
Channels: 2, copyright: No, original: Yes, CRC: Yes, emphasis: 0
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
Building audio filter chain for 48000Hz/2ch/s16le -> 0Hz/0ch/??...
[libaf] Adding filter dummy 
[dummy] Was reinitialized: 48000Hz/2ch/s16le
[dummy] Was reinitialized: 48000Hz/2ch/s16le
Trying preferred audio driver 'pulse', options '[none]'
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
AO: Description: PulseAudio audio output
AO: Author: Lennart Poettering
Building audio filter chain for 48000Hz/2ch/s16le -> 48000Hz/2ch/s16le...
[dummy] Was reinitialized: 48000Hz/2ch/s16le
[dummy] Was reinitialized: 48000Hz/2ch/s16le
Starting playback...
Increasing filtered audio buffer size from 0 to 50048
[ffmpeg] aspect_ratio: 1.772727
VDec: vo config request - 624 x 352 (preferred colorspace: Planar YV12)
Trying filter chain: vo
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.77:1 - prescaling to correct movie aspect.
VO Config (624x352->624x352,flags=0,'MPlayer',0x32315659)
VO: [xv] 624x352 => 624x352 Planar YV12 
VO: Description: X11/Xv
VO: Author: Gerd Knorr <kraxel@goldbach.in-berlin.de> and others
Xvideo image format: 0x32595559 (YUY2) packed
Xvideo image format: 0x32315659 (YV12) planar
Xvideo image format: 0x30323449 (I420) planar
Xvideo image format: 0x59565955 (UYVY) packed
Xvideo image format: 0x434d5658 (XVMC) planar
using Xvideo port 72 for hw scaling
*** [vo] Allocating (slices) mp_image_t, 624x352x12bpp YUV planar, 329472 bytes
*** [vo] Allocating (slices) mp_image_t, 624x352x12bpp YUV planar, 329472 bytes
Unicode font: 5025 glyphs.
Unicode font: 5025 glyphs.
*** [vo] Allocating (slices) mp_image_t, 624x352x12bpp YUV planar, 329472 bytes
Uninit audio filters...-0.004 ct: -0.060  77/ 77  4%  0%  0.5% 0 0 
[libaf] Removing filter dummy 
Uninit audio: mp3lib
Uninit video: ffmpeg
Successfully enabled DPMS
vo: uninit ...

Exiting... (Quit)

```

---

### Post by inameiname on 2010-09-23
As noticed in the readout of 'mplayer test.avi' for both my laptop and  my desktop, both are EXACTLY the same, minus this one line, which I  don't think matters:

A:   0.6 V:   0.7 A-V: -0.102 ct: -0.041  17/ 17 34% 26%  2.2% 6 0 
...and...
A:   2.5 V:   2.5 A-V:  0.004 ct: -0.062  60/ 60  4%  0%  0.5% 0 0

And as noticed in the readout of 'mplayer -v test.avi' for both my laptop and  my desktop, both are EXACTLY the same, minus this:

CPU vendor name: GenuineIntel  max cpuid level: 2
CPU: Intel(R) Celeron(R) CPU 2.00GHz (Family: 15, Model: 2, Stepping: 7)
extended cpuid-level: 4
...and...
CPU vendor name: GenuineIntel  max cpuid level: 10
CPU: Intel(R) Core(TM)2 Duo CPU     T5250  @ 1.50GHz (Family: 6, Model: 15, Stepping: 13)
extended cpuid-level: 8
extended cache-info: 134242368

...AND...

vo: X11 running at 1024x768 with depth 24 and 32 bpp (":0.0" => local display)
...and...
vo: X11 running at 1280x800 with depth 24 and 32 bpp (":0.0" => local display)

...AND...

[VO_XV] Using Xv Adapter #0 (Radeon Textured Video)
...and...
[VO_XV] Using Xv Adapter #0 (Intel(R) Textured Video)

...AND...

Xvideo image format: 0x59565955 (UYVY) packed
using Xvideo port 63 for hw scaling
...and...
Xvideo image format: 0x59565955 (UYVY) packed
Xvideo image format: 0x434d5658 (XVMC) planar
using Xvideo port 72 for hw scaling

...AND...

Uninit audio filters...-0.088 ct: -0.042  18/ 18 44% 18%  0.8% 4 0 
...and...
Uninit audio filters...-0.004 ct: -0.060  77/ 77  4%  0%  0.5% 0 0 

Based on this, I don't think any of the differences show why it works on my laptop, but not on my desktop. At least from my perspective. Maybe somebody else might see it differently.

---

### Post by inameiname on 2010-09-24
Bump.

---

### Post by melalcoolique on 2010-09-27
Try to kill processus *npviewer.bin* related to flash. Since the last security fix under maverick, i was unable to play movies with totem and vlc played sound no more.

Hope this helps.

---

### Post by inameiname on 2010-09-28
Ok, I'll try that. Though, I'm using Lucid, so hopefully it's not just a Maverick issue.

---

### Post by inameiname on 2010-10-03
Okay, so I tried to kill the process, *npviewer.bin*, however, it is nowhere to be found. It wasn't there in gnome-system-monitor in Lucid. So guess that's not the issue.

One odd thing noticed is that when supposedly 'playing' something in Totem, the 'totem' process is sleeping. Though this issue occurs with mplayer and it's frontends too so I know that isn't the issue.

---

### Post by inameiname on 2010-10-04
bump

---

### Post by inameiname on 2010-10-12
Sadly I can confirm that this issue STILL DOESNT WORK under Maverick. :(

So I guess, I'll bump again.

---

### Post by inameiname on 2010-10-21
I recently learned that it isn't just this one computer that has this issue. I've learned another desktop I have has the same trouble, that the video simply won't move forward, backward, or anything, and sits there frozen, no matter the type.

FYI, both of the victims are using Maverick, although the issue was first evident on Lucid.

Due to it not being just one computer, I'm surprised nobody else is having this issue.

---

### Post by inameiname on 2011-06-18
I know this is an old issue I was having, but figured I should update this thread. 

The issue was caused by an update somewhere along the lines. I do not know which one, or why, but it was something. Regardless, another update fixed the problem.

And so far so good in Natty, so I'll just mark this as solved. Just shows it can be a good, or bad, thing to update. Hehe

---

