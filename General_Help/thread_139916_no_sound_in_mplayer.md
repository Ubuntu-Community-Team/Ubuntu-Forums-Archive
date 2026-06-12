---
title: "no sound in mplayer"
date: 2006-03-05
forum: General Help
---

### Post by beck24 on 2006-03-05
Hi, I've read all that I can read and still nothing resembles what I have here.
mplayer is working fine for video, and it's not outputting any errors, I'm just not getting any sound.  I've tried editting the conf file to all the combinations of audio output that are available...


matt@ubuntu:~$ mplayer -ao help
MPlayer 1.0pre7try2-3.3.6 (C) 2000-2005 MPlayer Team
CPU: Advanced Micro Devices  (Family: 8, Stepping: 0)
Detected cache-line size is 64 bytes
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 3DNow 3DNowEx SSE SSE2


Available audio output drivers:
        mpegpes DVB audio output
        oss     OSS/ioctl audio output
        null    Null audio output
        pcm     RAW PCM/WAVE file writer audio output

matt@ubuntu:~$                 

I have sound for all other apps, and xine is working fine.  Any ideas?

---

### Post by codejunkie on 2006-03-05
[QUOTE=beck24]Hi, I've read all that I can read and still nothing resembles what I have here.
mplayer is working fine for video, and it's not outputting any errors, I'm just not getting any sound.  I've tried editting the conf file to all the combinations of audio output that are available...


matt@ubuntu:~$ mplayer -ao help
MPlayer 1.0pre7try2-3.3.6 (C) 2000-2005 MPlayer Team
CPU: Advanced Micro Devices  (Family: 8, Stepping: 0)
Detected cache-line size is 64 bytes
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 3DNow 3DNowEx SSE SSE2


Available audio output drivers:
        mpegpes DVB audio output
        oss     OSS/ioctl audio output
        null    Null audio output
        pcm     RAW PCM/WAVE file writer audio output

matt@ubuntu:~$                 

I have sound for all other apps, and xine is working fine.  Any ideas?[/QUOTE]

run ```
sudo gedit ~/.mplayer/config
```and make the file look like this
```

# Write your default config options here!
vo=xv,x11
ao=esd,oss,arts

```
run ```
sudo gedit ~/.mplayer/gui.conf
```make it look like this
```

enable_audio_equ = "no"
vo_driver = "xv"
vo_panscan = "0.000000"
vo_doublebuffering = "yes"
vo_direct_render = "no"
vo_dxr3_device = "/dev/em8300-0"
v_framedrop = "0"
v_flip = "-1"
v_ni = "no"
v_idx = "-1"
vf_pp = "no"
vf_autoq = "0"
vf_lavc = "no"
ao_driver = "esd"
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
playbar = "no"
load_fullscreen = "no"
show_videowin = "yes"
stopxscreensaver = "no"
autosync = "no"
autosync_size = "0"
gui_skin = "default"
gui_save_pos = "yes"
gui_main_pos_x = "28187"
gui_main_pos_y = "2066"
gui_video_out_pos_x = "6"
gui_video_out_pos_y = "46"
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
and if your using the mozilla-mplayer plugin run
```
sudo gedit /etc/mplayerplug-in.conf
```
make it look like this
```

#debug=0
vo=xv,x11
ao=esd,oss,arts
#download=1
#dload-dir=$HOME/tmp
#keep-download=0
noembed=1
#cachesize=512
#use-mimetypes=0
enable-ogg=1
enable-smil=1
enable-helix=1
qt-speed=high
#rtsp-use-tcp=0
#nomediacache=0
#framedrop=0
#autosync=0
#mc=1
#black-background=0
#user-agent=NSPlayer

```
and run
```
touch mplayerplug-in.so
```
after you've made all the changes.

---

### Post by beck24 on 2006-03-05
I'm afraid that didn't work... copying your conf actually prevented mplayer from starting up at all, just editting the audio options didn't seem to make a difference.  I haven't bothered with the mozilla plugin just yet... figured if mplayer wouldn't work stand-alone then there's no point.

Any other ideas?

---

### Post by Georges on 2006-03-05
I had this issue. Phenomen was like this:

mplayer does not complain about busy device or locks up. It just shows the video, no sound.
Same goes for everything else supposed to make sound.
My PC used the internal speaker with onboard sound. 
In my case I was using XFCE as dektop. And that volume control panel had no effect.
In a terminal I then started alsamixer and moved the mono-volume up. From that point on the xfce volume control worked.

No mplayer config fiddeling needed.

---

### Post by beck24 on 2006-03-05
Thanx for the replies, but still nothing... it would be much easier if it came up with an error or something.

Any other ideas?

---

### Post by kingsidy on 2006-03-05
i think that you need to go into the settings and select alsa or esd as the sound system. go into the preferences and under the sound tab, select alsa or esd. Try that and see if one them works.

---

### Post by beck24 on 2006-03-05
I don't have the option of alsa or esd, which may be the root of the problem.  Here's the output when I play a file.

> MPlayer 1.0pre7try2-3.3.6 (C) 2000-2005 MPlayer Team
CPU: Advanced Micro Devices  (Family: 8, Stepping: 0)
Detected cache-line size is 64 bytes
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 3DNow 3DNowEx SSE SSE2


Cannot load font: /usr/share/fonts/truetype/msttcorefonts/impact.ttf
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Playing test.avi.
AVI file format detected.
VIDEO:  [XVID]  624x352  12bpp  23.976 fps  987.0 kbps (120.5 kbyte/s)
Clip info:
 Software: VirtualDub
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [mp3] afm:mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
vo: X11 running at 1280x768 with depth 24 and 32 bpp (":0.0" => local display)
xscreensaver_disable: xscreensaver wid=10485761.
Opening video filter: [hqdn3d]
Opening video filter: [pp=de]
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm:ffmpeg (FFmpeg MPEG-4)
==========================================================================
[PP] Using external postprocessing filter, max q = 6.
Checking audio filter chain for 48000Hz/2ch/s16le -> 48000Hz/2ch/s16le...
AF_pre: 48000Hz/2ch/s16le
Could not open/initialize audio device -> no sound.
Audio: no sound
Starting playback...
VDec: vo config request - 624 x 352 (preferred csp: Planar YV12)
[PP] Using external postprocessing filter, max q = 6.
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.77:1 - prescaling to correct movie aspect.
VO: [x11] 624x352 => 624x352 Planar YV12  [zoom]
SwScaler: using unscaled Planar YV12 -> BGRA special converter
V:  11.6 278/278  6% 31%  0.0% 0 6
Exiting... (Quit)


Any idea how I can enable alsa or esd?

---

### Post by beck24 on 2006-03-06
Bump.

Anybody know how to make mplayer use alsa or esd if those options aren't listed for audio outputs?

---

### Post by matttail on 2006-03-07
I'm also having this problem.  I'm actaully using xine engine and gxine frotn end, also same progme with totem movie player.  Sound works perfectly fine in xmms and from gnome it self, but no sound from anything I try and play from gxine.  Vidoe is working great, just no sound.

---

