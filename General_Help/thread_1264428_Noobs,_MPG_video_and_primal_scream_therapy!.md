---
title: "Noobs, MPG video and primal scream therapy!"
date: 2009-09-12
forum: General Help
---

### Post by Irvine_himself on 2009-09-12
I am  using Ubuntu 9.04 Juanty on Dell optiplex GX270.

For the last two day's, I have been trying to play mpg videos without success. The mpg's themselves play fine on XP using the VLC media player......

 The steps I have taken so far are

1/ installed the restricted codecs
2/ installed the win32 codecs
3/ installed Dragon player
4/ installed all possible option for xine, gxine and totem-xine
5/ installed Kaffiene
6/ installed Real player.

(Movie player was already installed)

After installing the extra codecs, they now play the audio track , but there is no video output, (just a blank screen.) Before, they were starting and immediately shutting down.

Kaffeine is detecting both the Real player and Win32 codecs, I haven't figured out how to check the others.

Does anybody have any ideas about how I could proceed?



By the way, Flash video in Firefox works fine, but if I try to run my MPG video in Firefox it just loads and quits as if it was an empty file. (again they play fine using Firefox in XP)

---

### Post by BUSHYBOB on 2009-09-12
> **Irvine_himself said:**
> The mpg's themselves play fine on XP using the VLC media player......

 

Have you tried VLC on Ubuntu?

---

### Post by Irvine_himself on 2009-09-12
Sorry, I thought I had made that clear. Yes I have tried VLC for Ubuntu, I have also installed every thing related to gstreamer that didn't conflict or was marked bad.

---

### Post by BUSHYBOB on 2009-09-12
VLC uses it's own built in codecs. Are you using the same versions?

---

### Post by Irvine_himself on 2009-09-12
> **BUSHYBOB said:**
> VLC uses it's own built in codecs. Are you using the same versions?

The Ubuntu version came from synaptic and is 0.9,  the Xp version was 0.9 but I just updated it to 1.0 something or other, they both worked.

I haven't installed the gstreamer thingies marked bad and ugly, but I found this    [http://linux.about.com/od/ubuntu_doc/a/ubudg6t2.htm](http://linux.about.com/od/ubuntu_doc/a/ubudg6t2.htm)  which says that I should.

What does bad and ugly refer to in this case and is it likely to work?

---

### Post by BUSHYBOB on 2009-09-12
Not sure about bad and ugly, but I'd go for it.

---

### Post by Irvine_himself on 2009-09-12
> **BUSHYBOB said:**
> Not sure about bad and ugly, but I'd go for it.

The box is up at my mates until I get it set up for my needs, (mainly graphics, web design and some Delphi programming.) He has a high speed internet whereas I have a 56k modem.... which is free! 

But if I don't hear anything to the contrary tonight, I think that is going to be a go. As far as I can see, I have nothing to lose and everything to win. I can always re-install!

---

### Post by rob-ward on 2009-09-12
Not sure why vlc won't work for you it should, you could try and install the newer VLC in ubuntu 

instructions here - [http://rob-ward.co.uk/thisarticle.php?id=18](http://rob-ward.co.uk/thisarticle.php?id=18)

It may also help if you were to run vlc from the commandline and play the file, the debug may help if there is a problem

---

### Post by Irvine_himself on 2009-09-12
Thanks Rob,

I will try that first thing tomorrow and if running it from the command line turns up anything I will let you know.

---

### Post by BUSHYBOB on 2009-09-13
It's possible that the xp and linux versions of vlc have been compiled with different sets of codecs.

---

### Post by andrew.46 on 2009-09-13
Hi Irvine,

> **Irvine_himself said:**
> Does anybody have any ideas about how I could proceed?

I suspect an excellent move would be to identify what codecs are being used in your problem videos. One way is to use FFmpeg, if you want to try this way download a copy of FFmpeg according to these directions:

HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

and then run FFmpeg with your problem file as follows:

```
ffmpeg -i ***[COLOR="Red"]problem_file.mpg[/COLOR]***
```

If you can then post the full FFmpeg terminal output, including your command, in a post here it should not be too much of a problem to get them playing.

Andrew

---

### Post by Irvine_himself on 2009-09-13
> **BUSHYBOB said:**
> It's possible that the xp and linux versions of vlc have been compiled with different sets of codecs.

"Ahgrrrr"!! Now I remember why, many years ago, I switched back to Xp from Fedora. Only, (partly,) joking...... snigger. While I understand the need for copyright, this is another example of how stupid our current copyright laws really are.


Thanks Andrew.46, that sounds like really good advice. Though for the moment, I have a friendly Systems Engineer / (Linux Specialist) tearing his hair out with  another unrelated problem, (communication cards,) and I won't be able to get back to this until tomorrow.


For those of you who are sadists. 

He started at midday yesterday and was at it till 5am this morning. At one point he completely crashed everything to the point that it refused to boot... He now has the modem talking very badly with the server. When I get the full details, I will post a bug report but it was something to do with Jaunta not liking the modem because it wasn't fast enough....

---

### Post by Irvine_himself on 2009-09-15
Okay, I am sort of back to this for the moment, (my dial up modem problem is only half solved but my systems engineer has had to go back to his real work.)

Here is the output from running FFmpeg:
> 
irvine@irvine-desktop:~$ ffmpeg -i 'problemfile.mpg' 
FFmpeg version 0.5-svn17737+3:0.svn20090303-1ubuntu6, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --extra-version=svn17737+3:0.svn20090303-1ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --disable-stripping --disable-vhook --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-armv6t2 --disable-armvfp --disable-neon --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 10 2009 23:18:41, gcc: 4.3.3
Input #0, mpeg, from '/problemfile.mpg':
  Duration: 00:14:01.16, start: 0.397767, bitrate: 1394 kb/s
    Stream #0.0[0x1e0]: Video: mpeg1video, yuv420p, 352x240 [PAR 200:219 DAR 880:657], 1150 kb/s, 29.97 tbr, 90k tbn, 29.97 tbc
    Stream #0.1[0x1c0]: Audio: mp2, 44100 Hz, stereo, s16, 224 kb/s
At least one output file must be specified
I notice the line "Input #0, mpeg, from '/problemfile.mpg':" I am not sure what it means, but the file is 138 MB and runs fine inXp.  FFmpeg launched Movie player which immediately closed. In Kaffeine the video ran with Audio but a black screen.

As I say, all the Mpgs run fine in XP with a variety of players including VLC, the Ubuntu version of VLC opens the video and immediatel closes.

---

### Post by andrew.46 on 2009-09-15
Hi Irvine,

> **Irvine_himself said:**
> As I say, all the Mpgs run fine in XP with a variety of players including VLC, the Ubuntu version of VLC opens the video and immediatel closes.

Looks like a pretty ordinary file to me. You should be able to play this file with the basic player that comes with FFmpeg:

```
ffplay problemfile.mpg
```

and I would be a little taken aback if the file did not spring to life. As regards vlc I would suggest perhaps opening up the preferences and selecting another video output. I have attached a screenshot to show the menu I am referring to, perhaps try x11?

All the best,

Andrew

---

### Post by Irvine_himself on 2009-09-15
Hi Andrew

The x11 video preferences worked thank you

As for

ffplay -i problemfile.mpg

 I suppose it is only of academic interest since I can now play with VLC player and un-install the ones I don't use?  But FFplay  did not like "-i"

> 
FFplay version 0.5-svn17737+3:0.svn20090303-1ubuntu6, Copyright (c) 2003-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --extra-version=svn17737+3:0.svn20090303-1ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --disable-stripping --disable-vhook --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-armv6t2 --disable-armvfp --disable-neon --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 10 2009 23:18:41, gcc: 4.3.3
ffplay: unrecognized option '-i'
irvine@irvine-desktop:~$ ffplay  problemfile.mpg
FFplay version 0.5-svn17737+3:0.svn20090303-1ubuntu6, Copyright (c) 2003-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --extra-version=svn17737+3:0.svn20090303-1ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --disable-stripping --disable-vhook --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-armv6t2 --disable-armvfp --disable-neon --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 10 2009 23:18:41, gcc: 4.3.3
problemfile.mpg: no such file or directory
irvine@irvine-desktop:~$ ffplay -i problemfile.mpg
FFplay version 0.5-svn17737+3:0.svn20090303-1ubuntu6, Copyright (c) 2003-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --extra-version=svn17737+3:0.svn20090303-1ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --disable-stripping --disable-vhook --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-armv6t2 --disable-armvfp --disable-neon --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 10 2009 23:18:41, gcc: 4.3.3
ffplay: unrecognized option '-i'
irvine@irvine-desktop:~$ ffplay i problemfile.mpg
FFplay version 0.5-svn17737+3:0.svn20090303-1ubuntu6, Copyright (c) 2003-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --extra-version=svn17737+3:0.svn20090303-1ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --disable-stripping --disable-vhook --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-armv6t2 --disable-armvfp --disable-neon --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 10 2009 23:18:41, gcc: 4.3.3
problemfile.mpg: no such file or directory
irvine@irvine-desktop:~$ ffplay -i problemfile.mpg
FFplay version 0.5-svn17737+3:0.svn20090303-1ubuntu6, Copyright (c) 2003-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --extra-version=svn17737+3:0.svn20090303-1ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --disable-stripping --disable-vhook --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-armv6t2 --disable-armvfp --disable-neon --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 10 2009 23:18:41, gcc: 4.3.3
ffplay: unrecognized option '-i'
irvine@irvine-desktop:~$ 


---

### Post by andrew.46 on 2009-09-15
Hi Irvine,

> **Irvine_himself said:**
> The x11 video preferences worked thank you

Excellent news :).

> As for

```
ffplay -i problemfile.mpg
```

 I suppose it is only of academic interest since I can now play with VLC player and un-install the ones I don't use?  But FFplay  did not like "-i"

Oops, I have had a small mental aberration and transposed an FFmpeg command on to FFplay, my apologies :). I have taken the liberty of correcting my post above...

All the best,

Andrew

---

### Post by Irvine_himself on 2009-09-15
Thanks, I am working from two different machine at two different locations, so I will try that tomorrow. Meantime I am marking this solved

---

### Post by andrew.46 on 2009-09-15
Hi Irvine,

> **Irvine_himself said:**
> Thanks, I am working from two different machine at two different locations, so I will try that tomorrow. 

I would not get too excited about FFplay, it is a very simple piece of software only designed for the most basic testing of FFmpeg and media files. vlc of course is another thing all together...

Andrew

---

