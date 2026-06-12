---
title: "Need help with streaming video's in mplayer"
date: 2006-03-11
forum: General Help
---

### Post by ndhskp on 2006-03-11
When I try to play streaming video from QVC or HSN the quality is very poor.  QVC has very jerky playback and HSN has very poor A/V sync.  The web sites in question are> [QVC]("http://www.qvc.com") and [HSN](http://www.hsn.com/cnt/program_guide/default.aspx?prev=hsnToday&o=!LNHSNPG&cm_sp=Global*LNTV*ProgramGuide)
The QVC link is the red thing on the left that says "Watch QVC live"

My W32 codecs are up to date and mplayer is compiled from the latest cvs.  Mplayer plugin is compiled to the latest version 3.21 and I am running the Firefox nightlys currently at (2006031104).  My ADSL connection is in pratical terms 4Mb down and 720Kb up.  Also my cpu is Intel 1.8Ghz with 2GB of system merory.  I have played these streams before when I used to have windows and they played perfectly in windows media but I no longer use windows.  Any ideas anybody?

Here is my code output for mplayer```
username@ubuntu:~$ mplayer mms://live.hsn.com/hsnlive
MPlayer dev-CVS-060311-03:12-4.0.2 (C) 2000-2006 MPlayer Team
CPU: Intel Pentium 4/Celeron 4 Northwood; Pentium 4 EE/Xeon Prestonia,Gallatin (Family: 15, Stepping: 9)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2


Playing mms://live.hsn.com/hsnlive.
STREAM_ASF, URL: mms://live.hsn.com/hsnlive
Resolving live.hsn.com for AF_INET6...
Couldn't resolve name for AF_INET6: live.hsn.com
Resolving live.hsn.com for AF_INET...
Connecting to server live.hsn.com[192.234.237.145]: 1755...
Connected
Unknown object
Unknown object
File object, packet length = 8000 (8000)
Unknown object
Stream object, stream id: 1
Stream object, stream id: 2
Unknown object
Unknown object
Data object
mmst packet_length = 8000
Cache size set to 64 KBytes
Cache fill:  0.00% (0 bytes)
ASF file format detected.
VIDEO:  [WMV3]  480x360  24bpp  1000.000 fps    0.0 kbps ( 0.0 kbyte/s)
Clip info:
 name: HSN
 author: HSN
 copyright: Copyright \uffff 2006 HSN
 comments:
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 32000 Hz, 2 ch, s16le, 32.0 kbit/3.12% (ratio: 4000->128000)
Selected audio codec: [ffwmav2] afm: ffmpeg (DivX audio v2 (FFmpeg))
==========================================================================
==========================================================================
Opening video decoder: [dmo] DMO video codecs
DMO dll supports VO Optimizations 0 1
DMO dll might use previous sample when requested
GetOutput r=0x0   size:518400  align:1
StreamCount r=0x0  1  1
Decoder supports the following formats: YV12 YUY2 UYVY YVYU RGB8 RGB555 RGB565 RGB24 RGB32
Decoder is capable of YUV output (flags 0x1b)
VDec: vo config request - 480 x 360 (preferred colorspace: Packed YUY2)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 480x360 => 480x360 Planar YV12
Selected video codec: [wmv9dmo] vfm: dmo (Windows Media Video 9 DMO)
==========================================================================
AO: [oss] 32000Hz 2ch s16le (2 bytes per sample)
Starting playback...
A:13867.5 V:13867.5 A-V:  0.015 ct: -1.657 1195/1195  6%  0% 13.0% 7 0 18%

MPlayer interrupted by signal 2 in module: decode_audio


MPlayer interrupted by signal 2 in module: enable_cache
username@ubuntu:~$
```Mplayer plugin conf file```
#debug=0
#vo=xv,x11
#ao=arts,esd,oss
#download=1
#dload-dir=$HOME/tmp
#keep-download=0
#noembed=0
#cachesize=512
#use-mimetypes=0
#enable-ogg=1
#enable-smil=1
#enable-helix=1
qt-speed=high
#rtsp-use-tcp=0
#nomediacache=0
#framedrop=0
#autosync=0
#mc=1
#black-background=0
#user-agent=NSPlayer
```Mplayer mplayerplugin.types file```
video/mpeg:mpg,mpeg:MPEG;
audio/mpeg:mpg,mpeg:MPEG;
video/x-mpeg:mpg,mpeg:MPEG;
video/x-mpeg2:mpv2,mp2ve:MPEG2;
audio/mpeg:mpg,mpeg:MPEG;
audio/x-mpeg:mpg,mpeg:MPEG;
audio/mpeg2:mp2:MPEG audio;
audio/x-mpeg2:mp2:MPEG audio;
audio/mpeg3:mp3:MPEG audio;
audio/x-mpeg3:mp3:MPEG audio;
audio/mp3:mp3:MPEG audio;
audio/x-mpegurl:m3u:MPEG url;
video/mp4:mp4:MPEG 4 Video;
application/x-ogg:ogg:Ogg Vorbis Media;
audio/ogg:ogg:Ogg Vorbis Audio;
application/ogg:ogg:Ogg Vorbis / Ogg Theora;
video/fli:fli,flc:FLI animation;
video/x-fli:fli,flc:FLI animation;
video/vnd.vivo:viv,vivo:VivoActive;
application/x-nsv-vp3-mp3:nsv:Nullsoft Streaming Video;
audio/basic:au,snd:Basic audio;
audio/x-basic:au,snd:Basic audio;
audio/x-scpls:pls:Shoutcast Playlist;
video/divx:divx:DivX Media Format;
video/vnd.divx:divx:DivX Media Format;
audio/midi:mid,midi,kar:MIDI Audio;
```Main mplayer gui.conf file```
enable_audio_equ = "no"
vo_driver = "xv"
vo_panscan = "0.000000"
vo_doublebuffering = "yes"
vo_direct_render = "yes"
v_framedrop = "1"
v_flip = "0"
v_ni = "no"
v_idx = "-1"
vf_pp = "no"
vf_autoq = "0"
vf_lavc = "no"
ao_driver = "alsa"
ao_volnorm = "no"
softvol = "no"
ao_surround = "no"
ao_extra_stereo = "no"
ao_extra_stereo_coefficient = "1.000000"
dvd_device = "/dev/dvd"
cdrom_device = "/dev/cdrom"
osd_level = "1"
sub_auto_load = "yes"
sub_unicode = "no"
sub_pos = "100"
sub_overlap = "no"
font_factor = "0.750000"
font_text_scale = "5.000000"
font_osd_scale = "6.000000"
font_blur = "2.000000"
font_outline = "2.000000"
font_autoscale = "3"
cache = "no"
cache_size = "2048"
playbar = "yes"
load_fullscreen = "no"
show_videowin = "yes"
stopxscreensaver = "no"
autosync = "no"
autosync_size = "0"
gui_skin = "default"
gui_save_pos = "yes"
gui_main_pos_x = "524"
gui_main_pos_y = "585"
gui_video_out_pos_x = "150"
gui_video_out_pos_y = "48"
equ_band_00 = "0.000000"
equ_band_01 = "0.000000"
equ_band_02 = "0.000000"
equ_band_03 = "0.000000"
equ_band_04 = "0.000000"
equ_band_05 = "0.000000"
equ_band_06 = "0.000000"
equ_band_07 = "0.000000"
equ_band_08 = "0.000000"
equ_band_09 = "0.000000"
equ_band_10 = "0.000000"
equ_band_11 = "0.000000"
equ_band_12 = "0.000000"
equ_band_13 = "0.000000"
equ_band_14 = "0.000000"
equ_band_15 = "0.000000"
equ_band_16 = "0.000000"
equ_band_17 = "0.000000"
equ_band_18 = "0.000000"
equ_band_19 = "0.000000"
equ_band_20 = "0.000000"
equ_band_21 = "0.000000"
equ_band_22 = "0.000000"
equ_band_23 = "0.000000"
equ_band_24 = "0.000000"
equ_band_25 = "0.000000"
equ_band_26 = "0.000000"
equ_band_27 = "0.000000"
equ_band_28 = "0.000000"
equ_band_29 = "0.000000"
equ_band_30 = "0.000000"
equ_band_31 = "0.000000"
equ_band_32 = "0.000000"
equ_band_33 = "0.000000"
equ_band_34 = "0.000000"
equ_band_35 = "0.000000"
equ_band_36 = "0.000000"
equ_band_37 = "0.000000"
equ_band_38 = "0.000000"
equ_band_39 = "0.000000"
equ_band_40 = "0.000000"
equ_band_41 = "0.000000"
equ_band_42 = "0.000000"
equ_band_43 = "0.000000"
equ_band_44 = "0.000000"
equ_band_45 = "0.000000"
equ_band_46 = "0.000000"
equ_band_47 = "0.000000"
equ_band_48 = "0.000000"
equ_band_49 = "0.000000"
equ_band_50 = "0.000000"
equ_band_51 = "0.000000"
equ_band_52 = "0.000000"
equ_band_53 = "0.000000"
equ_band_54 = "0.000000"
equ_band_55 = "0.000000"
equ_band_56 = "0.000000"
equ_band_57 = "0.000000"
equ_band_58 = "0.000000"
equ_band_59 = "0.000000"
```

---

### Post by Jingo on 2006-04-23
Same problem here:

Source for demo: mms://wms.dr.dk/storage/forbrug/Livsstil/dolph/dw5.wmv
Try Windows vs. Ubuntu.

Bitrate in Ubuntu to low... only 40 kbit/s
In Windows: 500kbit/s

which explains the quality difference... but how do I get Ubuntu to accept higher stream ?

---

### Post by ndhskp on 2006-04-23
[quote=Jingo]Same problem here:

Source for demo: mms://wms.dr.dk/storage/forbrug/Livsstil/dolph/dw5.wmv
Try Windows vs. Ubuntu.

Bitrate in Ubuntu to low... only 40 kbit/s
In Windows: 500kbit/s

which explains the quality difference... but how do I get Ubuntu to accept higher stream ?[/quote]One thing you can do is to look for the ip address of the 500kb stream and then enter that address manually into the main mplayer program.```
mplayer Adresss of video goes here
```  Or you can enter it in the mplayer gui if you have that installed.

---

### Post by Jingo on 2006-04-23
You mean there's no way to let mplayer chose the better quality stream automatic ?
Everytime I want to look at a stream, I should start windows to get the best streams ip ?

---

### Post by ndhskp on 2006-04-23
[quote=Jingo]You mean there's no way to let mplayer chose the better quality stream automatic ?
Everytime I want to look at a stream, I should start windows to get the best streams ip ?[/quote]In Firefox you can always use View>Page Source or Ctrl+u to see the souce code for the page to get the address.  Or Tools>Page Info or Ctrl+i.  There probably is a way to tell mplayer how to select the proper stream but you need to go to the mplayer website and look at their documentation.

[Mplayer web site.](http://www.mplayerhq.hu/design7/news.html)

---

### Post by reubadoob on 2006-04-27
I too am experiencing extreme choppiness when watching a video stream with mplayer. I always seem to get a the AF_INET6 error message but the video plays in a small window outside of firefox. Is there anyway to keep the video from opening another window? What can be done about the choppiness?

---

### Post by WADemosthenes on 2006-07-01
[QUOTE=reubadoob]I too am experiencing extreme choppiness when watching a video stream with mplayer. I always seem to get a the AF_INET6 error message but the video plays in a small window outside of firefox. Is there anyway to keep the video from opening another window? What can be done about the choppiness?[/QUOTE]

I have the exact same problem, no idea how to fix it though.

Edit: try this:
[QUOTE=_jason]add ```
prefer-ipv4 = yes
``` to your ~/.mplayer/config[/QUOTE]

---

