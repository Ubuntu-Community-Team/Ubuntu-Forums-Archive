---
title: "Help PLZ! I'm unable to watch videos on MPlayer :("
date: 2010-05-19
forum: General Help
---

### Post by __ShaM__ on 2010-05-19
Hi There!

I Recently moved to Ubuntu 10.04 LTS and i lyk its one thing only and thats it's Apple Obsessed THEME :D!

I'm having problem with MPlayer, I Have updated this from Belgian Repositories but it play files with blank screen. but audio is ok :), what should i do? Help me plz!

Regards
        ShaM

---

### Post by deathadder on 2010-05-19
Hi,

What type of video is it? Are there any errors thrown by mplayer?

---

### Post by __ShaM__ on 2010-05-19
All type of files bro :( e:g: MKV, AVI, FLV, MPG, MPEG etc...

Shows no erorr/erorr msg.

---

### Post by deathadder on 2010-05-19
What config options are you using? I had a search on the forums earlier and found a thread that suggest passing "-vo x11" to mplayer. If that works you can add the following to your ~/.mplayer/config file to use it by default: 
```
vo=x11
```

---

### Post by doas777 on 2010-05-19
first off, what kind of vid card do you have and what driver are you using to run it? 

secondly, if you are going to install mplayer outside of the traditional cannonical repos, I would strongly recomend this ppa:
[https://launchpad.net/~rvm/+archive/mplayer](https://launchpad.net/~rvm/+archive/mplayer)

they have another ppa for smplayer, a nice frontend for mplayer. 

also if you want to file a bug report, it is important to know that if it has a gui, it is not mplayer, but more likely gmplayer, a very stale project, but one that is still in the repos.

---

### Post by andrew.46 on 2010-05-19
Hi ShaM,

> **__ShaM__ said:**
> I'm having problem with MPlayer, I Have updated this from Belgian Repositories but it play files with blank screen. but audio is ok :), what should i do? 

Can you play a file from the commandline with the following syntax:

```
mplayer -v my_file
```

where of course you will have to substitute the correct path and name for 'my_file'. If you post the command and full terminal output here there should be a few clues.

Andrew

---

### Post by __ShaM__ on 2010-05-20
@ [deathadder]("http://ubuntuforums.org/member.php?u=915110"):
Nope, Nothing i have in config file (Blank File), n little success with ur suggestion :), this time got video image at full screen :guitar: but still unable to watch video image at:
Resize 1:2
Resize 1:1
Resize 2:1
& maximum size :(

@ [andrew.46]("http://ubuntuforums.org/member.php?u=208550"):
Here what i got from that command:

```

sham@hell-boy:~$ mplayer -v "/home/sham/Desktop/02). EnglisH SonGz/Linkin Park - New Divide.mkv"
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
Creating config file: /home/sham/.mplayer/config
MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
CPU vendor name: GenuineIntel  max cpuid level: 2
CPU: Intel(R) Pentium(R) 4 CPU 2.40GHz (Family: 15, Model: 2, Stepping: 7)
extended cpuid-level: 4
Detected cache-line size is 64 bytes
Testing OS support for SSE... yes.
Tests of OS support for SSE passed.
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNowExt: 0 SSE: 1 SSE2: 1 SSSE3: 0
Compiled with runtime CPU detection.
get_path('codecs.conf') -> '/home/sham/.mplayer/codecs.conf'
Reading /home/sham/.mplayer/codecs.conf: Can't open '/home/sham/.mplayer/codecs.conf': No such file or directory
Reading /etc/mplayer/codecs.conf: Can't open '/etc/mplayer/codecs.conf': No such file or directory
Using built-in default codecs.conf.
Configuration: --prefix=/usr --confdir=/etc/mplayer --enable-xvmc --enable-menu --enable-largefiles --language=all --disable-libdvdcss-internal --disable-dvdread-internal --disable-libavutil_a --disable-libavcodec_a --disable-libavformat_a --disable-libpostproc_a --disable-libswscale_a --target=i586-linux --enable-runtime-cpudetection --enable-debug --enable-mga --enable-3dfx --enable-tdfxfb --disable-gui
CommandLine: '-v' '/home/sham/Desktop/02). EnglisH SonGz/Linkin Park - New Divide.mkv'
init_freetype
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
get_path('fonts') -> '/home/sham/.mplayer/fonts'
Using nanosleep() timing
get_path('input.conf') -> '/home/sham/.mplayer/input.conf'
Can't open input config file /home/sham/.mplayer/input.conf: No such file or directory
Parsing input config file /etc/mplayer/input.conf
Input config file /etc/mplayer/input.conf parsed: 89 binds
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
get_path('Linkin Park - New Divide.mkv.conf') -> '/home/sham/.mplayer/Linkin Park - New Divide.mkv.conf'

Playing /home/sham/Desktop/02). EnglisH SonGz/Linkin Park - New Divide.mkv.
get_path('sub/') -> '/home/sham/.mplayer/sub/'
[file] File size is 70703518 bytes
STREAM: [file] /home/sham/Desktop/02). EnglisH SonGz/Linkin Park - New Divide.mkv
STREAM: Description: File
STREAM: Author: Albeu
STREAM: Comment: based on the code from ??? (probably Arpi)
LAVF_check: QuickTime/MPEG-4/Motion JPEG 2000 format
libavformat file format detected.
==> Found audio stream: 0
[lavf] Audio stream found, -aid 0
======= WAVE Format =======
Format Tag: 255 (0xFF)
Channels: 2
Samplerate: 44100
avg byte/sec: 0
Block align: 1
bits/sample: 16
cbSize: 2
Unknown extra header dump: [12] [10] 
==========================================================================
==> Found video stream: 1
[lavf] Video stream found, -vid 1
======= VIDEO Format ======
  biSize 80
  biWidth 1280
  biHeight 720
  biPlanes 0
  biBitCount 24
  biCompression 828601953='avc1'
  biSizeImage 2764800
Unknown extra header dump: [1] [64] [0] [1f] [fd] [e1] [0] [18] [67] [64] [0] [1f] [ac] [24] [84] [1] [40] [16] [ec] [4] [40] [0] [0] [c] [80] [0] [2] [57] [a3] [c6] [c] [92] [1] [0] [5] [68] [ee] [32] [c8] [b0] 
===========================
LAVF: 1 audio and 1 video streams found
LAVF: build 3415808
VIDEO:  [avc1]  1280x720  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
[V] filefmt:44  fourcc:0x31637661  size:1280x720  fps:23.976  ftime:=0.0417
get_path('sub/') -> '/home/sham/.mplayer/sub/'
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: Permission denied.
[VO_3DFX] Unable to open /dev/3dfx.
X11 opening display: :0.0
vo: X11 color mask:  FFFFFF  (R:FF0000 G:FF00 B:FF)
vo: X11 running at 1152x864 with depth 24 and 32 bpp (":0.0" => local display)
[x11] Detected wm supports NetWM.
[x11] Detected wm supports FULLSCREEN state.
[x11] Detected wm supports ABOVE state.
[x11] Detected wm supports BELOW state.
[x11] Current fstype setting honours FULLSCREEN ABOVE BELOW X atoms
Disabling DPMS
DPMSDisable stat: 1
[VO_XV] Using Xv Adapter #0 (ATI Rage128 Video Overlay)
[xv common] Drawing colorkey manually.
[xv common] Using colorkey from Xv (0x00001e).
[xv common] Maximum source image dimensions: 2048x2048
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
INFO: libavcodec init OK!
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
dec_audio: Allocating 4608 bytes for input buffer.
dec_audio: Allocating 49152 + 65536 = 114688 bytes for output buffer.
FAAD: Decoder init done (0Bytes)!
FAAD: Negotiated samplerate: 44100Hz  channels: 2
FAAD: compressed input bitrate missing, assuming 128kbit/s!
AUDIO: 44100 Hz, 2 ch, s16le, 128.0 kbit/9.07% (ratio: 16000->176400)
Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio))
==========================================================================
Building audio filter chain for 44100Hz/2ch/s16le -> 0Hz/0ch/??...
[libaf] Adding filter dummy 
[dummy] Was reinitialized: 44100Hz/2ch/s16le
[dummy] Was reinitialized: 44100Hz/2ch/s16le
Trying preferred audio driver 'pulse', options '[none]'
AO: [pulse] 44100Hz 2ch s16le (2 bytes per sample)
AO: Description: PulseAudio audio output
AO: Author: Lennart Poettering
Building audio filter chain for 44100Hz/2ch/s16le -> 44100Hz/2ch/s16le...
[dummy] Was reinitialized: 44100Hz/2ch/s16le
[dummy] Was reinitialized: 44100Hz/2ch/s16le
Starting playback...
Increasing filtered audio buffer size from 0 to 46144
[ffmpeg] aspect_ratio: 1.777778
VDec: vo config request - 1280 x 720 (preferred colorspace: Planar YV12)
Trying filter chain: vo
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO Config (1280x720->1280x720,flags=0,'MPlayer',0x32315659)
VO: [xv] 1280x720 => 1280x720 Planar YV12 
VO: Description: X11/Xv
VO: Author: Gerd Knorr <kraxel@goldbach.in-berlin.de> and others
Xvideo image format: 0x32595559 (YUY2) packed
Xvideo image format: 0x59565955 (UYVY) packed
Xvideo image format: 0x32315659 (YV12) planar
Xvideo image format: 0x30323449 (I420) planar
using Xvideo port 63 for hw scaling
*** [vo] Exporting mp_image_t, 1280x720x12bpp YUV planar, 1382400 bytes
Unicode font: 5025 glyphs.
Unicode font: 5025 glyphs.
A:  28.7 V:  28.0 A-V:  0.670 ct:  0.023   0/  0 71% 13%  1.9% 50 0 

           ************************************************
           **** Your system is too SLOW to play this!  ****
           ************************************************

Possible reasons, problems, workarounds:
- Most common: broken/buggy _audio_ driver
  - Try -ao sdl or use the OSS emulation of ALSA.
  - Experiment with different values for -autosync, 30 is a good start.
- Slow video output
  - Try a different -vo driver (-vo help for a list) or try -framedrop!
- Slow CPU
  - Don't try to play a big DVD/DivX on a slow CPU! Try some of the lavdopts,
    e.g. -vfm ffmpeg -lavdopts lowres=1:fast:skiploopfilter=all.
- Broken file
  - Try various combinations of -nobps -ni -forceidx -mc 0.
- Slow media (NFS/SMB mounts, DVD, VCD etc)
  - Try -cache 8192.
- Are you using -cache to play a non-interleaved AVI file?
  - Try -nocache.
Read DOCS/HTML/en/video.html for tuning/speedup tips.
If none of this helps you, read DOCS/HTML/en/bugreports.html.

ds_fill_buffer: EOF reached (stream: video)    0 68%  7%  1.8% 1769 0 
EOF code: 1  65.7 A-V:  0.030 ct:  0.023   0/  0 68%  7%  1.8% 1769 0 

Uninit audio filters...
[libaf] Removing filter dummy 
Uninit audio: faad
FAAD: Closing decoder!
Uninit video: ffmpeg
Successfully enabled DPMS
vo: uninit ...

Exiting... (End of file)
sham@hell-boy:~$ 
```@ All Others:
Sorry guys i don't know much about linux/ubuntu, don't understand you! but thank you all for ur quick rplies :)...

---

