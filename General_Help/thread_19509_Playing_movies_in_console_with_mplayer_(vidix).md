---
title: "Playing movies in console with mplayer (vidix)"
date: 2005-03-12
forum: General Help
---

### Post by krusbjorn on 2005-03-12
Hi,

as i cant get tv-out to work in X, i'm trying to play movies in the console. as the title states, i'm using mplayer and vidix. 

however, 

mplayer -vo cvidix -v  ./Thumb\ Wars\ The\ Phantom\ Cuticle.avi

result in the following (sudo'ing the command doesnt help):

> MPlayer 1.0pre6-3.3.4 (C) 2000-2004 MPlayer Team
CPU: Intel Celeron 2/Pentium III Coppermine,Geyserville (Family: 6, Stepping: 10)
Detected cache-line size is 32 bytes
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 0
Compiled for x86 CPU with extensions: MMX MMX2 SSE


CommandLine: '-vo' 'cvidix' '-v' './Thumb Wars The Phantom Cuticle.avi'
get_path('font/font.desc') -> '/home/johannes/.mplayer/font/font.desc'
font: can't open file: /home/johannes/.mplayer/font/font.desc
Font /usr/local/share/mplayer/font/font.desc loaded successfully! (206 chars)
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
Linux RTC init error in ioctl (rtc_irqp_set 1024): Åtkomst nekas
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Using nanosleep() timing
get_path('input.conf') -> '/home/johannes/.mplayer/input.conf'
Can't open input config file /home/johannes/.mplayer/input.conf: Filen eller katalogen finns inte
Parsing input config file /usr/local/etc/mplayer/input.conf
Input config file /usr/local/etc/mplayer/input.conf parsed: 59 binds
get_path('Thumb Wars The Phantom Cuticle.avi.conf') -> '/home/johannes/.mplayer/Thumb Wars The Phantom Cuticle.avi.conf'
Playing ./Thumb Wars The Phantom Cuticle.avi.
[file] File size is 640657408 bytes
STREAM: [file] ./Thumb Wars The Phantom Cuticle.avi
STREAM: Description: File
STREAM: Author: Albeu
STREAM: Comment: based on the code from ??? (probably Arpi)
AVI file format detected.
list_end=0x2292
======= AVI Header =======
us/frame: 33367  (fps=29,970)
max bytes/sec: 0
padding: 0
MainAVIHeader.dwFlags: (272) HAS_INDEX IS_INTERLEAVED
frames  total: 52226   initial: 0
streams: 2
Suggested BufferSize: 0
Size:  640 x 480
==========================
list_end=0x10F4
==> Found video stream: 0
====== STREAM Header =====
Type: vids   FCC: div3 (33766964)
Flags: 0
Priority: 0   Language: 0
InitialFrames: 0
Rate: 29970/1000 = 29,970
Start: 0   Len: 52226
Suggested BufferSize: 55739
Quality 10000
Sample size: 0
==========================
found 'bih', 40 bytes of 40
======= VIDEO Format ======
  biSize 40
  biWidth 640
  biHeight 480
  biPlanes 1
  biBitCount 24
  biCompression 861292868='DIV3'
  biSizeImage 921600
===========================
Regenerating keyframe table for DIVX3 video
list_end=0x2186
==> Found audio stream: 1
====== STREAM Header =====
Type: auds   FCC:  (0)
Flags: 0
Priority: 0   Language: 0
InitialFrames: 1
Rate: 48000/1152 = 41,667
Start: 0   Len: 72609
Suggested BufferSize: 960
Quality -1
Sample size: 0
==========================
found 'wf', 30 bytes of 18
======= WAVE Format =======
Format Tag: 85 (0x55)
Channels: 2
Samplerate: 48000
avg byte/sec: 22554
Block align: 1152
bits/sample: 0
cbSize: 12
mp3.wID=1
mp3.fdwFlags=0x2
mp3.nBlockSize=541
mp3.nFramesPerBlock=1
mp3.nCodecDelay=0
===========================
list_end=0x2292
AVI: dmlh found (size=248) (total_frames=52226)
list_end=0x22B6
hdr=Software  size=15
Software  : Nandub v1.0rc2
list_end=0x26112A80
Found movie at 0x280C - 0x26112A80
Reading INDEX block, 124835 chunks for 52226 frames (fpos=0x26112a88)
AVI index offset: 0x2808 (movi=0x280C idx0=0x4 idx1=0x18C)
Auto-selected AVI audio ID = 1
Auto-selected AVI video ID = 0
AVI: Searching for audio stream (id:1)
AVI video size=598318246 (52226) audio size=39306240 (72609)
VIDEO:  [DIV3]  640x480  24bpp  29,970 fps  2746,8 kbps (335,3 kbyte/s)
[V] filefmt:3  fourcc:0x33564944  size:640x480  fps:29,97  ftime:=0,0334
Clip info:
 Software: Nandub v1.0rc2
get_path('sub/') -> '/home/johannes/.mplayer/sub/'
get_path('default.sub') -> '/home/johannes/.mplayer/default.sub'
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
dec_audio: Allocating 4608 + 65536 = 70144 bytes for output buffer.
mp3lib: made decode tables with MMX optimization
mp3lib: using MMX optimized decore!
MP3lib: init layer2&3 finished, tables done
MPEG 1.0, Layer III, 48000 Hz 32 kbit Joint-Stereo, BPF: 96
Channels: 2, copyright: No, original: Yes, CRC: No, emphasis: 0
AUDIO: 48000 Hz, 2 ch, 16 bit (0x10), ratio: 4000->192000 (32,0 kbit)
Selected audio codec: [mp3] afm:mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
vo_cvidix: No vidix driver name provided, probing available ones (-v option for details)!
vidixlib: PROBING: /usr/local/lib/mplayer/vidix/rage128_vid.so
vidixlib: /usr/local/lib/mplayer/vidix/rage128_vid.so not driver: libdha.so.1.0: kan inte öppna delad objektfil: Filen eller katalogen finns inte
vidixlib: PROBING: /usr/local/lib/mplayer/vidix/pm3_vid.so
vidixlib: /usr/local/lib/mplayer/vidix/pm3_vid.so not driver: libdha.so.1.0: kan inte öppna delad objektfil: Filen eller katalogen finns inte
vidixlib: PROBING: /usr/local/lib/mplayer/vidix/mga_crtc2_vid.so
vidixlib: /usr/local/lib/mplayer/vidix/mga_crtc2_vid.so not driver: libdha.so.1.0: kan inte öppna delad objektfil: Filen eller katalogen finns inte
vidixlib: PROBING: /usr/local/lib/mplayer/vidix/sis_vid.so
vidixlib: /usr/local/lib/mplayer/vidix/sis_vid.so not driver: libdha.so.1.0: kan inte öppna delad objektfil: Filen eller katalogen finns inte
vidixlib: PROBING: /usr/local/lib/mplayer/vidix/radeon_vid.so
vidixlib: /usr/local/lib/mplayer/vidix/radeon_vid.so not driver: libdha.so.1.0: kan inte öppna delad objektfil: Filen eller katalogen finns inte
vidixlib: PROBING: /usr/local/lib/mplayer/vidix/unichrome_vid.so
vidixlib: /usr/local/lib/mplayer/vidix/unichrome_vid.so not driver: libdha.so.1.0: kan inte öppna delad objektfil: Filen eller katalogen finns inte
vidixlib: PROBING: /usr/local/lib/mplayer/vidix/nvidia_vid.so
vidixlib: /usr/local/lib/mplayer/vidix/nvidia_vid.so not driver: libdha.so.1.0: kan inte öppna delad objektfil: Filen eller katalogen finns inte
vidixlib: PROBING: /usr/local/lib/mplayer/vidix/mach64_vid.so
vidixlib: /usr/local/lib/mplayer/vidix/mach64_vid.so not driver: libdha.so.1.0: kan inte öppna delad objektfil: Filen eller katalogen finns inte
vidixlib: PROBING: /usr/local/lib/mplayer/vidix/mga_vid.so
vidixlib: /usr/local/lib/mplayer/vidix/mga_vid.so not driver: libdha.so.1.0: kan inte öppna delad objektfil: Filen eller katalogen finns inte
vidixlib: PROBING: /usr/local/lib/mplayer/vidix/savage_vid.so
vidixlib: /usr/local/lib/mplayer/vidix/savage_vid.so not driver: libdha.so.1.0: kan inte öppna delad objektfil: Filen eller katalogen finns inte
vidixlib: PROBING: /usr/local/lib/mplayer/vidix/cyberblade_vid.so
vidixlib: /usr/local/lib/mplayer/vidix/cyberblade_vid.so not driver: libdha.so.1.0: kan inte öppna delad objektfil: Filen eller katalogen finns inte
vosub_vidix: Couldn't find working VIDIX driver
Error opening/initializing the selected video_out (-vo) device.

uninit audio: mp3lib
vo: x11 uninit called but X11 not inited..

Exiting... (End of file) 

I have dowbloaded, compiled and installe the vidix, and the files in /usr/local/lib/mplayer/vidix/ are in place. 

libdha.so.1.0 is located in ~/program/MPlayer-1.0pre6a/libdha/
and in /usr/local/lib/

Anyone have any suggestions? Are there other drivers that are easier to get to work?

Thanks
 -Johannes

EDIT: btw "kan inte öppna delad objektfil: Filen eller katalogen finns inte" means "can not open shared objectfile. File or directory doesnt exist."

If i choose vesa instead of cvidix, it works perfectly, 'cept for the tearing.

---

### Post by encompass on 2006-11-06
Not sure what I am using but I can do it most times perfectly.  I don't put any settings in the command.  But I am running edgy.

---

