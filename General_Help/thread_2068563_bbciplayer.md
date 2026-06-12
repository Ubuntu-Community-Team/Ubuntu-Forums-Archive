---
title: "bbciplayer"
date: 2012-10-09
forum: General Help
---

### Post by thomastt371 on 2012-10-09
I have installed this through the software centre,and I cannot find it anywhere though its listed as installed.I am running xubuntu xfce desktop.can anyone advise me whether I have to open it as a command?  michael

---

### Post by pqwoerituytrueiwoq on 2012-10-09
that program has no GUI so there is no menu entry
here is the manual for the program
[http://manpages.ubuntu.com/manpages/precise/man1/get_iplayer.1.html](http://manpages.ubuntu.com/manpages/precise/man1/get_iplayer.1.html)

---

### Post by raja.genupula on 2012-10-09
I think it will be in either Internet or Multimedia categories of menu

---

### Post by jerrrys on 2012-10-09
I don't use it, but [open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

bbciplayer

That should do it.  Also Im sure there are better ways to do it, but I do not run Unity either.  So maybe someone else will give you unity instructions.

And welcome to the forums  :)

Edit:  Hi raja  :)

---

### Post by Merrattic on 2012-10-09
@ [pqwoerituytrueiwoq]("http://ubuntuforums.org/member.php?u=865458")

That's for **get-**iplayer! I uninstalled software centre so can't check but does the OP mean get-iplayer or something else called bbciplayer?

EDIT

Just run a check on software centre, no such application as bbciplayer, so OP must mean get-iplayer?

This is command line app (although there is a GUI out there somewhere for it.)

Useful commands:
```
get-iplayer --help
get-iplayer    << downloads latest listing>>
get-iplayer --refresh    <<updates latest listing>>
get-iplayer --search  myprogram     << searches latest downloaded listing for myprogram>>
get-iplayer --get 123 --subtitles  <<starts download of program with PID 123 and also fetches subtitles>>
```

---

### Post by jimmac49 on 2012-10-09
Google it, BBC iPlayer  and register then bookmark it in Firefox, thats how I do it, no probs.

---

### Post by pqwoerituytrueiwoq on 2012-10-09
> **Merrattic said:**
> @ [pqwoerituytrueiwoq]("http://ubuntuforums.org/member.php?u=865458")

That's for **get-**iplayer! I uninstalled software centre so can't check but does the OP mean get-iplayer or something else called bbciplayer?

that was the closest thing i could find in my software center/synaptic on 12.10 i assumed that was it

---

### Post by coldraven on 2012-10-09
Say you want to watch Inspector Montalbano, open a terminal and type 
```
get_iplayer inspector
```Then you will see something like this
```
coldraven@happy:~$ get_iplayer inspector
get_iplayer v2.80, Copyright (C) 2008-2010 Phil Lewis
  This program comes with ABSOLUTELY NO WARRANTY; for details use --warranty.
  This is free software, and you are welcome to redistribute it under certain
  conditions; use --conditions for details.

Matches:
416:    Inspector Montalbano: Series 2 - 2. Equal Time, BBC Four, Crime,Drama,Guidance,TV, default
417:    Inspector Montalbano: Series 2 - 3. The Patience of the Spider, BBC Four, Crime,Drama,Guidance,TV, default
418:    Inspector Montalbano: Series 2 - 4. The Game of Three Cards, BBC Four, Crime,Drama,Guidance,TV, default
419:    Inspector Montalbano: Series 2 - 5. August Flame, BBC Four, Crime,Drama,Guidance,TV, default
420:    Inspector Montalbano: Series 2 - 6. The Wings of the Sphynx, BBC Four, Crime,Drama,Guidance,TV, default
421:    Inspector Montalbano: Series 2 - 7. The Track of Sand, BBC Four, Crime,Drama,Guidance,Highlights,TV, default,
422:    Inspector Montalbano: Series 2 - 1. Turning Point, BBC Four, Crime,Drama,Guidance,TV, default

INFO: 7 Matching Programmes

```If you want them all type
```
get_iplayer --get inspector
```If you only want to see the last one type
```
get_iplayer --get 422
```It will download to your home directory.

---

### Post by Cheesemill on 2012-10-09
To make life easier I have these 2 aliases in my ~/.bashrc file:
```
alias ipl='get_iplayer --nocopyright'
alias gipl='get_iplayer --nocopyright --output=~/Videos --tvmode=flashhd,flashvhigh,flashhigh,flashstd,flashnormal --get'

```I can then use ipl to search for a program and then gipl to download it (in HD if available), for example:
```
rob@arch:~$ ipl Buzzcocks
Matches:
509:    Never Mind the Buzzcocks: Series 26 - Episode 2, BBC Two, Comedy,Entertainment,Games & Quizzes,Guidance,TV, default
510:    Never Mind the Buzzcocks: Series 26 - Episode 3, BBC Two, Comedy,Entertainment,Games & Quizzes,Guidance,HD,Popular,TV, default,

INFO: 2 Matching Programmes
``````
rob@arch:~$ gipl 510
Matches:
510:    Never Mind the Buzzcocks: Series 26 - Episode 3, BBC Two, Comedy,Entertainment,Games & Quizzes,Guidance,HD,Popular,TV, default,

INFO: 1 Matching Programmes
INFO: Checking existence of default version
INFO: flashvhigh1,flashvhigh2,flashvhigh3,flashvhigh4,flashhigh1,flashhigh2,flashstd1,flashstd2 modes will be tried for version default
INFO: Trying flashvhigh1 mode to record tv: Never Mind the Buzzcocks: Series 26 - Episode 3
INFO: File name prefix = Never_Mind_the_Buzzcocks_Series_26_-_Episode_3_b01nclbn_default                 
RTMPDump v2.4
(c) 2010 Andrej Stepanchuk, Howard Chu, The Flvstreamer Team; license: GPL
Connecting ...
INFO: Connected...
Starting download at: 0.000 kB
INFO: Metadata:
INFO:   duration              1760.13
INFO:   moovPosition          32.00
INFO:   width                 1280.00
INFO:   height                720.00
INFO:   videocodecid          avc1
INFO:   audiocodecid          mp4a
INFO:   avcprofile            100.00
INFO:   avclevel              41.00
INFO:   aacaot                2.00
INFO:   videoframerate        25.00
INFO:   audiosamplerate       24000.00
INFO:   audiochannels         2.00
INFO: trackinfo:
INFO:   length                44001000.00
INFO:   timescale             25000.00
INFO:   language              eng
INFO: sampledescription:
INFO:   sampletype            avc1
INFO:   length                42243072.00
INFO:   timescale             24000.00
INFO:   language              eng
INFO: sampledescription:
INFO:   sampletype            mp4a
596288.851 kB / 1760.09 sec (99.9%)
Download complete
ffmpeg version 1.0 Copyright (c) 2000-2012 the FFmpeg developers
  built on Sep 29 2012 11:22:50 with gcc 4.7.1 (GCC) 20120721 (prerelease)
  configuration: --prefix=/usr --enable-libmp3lame --enable-libvorbis --enable-libxvid --enable-libx264 --enable-libvpx --enable-libtheora --enable-libgsm --enable-libspeex --enable-postproc --enable-shared --enable-x11grab --enable-libopencore_amrnb --enable-libopencore_amrwb --enable-libschroedinger --enable-libopenjpeg --enable-librtmp --enable-libpulse --enable-libv4l2 --enable-gpl --enable-version3 --enable-runtime-cpudetect --disable-debug --disable-static
  libavutil      51. 73.101 / 51. 73.101
  libavcodec     54. 59.100 / 54. 59.100
  libavformat    54. 29.104 / 54. 29.104
  libavdevice    54.  2.101 / 54.  2.101
  libavfilter     3. 17.100 /  3. 17.100
  libswscale      2.  1.101 /  2.  1.101
  libswresample   0. 15.100 /  0. 15.100
  libpostproc    52.  0.100 / 52.  0.100
Input #0, flv, from '/home/rob/Videos/Never_Mind_the_Buzzcocks_Series_26_-_Episode_3_b01nclbn_default.partial.mp4.flv':
  Metadata:
    moovPosition    : 32
    avcprofile      : 100
    avclevel        : 41
    aacaot          : 2
    videoframerate  : 25
    audiochannels   : 2
  Duration: 00:29:20.12, start: 0.000000, bitrate: 2775 kb/s
    Stream #0:0: Video: h264 (High), yuv420p, 1280x720 [SAR 180:180 DAR 16:9], 25 tbr, 1k tbn, 50 tbc
    Stream #0:1: Audio: aac, 48000 Hz, stereo, s16
Output #0, mp4, to '/home/rob/Videos/Never_Mind_the_Buzzcocks_Series_26_-_Episode_3_b01nclbn_default.partial.mp4':
  Metadata:
    moovPosition    : 32
    avcprofile      : 100
    avclevel        : 41
    aacaot          : 2
    videoframerate  : 25
    audiochannels   : 2
    encoder         : Lavf54.29.104
    Stream #0:0: Video: h264 ([33][0][0][0] / 0x0021), yuv420p, 1280x720 [SAR 180:180 DAR 16:9], q=2-31, 1k tbn, 1k tbc
    Stream #0:1: Audio: aac ([64][0][0][0] / 0x0040), 48000 Hz, stereo
Stream mapping:
  Stream #0:0 -> #0:0 (copy)
  Stream #0:1 -> #0:1 (copy)
Press [q] to stop, [?] for help
frame=44001 fps=22316 q=-1.0 Lsize=  596017kB time=00:29:20.12 bitrate=2774.0kbits/s    
video:574390kB audio:20354kB subtitle:0 global headers:0kB muxing overhead 0.214015%
INFO: Recorded /home/rob/Videos/Never_Mind_the_Buzzcocks_Series_26_-_Episode_3_b01nclbn_default.mp4

INFO: Downloaded Thumbnail to '/home/rob/Videos/Never_Mind_the_Buzzcocks_Series_26_-_Episode_3_b01nclbn_default.jpg
```'

---

### Post by evilsoup on 2012-10-09
Another neat thing you can do with get_iplayer is streaming from the BBC, without. You need mplayer (VLC can also do it).

```
get_iplayer --stream 422 | mplayer -
```

You can allegedly stream live TV as well, but I can't get that to work, so the BBC must have changed things at some point.

---

