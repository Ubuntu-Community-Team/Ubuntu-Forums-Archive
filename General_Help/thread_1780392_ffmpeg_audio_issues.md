---
title: "ffmpeg audio issues"
date: 2011-06-11
forum: General Help
---

### Post by davidstoll on 2011-06-11
I thought I just posted this, but for some reason it got deleted or something...?

Anyway, I'm having trouble with ffmpeg.  I'm running MythBuntu 10.10 32bit.  When I try to convert a file created by cat'ing my Hauppauge HDPVR video recorder, it creates a x264 video file with aac audio.

When I use ffmpeg to convert it to an mpeg 2 with ac3, the audio is muted.  mediainfo shows that it is there, but I get no sound.  I've even tried with other computers (even Windows).

If I try to encode as mp3, I get mpeg audio even though it says it's encoding with libmp3lame.  Normally, if the audio is mp3, it would have some kind of reference to mp3.

If I try to re-encode with aac (libfaac), I also get mpeg audio.

I used the ffmpeg and x264 thread in this forum to compile it, but it doesn't seem to help (and also adds other quirky things that I'm not used to...other minor errors and it just seems more touchy).

Lastly, I tried mencoder and I get similar results.

Can anyone help me figure out what I'm missing?

---

### Post by andrew.46 on 2011-06-12
Can you give the full commandline you have used and the complete, uncut terminal output? This will make it a lot easier to see what is going on and hopefully suggest a fix :)

---

### Post by Elfy on 2011-06-12
> **davidstoll said:**
> I thought I just posted this, but for some reason it got deleted or something...?You did - you posted in Tutorials and Tips - threads there are moderated until approved by staff. It's a forum to put tutorials etc for other users rather than questions. Anyway I closed it now that you made this one.

---

### Post by davidstoll on 2011-06-12
sure...by the way, I've used ffmpeg for years and have not had this kind of trouble before...something strange is going on.

I am currently using the latest from git (as of a day or two ago).

In all of these I use the -ss and -t to make it complete faster, but I have allowed them to do a complete conversion too.


Since this is the most important situation that I want to get working, I'll use this example.  MediaInfo shows it has AC3 in the out.mpg, but it is muted.
```

$ ffmpeg -i test.mp4 -acodec ac3 -vcodec copy out.mpg 
ffmpeg version git-N-30720-g7aa5947, Copyright (c) 2000-2011 the FFmpeg developers
  built on Jun 11 2011 01:37:14 with gcc 4.4.5
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libx264 --enable-libxvid --enable-x11grab --enable-libvpx
  libavutil    51.  8. 0 / 51.  8. 0
  libavcodec   53.  7. 0 / 53.  7. 0
  libavformat  53.  3. 1 / 53.  3. 1
  libavdevice  53.  1. 1 / 53.  1. 1
  libavfilter   2. 15. 0 /  2. 15. 0
  libswscale    0. 14. 1 /  0. 14. 1
  libpostproc  51.  2. 0 / 51.  2. 0
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'test.mp4':
  Metadata:
    major_brand     : isom
    minor_version   : 512
    compatible_brands: isomiso2avc1mp41
    creation_time   : 1970-01-01 00:00:00
    encoder         : Lavf52.64.2
  Duration: 00:45:00.01, start: 0.000000, bitrate: 6510 kb/s
    Stream #0.0(und): Video: h264 (Main), yuv420p, 1280x720 [PAR 1:1 DAR 16:9], 6370 kb/s, 59.94 fps, 59.94 tbr, 120k tbn, 119.88 tbc
    Metadata:
      creation_time   : 1970-01-01 00:00:00
    Stream #0.1(und): Audio: aac, 48000 Hz, stereo, s16, 127 kb/s
    Metadata:
      creation_time   : 1970-01-01 00:00:00
[mpeg @ 0x9f080c0] VBV buffer size not set, muxing may fail
Output #0, mpeg, to 'out.mpg':
  Metadata:
    major_brand     : isom
    minor_version   : 512
    compatible_brands: isomiso2avc1mp41
    creation_time   : 1970-01-01 00:00:00
    encoder         : Lavf53.3.1
    Stream #0.0(und): Video: libx264, yuv420p, 1280x720 [PAR 1:1 DAR 16:9], q=2-31, 6370 kb/s, 90k tbn, 59.94 tbc
    Metadata:
      creation_time   : 1970-01-01 00:00:00
    Stream #0.1(und): Audio: ac3, 48000 Hz, stereo, s16, 64 kb/s
    Metadata:
      creation_time   : 1970-01-01 00:00:00
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press [q] to stop, [?] for help
frame=161837 fps=2300 q=-1.0 Lsize= 2130604kB time=00:44:59.98 bitrate=6464.5kbits/s    
video:2099528kB audio:21094kB global headers:0kB muxing overhead 0.470722%

```




> **andrew.46 said:**
> Can you give the full commandline you have used and the complete, uncut terminal output? This will make it a lot easier to see what is going on and hopefully suggest a fix :)

---

### Post by andrew.46 on 2011-06-13
Looks like the conversion has no problems although I am not sure about this:

```

[mpeg @ 0x9f080c0] VBV buffer size not set, muxing may fail

```

Does the output file play with ffplay? Perhaps try a different container as well, mkv might be a decent test. And worth trying to play with MPlayer...

---

### Post by davidstoll on 2011-06-13
Hmmm, nice call with the mkv container.  Yes, it plays just fine.  So, it's something with the mpg container.  Any chance I'm missing something on the command line that I should have included?

For what I'm playing it on/with and what I'm using it for, I really need mpg.


> **andrew.46 said:**
> Looks like the conversion has no problems although I am not sure about this:

```

[mpeg @ 0x9f080c0] VBV buffer size not set, muxing may fail

```

Does the output file play with ffplay? Perhaps try a different container as well, mkv might be a decent test. And worth trying to play with MPlayer...

---

### Post by andrew.46 on 2011-06-14
> **davidstoll said:**
> Hmmm, nice call with the mkv container.  Yes, it plays just fine.  So, it's something with the mpg container.  Any chance I'm missing something on the command line that I should have included?

For what I'm playing it on/with and what I'm using it for, I really need mpg.

I believe that mpg cannot actually contain ac3 sound, hence failure to playback audio, whereas a matroska container will pretty much hold anything :). For mpg the FFmpeg audio default is actually mp2, could you simply use this?

---

### Post by davidstoll on 2011-06-14
> **andrew.46 said:**
> I believe that mpg cannot actually contain ac3 sound, hence failure to playback audio, whereas a matroska container will pretty much hold anything :). For mpg the FFmpeg audio default is actually mp2, could you simply use this?

Actually, MythTV seems to record in mpg with 2 and 6 channel ac3.  I just checked a couple and I found some with two 6 channel ac3 audio streams (english & spanish).

I'm thinking it is some kind of command line switch that I need to help it integrate correctly, but of course, that is just a guess.

Normally I call -vcodec mpeg2video, but at one point in the last few years, some other switches were required to get that codec to work properly...as I recall...?

---

### Post by andrew.46 on 2011-06-15
I have to confess that I am at a bit of a loss, and also with absolutely no knowledge about MythTV as well :(. The page I usually consult about container formats:

Comparison of container formats
[http://en.wikipedia.org/wiki/Comparison_of_container_formats](http://en.wikipedia.org/wiki/Comparison_of_container_formats)

seems to suggest that .mpg files are quite limited in the codecs that they can contain, which is certainly confirmed in a few experiments I have made on my system. So I have to declare my complete failure to be of assistance here and hope that some more knowledgeable person can be of assistance...

**Edit:** Oddly enough FFplay will happily playback an mpg with ac3 sound but MPlayer barfs, so I am doubly not sure. Must be time to call in the cavalry....

---

### Post by FakeOutdoorsman on 2011-06-15
> **davidstoll said:**
> When I try to convert a file created by cat'ing my Hauppauge HDPVR video recorder, it creates a x264 video file with aac audio.
Your original post is confusing me. Are you saying your cat dump from the Hauppauge produces a file with H.264 video and AAC audio?

> **davidstoll said:**
> When I use ffmpeg to convert it to an mpeg 2 with ac3, the audio is muted.
You mention "mpeg 2", but the only FFmpeg command and output you provided is creating an output with H.264 video and AC3 audio in mpg container. Is this what you are wanting? I've never encountered this combination of formats in mpg before.

> **davidstoll said:**
> If I try to encode as mp3, I get mpeg audio even though it says it's encoding with libmp3lame.  Normally, if the audio is mp3, it would have some kind of reference to mp3.
I'm sorry, but I'm not sure what you mean here. The best way to explain this would be to provide your command and the complete output. I thought you required AC3?

> **davidstoll said:**
> I used the ffmpeg and x264 thread in this forum to compile it, but it doesn't seem to help (and also adds other quirky things that I'm not used to...other minor errors and it just seems more touchy).
What kind of errors?

> **davidstoll said:**
> For what I'm playing it on/with and what I'm using it for, I really need mpg.
What are you playing this on? If you require mpg container why not use the typical video and audio formats that are usually used for this container?  Example:
```
ffmpeg -i input -vcodec mpeg2video -qscale 4 -ab 128k output.mpg
```

> **davidstoll said:**
> Actually, MythTV seems to record in mpg with 2 and 6 channel ac3.  I just checked a couple and I found some with two 6 channel ac3 audio streams (english & spanish).
Can you show the FFmpeg output of one of these files that MythTV produces that contain the AC3 audio?
```
ffmpeg -i input_from_mythtv.foo
```

> **andrew.46 said:**
> I have to confess that I am at a bit of a loss, and also with absolutely no knowledge about MythTV as well :(.
I too know nothing of MythTV.

> **andrew.46 said:**
> Must be time to call in the cavalry....
But you're the cavalry.

---

### Post by davidstoll on 2011-06-16
Sorry, I would have posted sooner, but I did not get notified of a new response to this thread...that sometimes happens...hmmm.


> **FakeOutdoorsman said:**
> Your original post is confusing me. Are you saying your cat dump from the Hauppauge produces a file with H.264 video and AAC audio?

Correct.  By default, the device outputs H.264 and AAC.

> **FakeOutdoorsman said:**
> 
Can you show the FFmpeg output of one of these files that MythTV produces that contain the AC3 audio?
```
ffmpeg -i input_from_mythtv.foo
```



$ ffmpeg -i /mythtv/recordings/1171_20110616153000.mpg
ffmpeg version git-N-30720-g7aa5947, Copyright (c) 2000-2011 the FFmpeg developers
  built on Jun 11 2011 01:37:14 with gcc 4.4.5
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libx264 --enable-libxvid --enable-x11grab --enable-libvpx
  libavutil    51.  8. 0 / 51.  8. 0
  libavcodec   53.  7. 0 / 53.  7. 0
  libavformat  53.  3. 1 / 53.  3. 1
  libavdevice  53.  1. 1 / 53.  1. 1
  libavfilter   2. 15. 0 /  2. 15. 0
  libswscale    0. 14. 1 /  0. 14. 1
  libpostproc  51.  2. 0 / 51.  2. 0
[mpegts @ 0xa70d360] max_analyze_duration 5000000 reached at 5024000
Input #0, mpegts, from '/mythtv/recordings/1171_20110616153000.mpg':
  Duration: 00:30:56.13, start: 59665.128544, bitrate: 6828 kb/s
  Program 1 
    Stream #0.0[0x31]: Video: mpeg2video (Main), yuv420p, 1280x720 [PAR 1:1 DAR 16:9], 15980 kb/s, 59.96 fps, 59.94 tbr, 90k tbn, 119.88 tbc
    Stream #0.1[0x34](eng): Audio: ac3, 48000 Hz, 5.1, s16, 448 kb/s
    Stream #0.2[0x35](spa): Audio: ac3, 48000 Hz, stereo, s16, 192 kb/s

---

