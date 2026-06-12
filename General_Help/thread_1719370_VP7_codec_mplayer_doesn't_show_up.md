---
title: "VP7 codec mplayer doesn't show up"
date: 2011-04-01
forum: General Help
---

### Post by qwertyjjj on 2011-04-01
I have maverick meerkat.
I'm tryting to play a video but it has a VP7 codec and VLC will not play it.
I installed mplayer but it doesnt show up in the sound and video menu options.
I have Movie Player but not Mplayer Movie Player?
Any ideas?

---

### Post by andrew.46 on 2011-04-02
Looks like a 32 bit MPlayer with the w32codecs (vp7vfw.dll) should play vp7 files:

```

andrew@skamandros~$ mplayer -vc help | grep -i 'vp7'

vp7         vfwex     working   On2 VP7 Personal Codec  [vp7vfw.dll]

```

I tested this on my own system with the following sample:
```

wget http://samples.mplayerhq.hu/V-codecs/VP7/potter-700.vp7
```

and it played the video perfectly from the commandline MPlayer:

```

andrew@skamandros~/Desktop$ mplayer potter-700.vp7 
MPlayer SVN-r33187-4.5.2 (C) 2000-2011 MPlayer Team

Playing potter-700.vp7.
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [VP70]  624x352  24bpp  23.976 fps  696.8 kbps (85.1 kbyte/s)
Load subtitles in ./
==========================================================================
Opening video decoder: [vfwex] Win32/VfWex video codecs
Loading codec DLL: 'vp7vfw.dll'
Win32 LoadLibrary failed to load: /usr/lib/codecs/vp7vfwLOC.dll
Loaded DLL driver vp7vfw.dll at 10000000
[PP] Using codec's postprocessing, max q = 9.
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 624x352 => 624x352 Packed YUY2 
**[COLOR="Red"]Selected video codec: [vp7] vfm: vfwex (On2 VP7 Personal Codec)[/COLOR]**
==========================================================================
==========================================================================
Cannot find codec for audio format 0x500.
Audio: no sound
Starting playback...
V:  24.3 584/584 18%  0%  0.0% 0 0 

Exiting... (Quit)

```

although oddly enough failed to play the audio which I shall investigate a little further :(.

Andrew

---

### Post by qwertyjjj on 2011-04-03
It plays the video, that's not the problem. The problem is that mplayer is not in the menu Applications --> Sound Video --> ?

---

### Post by andrew.46 on 2011-04-03
> **qwertyjjj said:**
> It plays the video, that's not the problem. The problem is that mplayer is not in the menu Applications --> Sound Video --> ?

OIC, perhaps add a decent gui:

```
sudo apt-get install smplayer
```

Andrew

---

### Post by qwertyjjj on 2011-04-05
> **andrew.46 said:**
> OIC, perhaps add a decent gui:

```
sudo apt-get install smplayer
```

Andrew

smplayer barely plays the video. the sound works but the video frame only updates every 2 seconds. mplayer from the command line works but sometimes the video stutters.
Isn't there anyway to get this to play in VLC?

---

### Post by andrew.46 on 2011-04-05
> **qwertyjjj said:**
> Isn't there anyway to get this to play in VLC?

I think not :(. vlc can be compiled to use external codecs by using an *--enable-loader* ./configure option but last I heard this part of the code was no longer being developed and vp7 does not figure here anyway.

---

### Post by qwertyjjj on 2011-04-06
any ideas what might cause the small stutter in playback in mplayer that doesn't occur in vlc? At first I thought it might be the video card not having enough memory but then that doesn't make sense as both apps should have the same problem...unless it's a codec thing?

---

### Post by andrew.46 on 2011-04-06
Some hints might be gleaned by running MPlayer with the *-v* option. Usually such problems will relate to audio or video output devices used and a good starting step is to experiment a little with either. Available settings can be seen as follows:
[B]
Video:[/B]

```

andrew@skamandros~$ **[COLOR="Red"]mplayer -vo help[/COLOR]**
MPlayer SVN-r33187-4.5.2 (C) 2000-2011 MPlayer Team
Available video output drivers:
	xv	X11/Xv
	gl_nosw	OpenGL no software rendering
	x11	X11 ( XImage/Shm )
	xover	General X11 driver for overlay capable video output drivers
	sdl	SDL YUV/RGB/BGR renderer (SDL v1.1.7+ only!)
	gl	OpenGL
	gl2	X11 (OpenGL) - multiple textures version
	dga	DGA ( Direct Graphic Access V2.0 )
	fbdev	Framebuffer Device
	fbdev2	Framebuffer Device
	svga	SVGAlib
	matrixview	MatrixView (OpenGL)
	aa	AAlib
	caca	libcaca
	v4l2	V4L2 MPEG Video Decoder Output
	xvidix	X11 (VIDIX)
	cvidix	console VIDIX
	null	Null video output
	mpegpes	MPEG-PES to DVB card
	yuv4mpeg	yuv4mpeg output for mjpegtools
	png	PNG file
	jpeg	JPEG file
	gif89a	animated GIF output
	tga	Targa output
	pnm	PPM/PGM/PGMYUV file
	md5sum	md5sum of each frame

```

Many of these have specialised use, but certainly xv and gl are good choices and of course vdpau if you have it available.
[B]
Audio:[/B]

```

andrew@skamandros~$ **[COLOR="Red"]mplayer -ao help[/COLOR]**
MPlayer SVN-r33187-4.5.2 (C) 2000-2011 MPlayer Team
Available audio output drivers:
	oss	OSS/ioctl audio output
	alsa	ALSA-0.9.x-1.x audio output
	esd	EsounD audio output
	sdl	SDLlib audio output
	mpegpes	DVB audio output
	v4l2	V4L2 MPEG Audio Decoder output
	null	Null audio output
	pcm	RAW PCM/WAVE file writer audio output

```

pulse seems to cause a bit of trouble, I personally do not have this available for MPlayer...

---

### Post by sazawal on 2012-03-17
I have the same problem. I am using 64 bit ubuntu 10.10. I have downloaded mplayer from medibuntu and it seems that vp7 codec is  already installed. But my file with vp7 codec is not not showing the  video. Although the audio is working fine. Here is the output of the  command

```
$ mplayer -vc help | grep vp7 
vp7         vfwex     working   On2 VP7 Personal Codec  [vp7vfw.dll]
```And here is the terminal output when I tried to play my file (.ogm format) with mplayer

```
$ mplayer blues.ogm 
MPlayer 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing blues.ogm.
libavformat file format detected.
[ogg @ 0x1598a20]max_analyze_duration reached
[lavf] stream 0: video (unknown), -vid 0
[lavf] stream 1: audio (vorbis), -aid 0
VIDEO:  [VP70]  640x352  0bpp  29.970 fps    0.0 kbps ( 0.0 kbyte/s)
SUB: Added subtitle file (1): ./blues.srt
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
[VO_3DFX] Unable to open /dev/3dfx.
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
[vdpau] Error when calling vdp_device_create_x11: 1
==========================================================================
**Requested video codec family [vp7] (vfm=vfwex) not available.**
Enable it at compilation.
Cannot find codec matching selected -vo and video format 0x30375056.
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 64.0 kbit/4.17% (ratio: 8000->192000)
Selected audio codec: [ffvorbis] afm: ffmpeg (FFmpeg Vorbis)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:   3.6 (03.5) of 5566.3 ( 1:32:46.3)  0.4% 

MPlayer interrupted by signal 2 in module: play_audio
A:   3.8 (03.7) of 5566.3 ( 1:32:46.3)  0.4%
```

Please help.

---

### Post by andrew.46 on 2012-03-18
What mplayer shows is that it is capable of decoding vp7 files by using vp7vfw.dll* if* it is available. I feel your pain, I am now running a 64bit MPlayer and thus don't have access to the windows codecs. But the need for these codecs is decreasing rapidly and the pain of building a 32bit MPlayer on a 64bit system is too much :(.

---

### Post by sazawal on 2012-03-18
So my still doesn't have vp7 codec although mplayer is able to decode it? I have downloaded manually vp7vfw.dll, what if I save it in my system files, would it work?

---

### Post by andrew.46 on 2012-03-18
The 64bit MPlayer will not use this codec :(.

---

### Post by sazawal on 2012-03-20
[IMG]http://ubuntuforums.org/images/icons/icon9.gif[/IMG]

---

### Post by andrew.46 on 2012-03-20
But I am thinking of writing a guide that deals with compiling the 32bit MPlayer on a 64bit system, there seems some demand, It is not impossible to do but there will be many small issues. I am away for 2 weeks from Thursday, when I return I will start writing.....

---

### Post by sazawal on 2012-03-20
Thanks a lot if you can do it. I am a newbie, but still I will try to help you out. Is there a need to build the complete mplayer for 64 bit system? mplayer is already running in my system, the problem is just with vp7 codec. A minor change in 32 bit one wouldn't work?

---

### Post by SeijiSensei on 2012-03-20
One option to consider while Andrew writes his guide is installing a 32-bit version of Ubuntu in a virtual machine on your 64-bit platform using [VirtualBox]("http://www.virtualbox.org/").  How well this will perform depends on the speed of the machine's CPU.  It might be worth a try, though, if you really need to watch those videos.

---

### Post by andrew.46 on 2012-03-20
> **sazawal said:**
>  A minor change in 32 bit one wouldn't work?

What is needed is a set of 32bit libraries installed to lib32 (the ia32-libs package), a multi-lib enabled compiler and a few extra options passed to MPlayer when compiling. There are a few other issues related to packaging though, for example whether this new MPlayer replaces the existing 64bit one, where it should be installed, should it have another name etc etc. It will be interesting :)

---

### Post by SeijiSensei on 2012-03-20
And then you'll get to do it all over again with the mplayer2 source! :D

---

### Post by sazawal on 2012-03-30
I was reading some forums and found that it is possible to compile and install 32-bit mplayer on 64-bit ubuntu. Here is a link to the forum [http://vvishnyakov.blogspot.in/2011/11/32bit-mplayer-on-64bit-ubuntu.html?showComment=1332713065028#c8100050247649659962]("http://vvishnyakov.blogspot.in/2011/11/32bit-mplayer-on-64bit-ubuntu.html?showComment=1332713065028#c8100050247649659962http://")
Unfortunately, that didn't work out for me. Any ideas andrew.46?

---

### Post by andrew.46 on 2012-03-30
> **sazawal said:**
>  Any ideas andrew.46?

I am away at the moment but the man who has the experience doing this is mc4man, very active on these Forums and I am sure he won't mind the question :).

---

