---
title: "vlc too slow to play MKV files?"
date: 2010-02-06
forum: General Help
---

### Post by princeofnam on 2010-02-06
from what i've heard, VLC doesn't support multi-threading, whatever that means, and so plays MKV files with much more CPU use.  is there any alternative? i know windows as COREAVC, but i don't believe that software is available for linux.

---

### Post by ubudog on 2010-02-06
Why don't you just use totem?  It comes with Ubuntu and normally everything works out of the box.

---

### Post by knurledflanges on 2010-02-06
I'm kinda wrestling blindly with this issue too, since neither VLC or Totem "just work" with mkv's on my system due to extreme lag/choppiness in the frame rate, but Mplayer often works fine, although I'm having trouble with audio getting out of sync on it with some files. From what I've read and observed, it's not necessarily lack of CPU power that's the problem. I have some mkv's that play just fine in VLC on Windows on my old 1.3ghz machine but do the 1 frame per second thing in VLC on Ubuntu.

---

### Post by falconindy on 2010-02-06
vlc is a "fork" of mplayer, which I've found to be far better. It doesn't have a GUI by default, but I've heard smplayer is a popular front end for it. There's instructions on these forums about compiling the svn version of mplayer, which gets you VDPAU support and multithreading. It's worth the time to do so if your hardware supports it.

---

### Post by solitaire on 2010-02-06
> **princeofnam said:**
> from what i've heard, VLC doesn't support multi-threading, whatever that means, and so plays MKV files with much more CPU use.  is there any alternative? i know windows as COREAVC, but i don't believe that software is available for linux.

What CPU have you got?

I can play 720p MKV fine using "cvlc" with my 2Ghz Celeron CPU hits 75%-80%

---

### Post by lovinglinux on 2010-02-06
> **knurledflanges said:**
> I'm kinda wrestling blindly with this issue too, since neither VLC or Totem "just work" with mkv's on my system due to extreme lag/choppiness in the frame rate, but Mplayer often works fine, although I'm having trouble with audio getting out of sync on it with some files. From what I've read and observed, it's not necessarily lack of CPU power that's the problem. I have some mkv's that play just fine in VLC on Windows on my old 1.3ghz machine but do the 1 frame per second thing in VLC on Ubuntu.

The mkv container is not the problem, but the resolution is. I used to play low resolution mkv files without problems in a Pentium 4, but was unable to play 720p videos, no matter if they were mkv, avi or something else. The thing is that mkv's are often used as the container of choice for 720p + videos encoded with h.264. These  probably play fine in Windows because of PureVideo technology. 

> From: [http://en.wikipedia.org/wiki/PureVideo](http://en.wikipedia.org/wiki/PureVideo)

Nvidia PureVideo  is a hardware feature designed to offload video decoding processes and video post-processing from a computer's CPU  hardware to NVIDIA's GPU hardware series GeForce 6, GeForce 7, GeForce 8, GeForce 9 and GeForce 200 ; GeForce M series (formerly known as GeForce Go); and Nvidia Quadro series. PureVideo is designed to work with Microsoft's Windows Media Player and Windows Media Center. NVIDIA's device drivers for Windows XP, Windows Vista and Windows 7  are PureVideo-enabled; with the appropriate (PureVideo-enabled) application software, the NVIDIA driver will automatically use whatever hardware-acceleration is available on the NVIDIA display-adapter.

In Linux, there is no PureVideo, but VDPAU, which doesn't work with all cards. For instance I have a nVidia 7300 GT, which supports PureVideo but not VDPAU, so unless I'm using a powerful CPU in Linux, the video will be choppy, since the decoding is entirely done by the CPU. For instance, I wasn't able to watch 720p videos when I had a Pentium 4, but they play just fine now, that I have upgraded to a Core 2 Duo.

> From: [http://en.wikipedia.org/wiki/VDPAU](http://en.wikipedia.org/wiki/VDPAU)

VDPAU (Video Decode and Presentation API for Unix) is an open source library (libvdpau) and API originally designed by NVIDIA for its GeForce 8 series and later GPU  hardware[2][3], targeted at the X Window System on Unix operating-systems (including Linux, FreeBSD, and Solaris).[4][5][6]  This VDPAU API allows video programs to offload portions of the video decoding process and video post-processing to the GPU video-hardware.

Currently, the portions capable of being offloaded by VDPAU onto the GPU are motion compensation (mo comp), inverse discrete cosine transform (iDCT) and VLD (Variable-Length Decoding) for MPEG-1, MPEG-2, MPEG-4 ASP (MPEG-4 Part 2), MPEG-4 AVC (H.264 / DivX 6), VC-1, WMV3/WMV9, Xvid / OpenDivX (DivX 4), and DivX 5 encoded videos.[4] Which specific codecs of these that can be offloaded to the GPU depends on the generation version of the GPU hardware, specifically to also decode MPEG-4 ASP (MPEG-4 Part 2), Xvid / OpenDivX (DivX 4), and DivX 5 formats a GeForce 200M (2xxM) Series (the eleventh generation of NVIDIA's GeForce graphics processing units) or newer GPU hardware is required[7].

VDPAU can be described as the X Window System equivalent of the Microsoft's DxVA (DirectX Video Acceleration) API for Windows[4].

---

### Post by princeofnam on 2010-02-06
is mplayer "Movie Player?"

---

### Post by lovinglinux on 2010-02-06
> **princeofnam said:**
> is mplayer "Movie Player?"

Yes, but I would recommend using [smplayer](apt:smplayer) instead. It's just another frontend to mplayer, but with better features.

---

### Post by knurledflanges on 2010-02-06
> **lovinglinux said:**
> Yes, but I would recommend using [smplayer]("apt:smplayer") instead. It's just another frontend to mplayer, but with better features.

The op was probably referring to the app named "Movie Player" in the default Ubuntu applications menu, which is Totem. Is Totem a frontend for mplayer? In my scenario above, I downloaded the package named "MPlayer" from the Ubuntu Software Center, and that was able to play some of the 720p x264 mkvs that weren't working in Totem or VLC for me, without having to configure anything except setting the video driver used to "xv."

Thanks for the explanation of the VDPAU stuff. I have an old Geforce 6200 card and a 1.2ghz processor; does that mean I'm kind of hosed on this front unless I get new hardware? If this is the case, why does Mplayer seem to be able to keep up with the frame rate while other players can't?

---

### Post by princeofnam on 2010-02-06
strangely, my ubuntu laptop with intel dual core 2 (1.5 ghz each) plays a 1080p video slower on movie player than my pentium 4 3 ghz processor downstairs with windows and CoreAVC.

---

### Post by princeofnam on 2010-02-06
can the "front end" for a program exist independently of it? or do i need to install mplayer to use smplayer?

---

### Post by lovinglinux on 2010-02-07
> **knurledflanges said:**
> The op was probably referring to the app named "Movie Player" in the default Ubuntu applications menu, which is Totem. Is Totem a frontend for mplayer? In my scenario above, I downloaded the package named "MPlayer" from the Ubuntu Software Center, and that was able to play some of the 720p x264 mkvs that weren't working in Totem or VLC for me, without having to configure anything except setting the video driver used to "xv."

Sorry. I'm running KDE minimal without the Software Center for so long that I forgot about that. The "Movie Player" from Ubuntu applications menu is indeed Totem, which is based on Gstreamer, not mplayer. The Mplayer you have downloaded is the mplayer frontend. I use smplayer and gnome-mplayer, which are also frontends to mplayer.

> **knurledflanges said:**
> Thanks for the explanation of the VDPAU stuff. I have an old Geforce 6200 card and a 1.2ghz processor; does that mean I'm kind of hosed on this front unless I get new hardware?

Yep.

> **knurledflanges said:**
> If this is the case, why does Mplayer seem to be able to keep up with the frame rate while other players can't?

I have no idea :)

---

### Post by lovinglinux on 2010-02-07
> **princeofnam said:**
> strangely, my ubuntu laptop with intel dual core 2 (1.5 ghz each) plays a 1080p video slower on movie player than my pentium 4 3 ghz processor downstairs with windows and CoreAVC.

Probably because the GPU on Windows supports PureVideo.

> **princeofnam said:**
> can the "front end" for a program exist independently of it? or do i need to install mplayer to use smplayer?

No. You need to install mplayer-nogui to use smplayer.

---

### Post by andrew.46 on 2010-02-08
Hi falconindy,

> **falconindy said:**
> vlc is a "fork" of mplayer, which I've found to be far better. 

It is a bit of a nitpick but vlc actually predates MPlayer by a few years. The vlc project started back [in 1996]("http://en.wikipedia.org/wiki/VLC_media_player#History") while MPlayer started [in 2000]("http://en.wikipedia.org/wiki/MPlayer#History").

> There's instructions on these forums about compiling the svn version of mplayer, which gets you VDPAU support and multithreading. It's worth the time to do so if your hardware supports it.

And for the bold compilers with a bit of time on their hands there is now also a guide for compiling the git vlc:

Howto: Build the development version of vlc under Ubuntu
[http://ubuntuforums.org/showthread.php?t=1398119](http://ubuntuforums.org/showthread.php?t=1398119)

although I will acknowledge that the vlc guide is not for the faint-hearted :).

Andrew

---

