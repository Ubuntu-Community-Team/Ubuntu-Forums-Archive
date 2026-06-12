---
title: "VDPAU Slow and Jump in Maverick"
date: 2010-10-23
forum: General Help
---

### Post by lakerssuperman on 2010-10-23
I recently upgraded to Maverick.  I did a clean install on my system.  I am running NVIDIA drivers from the X-Swat repo.  Whenever I try to play a mkv file using Gnome Mplayer it is very jumpy and laggy.  VLC, using it's new hardware acceleration, won't even display video, though it does output the audio.  I experienced none of these problems with my 10.04 setup.  Is anyone else experiencing this?  I am unsure if it is a player bug, a driver bug or something with the VDPAU library itself.  Thanks for any help you can offer.

---

### Post by 3togo on 2010-10-25
Are u sure u could run mplayer with vdpau support?

At present, the libvdpau is using nvidia 256.xxx while the nvidia-current is 260.xxx. I will be surprised if u could start your mplayer with vdapu support.

Correct me if I am wrong.

>mplayer -vo vdpau xxx.mkv

---

### Post by okanplz on 2010-10-25
I installed 10.10 yesterday and I have the same problem. I'm using the "current" version of the driver.

I think this is caused by 260.xxx, how can I go back to 256.xxx?

EDIT:

I've manually installed 256.53. That did not fix the problem

---

### Post by 3togo on 2010-10-25
I don't have time to try but below is some information that u might find it useful

1) Aplattner updated his libvdpau on Sept 2010 but I couldn't find which version of nvidia he is rerferring to.
[http://cgit.freedesktop.org/~aplattner/libvdpau](http://cgit.freedesktop.org/~aplattner/libvdpau)

2)Debian >> Packages >> experimental >> Source >> x11 >> nvidia-graphics-drivers
experimental version of  nvidia-graphics-drivers (256.53-2)
[http://packages.debian.org/source/experimental/nvidia-graphics-drivers](http://packages.debian.org/source/experimental/nvidia-graphics-drivers)

3)nvidia-current 260 includes another version of libvdpau_nvidia.so which might interfere with 1)
ps. Though nvidia developer mentioned in their web site that they will not include libvdpau_nvidia.so in the future, the conflict between 1) and 3) should remain as a problem rite now.

---

### Post by UrbenLegend on 2010-10-25
I am experiencing the same issue. Here's two solutions that worked for me.

1.) Reverting back to Nvidia 256 drivers sped things up a bit. I know okanplz said that he reverted back to these drivers and noticed no improvment, which brings me to my second solution,

2.) Maverick comes with pulseaudio installed, so you might be tempted to use pulse as the audio output in mplayer. DO NOT use pulse. Running the audio through pulseaudio causes the video to jerk at random intervals. I found that setting audio output to ALSA in mplayer sped things up a bit and since Pulseaudio has an ALSA plugin, you still get the benefits of Pulseaudio anyways.

Overall I've noticed that solution 1 speeds things up A LOT (with 260 drivers I couldn't even play videos in VLC), and solution 2 just removes some of the jerkiness that you might be experiencing. Using both of them at the same time has pretty much returned my VPDAU playback speeds to Karmic speeds.

---

### Post by okanplz on 2010-10-25
> **UrbenLegend said:**
> I am experiencing the same issue. Here's two solutions that worked for me.

1.) Reverting back to Nvidia 256 drivers sped things up a bit. I know okanplz said that he reverted back to these drivers and noticed no improvment, which brings me to my second solution,

2.) Maverick comes with pulseaudio installed, so you might be tempted to use pulse as the audio output in mplayer. DO NOT use pulse. Running the audio through pulseaudio causes the video to jerk at random intervals. I found that setting audio output to ALSA in mplayer sped things up a bit and since Pulseaudio has an ALSA plugin, you still get the benefits of Pulseaudio anyways.

Overall I've noticed that solution 1 speeds things up A LOT (with 260 drivers I couldn't even play videos in VLC), and solution 2 just removes some of the jerkiness that you might be experiencing. Using both of them at the same time has pretty much returned my VPDAU playback speeds to Karmic speeds.

I didn't know the jerk in the video was caused by pulse so I thought vdpau was the problem. I think it works now.

After going back and forth between 256.xx and 260.xx a couple times here's what I found:

256.xx probably works fine. There were some problems but my guess is that they were caused by pulse like UrbenLegend said.


I'm using 260.xx(from nvidia.com) now. It works but if I enable A*SS subtitles memory usage goes crazy. mplayer's memory usage went up to more than 1 GBs. I think I'll go back to 256.xx and try with A*SS subtitles.

---

### Post by 3togo on 2010-10-26
In my case, create a 2GB swapfile could help

>hdparm --fallocate 2000000 /swapfile ## (kilo-bytes)
>mkswap /swapfile
>swapon /swapfile

---

### Post by andremagoo on 2010-11-04
I had the same problem. So I install vdpau-va-driver and problem is gone.

Sorry for my bad english, just trying to help.

Edit: Using nvidia 260.19.12 drivers. CPU usage now arround 8%.

---

### Post by UrbenLegend on 2010-11-16
New driver 260.19.21 fixes the issue. Happy movie watching guys :P

---

### Post by Avari on 2010-11-17
> **UrbenLegend said:**
> New driver 260.19.21 fixes the issue. Happy movie watching guys :P
In my case it is incorrect :(
After I installed Maverick, I had the same problem: when playing video through VDPAU (mplayer -vo vdpau -vc ffh264vdpau movie.mkv), only about the first second played smoothly, then the playback speed drops sharply (maybe from 25 fps to 5-10?). Then the rate rises, but playback is not smooth.
Mplayer output looks like that:
```

MPlayer 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing &#1047;&#1072;&#1075;&#1088;&#1091;&#1079;&#1082;&#1080;/Mai-HiME [BD] [720p]/Mai-Hime 01 (BD 960x720 h264 FLAC) [Coalgirls].mkv.
libavformat file format detected.
[matroska @ 0xd3a740]Estimating duration from bitrate, this may be inaccurate
[lavf] stream 0: video (h264), -vid 0, Mai Hime 01
[lavf] stream 1: audio (flac), -aid 0, -alang jpn, 2.0 FLAC
[lavf] stream 2: subtitle (unknown), -sid 0, -slang eng, English
VIDEO:  [H264]  960x720  0bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
Clip info:
 doctype: matroska
 title: Mai Hime 01
==========================================================================
Forced video codec: ffh264vdpau
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264vdpau] vfm: ffmpeg (FFmpeg H.264 (VDPAU))
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 0.0 kbit/0.00% (ratio: 0->192000)
Selected audio codec: [ffflac] afm: ffmpeg (FFmpeg FLAC audio)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
[VD_FFMPEG] Trying pixfmt=0.
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [vdpau] 960x720 => 960x720 H.264 VDPAU acceleration 
[VD_FFMPEG] XVMC-accelerated MPEG-2.
A:   3.0 V:   2.0 A-V:  0.992 ct:  2.036   0/  0 16% 31%  0.1% 50 0 

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

A:   9.7 V:   9.7 A-V: -0.000 ct:  0.085   0/  0  3% 13%  0.4% 81 0 
Exiting... (Quit)

```
Now I installs 260.19.21 from ppa:ubuntu-x-swat/x-updates. The problem remains the same. I tried -ao sdl or -ao alsa - nothing has changed.
sudo dpkg-reconfigure linux-image-2.6.35-22-generic and sudo dpkg-reconfigure nvidia-current also did not change anything.
I can't install 256 drivers, because Synaptic shows only two variants of 260, and I do not want to abuse a package management system by installing video drivers from tarball :(
Please, tell me where I can leave bug report about this problem? It still exists as I can see :( I want to write bug report but I don't know where :(
PS. Ubuntu x64

---

### Post by lakerssuperman on 2010-11-17
I just installed the 260.19.21 and performance watching movies is slower than ever.  It's mildly frustrating.  I have not yet tried to revert to the 256 drivers.  It seems like from some of the reports, there may be some performance regression in the 260 line of drivers.

---

### Post by Avari on 2010-11-19
If you are too affected by this problem, please leave your bug reports here:
[vdpau slowness with 260.19.06]("http://www.nvnews.net/vbulletin/showthread.php?t=155618")

---

### Post by UrbenLegend on 2010-11-26
@Avari

From your logs you look like you're using the pulse audio output. Try switching that to ALSA and see if you get better results. Pulse lags the video for me (refer to my first post).

---

### Post by UrbenLegend on 2010-12-13
I have to take back my statement. It is slowing down for me again. The slow down occurs right after I run any 3D game. A video ram usage issue?

---

### Post by pedja_portugalac on 2010-12-27
> **andremagoo said:**
> I had the same problem. So I install vdpau-va-driver and problem is gone.

Sorry for my bad english, just trying to help.

Edit: Using nvidia 260.19.12 drivers. CPU usage now arround 8%.

Thank you very much. This is the right solution! Everything works good now. ;)

---

