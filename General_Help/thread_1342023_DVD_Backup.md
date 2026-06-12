---
title: "DVD Backup"
date: 2009-11-30
forum: General Help
---

### Post by kadeous on 2009-11-30
Greetings,
 
I'm using Ubuntu Server 9.10 Edition.
 
I followed the FFMPEG X264 Guide here and everything installed nicely. I'm now trying to make backups of our dvd collection at home and place them on the server to stream to the PS3, I have all that working great.
 
So I downloaded and installed vobcopy and used that to start ripping DVD's, it works and creates the .VOB file.
 
Now I'm trying to convert them in FFMPEG but this is the error that I'm getting. I've searched google, and here for answers but came up empty. Any help is greatly apprecaited as I'm still getting the hang of Ubuntu and well I need more coffee now. ;)
 
ffmpeg -i JUMPER_PS1.vob -acodec libfaac -ab 96k -vcodec libx264 -vpre hq -crf 22 -threads 0 jumper.mp4
FFmpeg version SVN-r20654, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  built on Nov 29 2009 02:06:24 with gcc 4.4.1
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libx264 --enable-libxvid --enable-x11grab --enable-libvorbis
  libavutil     50. 5. 1 / 50. 5. 1
  libavcodec    52.42. 0 / 52.42. 0
  libavformat   52.39. 2 / 52.39. 2
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0. 7. 2 /  0. 7. 2
[mpeg @ 0x1cf83c0]max_analyze_duration reached
Input #0, mpeg, from 'JUMPER_PS1.vob':
  Duration: 01:28:27.10, start: 0.211444, bitrate: 6000 kb/s
    Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 720x480 [PAR 8:9 DAR 4:3], 9800 kb/s, 59.94 tbr, 90k tbn, 59.94 tbc
    Stream #0.1[0x20]: Subtitle: dvdsub
    Stream #0.2[0x21]: Subtitle: dvdsub
    Stream #0.3[0x22]: Subtitle: dvdsub
    Stream #0.4[0x23]: Subtitle: dvdsub
    Stream #0.5[0x80]: Audio: ac3, 48000 Hz, 5.1, s16, 448 kb/s
    Stream #0.6[0x81]: Audio: ac3, 48000 Hz, stereo, s16, 192 kb/s
    Stream #0.7[0x82]: Audio: ac3, 48000 Hz, stereo, s16, 192 kb/s
    Stream #0.8[0x83]: Audio: ac3, 48000 Hz, stereo, s16, 192 kb/s
File 'jumper.mp4' already exists. Overwrite ? [y/N] y
[libx264 @ 0x1dd74c0]using SAR=8/9
[libx264 @ 0x1dd74c0]using cpu capabilities: MMX2 SSE2Fast FastShuffle SSEMisalign LZCNT
[libx264 @ 0x1dd74c0]profile High, level 3.1
[mp4 @ 0x1d1fb10]track 1: output format does not support sample rate 48000hz
Output #0, mp4, to 'jumper.mp4':
    Stream #0.0: Video: libx264, yuv420p, 720x480 [PAR 8:9 DAR 4:3], q=10-51, 200 kb/s, 60k tbn, 59.94 tbc
    Stream #0.1: Audio: aac, 48000 Hz, stereo, s16, 96 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.5 -> #0.1
Could not write header for output file #0 (incorrect codec parameters ?)

---

### Post by fluffman86 on 2009-11-30
You are really going about this the hard way.  [http://handbrake.fr](http://handbrake.fr)

---

### Post by kadeous on 2009-11-30
I tried to install that but it wouldn't run HandBreakCLI command not found, compiled from source and everything looked like it installed fine. If I could get a how to in ubuntu for that It would be greatly appreciated; however I couldn't find one. My brain is mush atm lol
 
Edit: I followed thier example on the wiki there with no luck

---

### Post by kadeous on 2009-11-30
I got handbrake working now.. I was spelling it break lmao... shewww this stuff is eating my brain alive.

---

