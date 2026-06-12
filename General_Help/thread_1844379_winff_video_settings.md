---
title: "winff video settings"
date: 2011-09-15
forum: General Help
---

### Post by cowboy7305 on 2011-09-15
[http://ubuntuforums.org/attachment.php?attachmentid=202209&stc=1&d=1316064816](http://ubuntuforums.org/attachment.php?attachmentid=202209&stc=1&d=1316064816)
i hope this works 
if it has good 
want to use the settings  in winff to convert vids to my player any help on doing this would be a great help ,i know this is the right settings thy came with the player but the converter only works on windows ,and this is the settings that show up on vid properties

---

### Post by TeoBigusGeekus on 2011-09-15
If these are the desired settings for the output video, then do it with ffmpeg:
```
ffmpeg -i /path/inputvideo.extension -vcodec mpeg4 -vtag xvid -r 15 -s 160x128 -acodec libmp3lame -ab 128k -ar 44100 -ac 2 outputvideo.avi
```

---

### Post by cowboy7305 on 2011-09-15
is there no program that can do this for me with , no way to use winff,i can never understand how to work codes in terminal

---

### Post by dniMretsaM on 2011-09-15
> **cowboy7305 said:**
> is there no program that can do this for me with , no way to use winff,i can never understand how to work codes in terminal

WinFF is just a graphical front-end for FFmpeg, so it's probably possible. I'll explore it some and get back to you. In the mean time, simply open up Terminal, copy -> paste the code in, and press Enter

---

### Post by cowboy7305 on 2011-09-15
tried that 
tied
cant find that eather putting in where the files are /mine/dwhelper/movie.flv
cant find them 
that is part of the code where it says where the files are

---

### Post by dniMretsaM on 2011-09-15
Try this:
(1) Open up WinFF (duh). There are two drop down menus. Select "AVI" on the first one and "XviD FullScreen" on the second.

(2) Now click the "Options" button in the upper right. A new section will appear at the bottom of the screen with a few tabs on it.

(3) On the "Video" tab, there is a section called "Frame Rate." Enter "15" in there. In "Video Size," put "160" in the first box and "128" in the second.

(3) In the next tab. "Audio," enter "128" in "Audio Bitrate," "44100" in "Sample Rate," and "2" in "Audio Channels."

(4) Now you can add the videos you want to convert and choose the path to save them to. Hit "Convert" and your on your way.

That should be it. If that doesn't work, let me know what errors you get. I don't have too much experience with WinFF (I use FFmpeg's CLI most of the time). Good luck.

---

### Post by cowboy7305 on 2011-09-15
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1.1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1.1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar 31 2011 18:53:20, gcc: 4.4.3

Seems stream 0 codec frame rate differs from container frame rate: 2000.00 (2000/1) -> 25.00 (25/1)
Input #0, flv, from '/home/mine/dwhelper/144102.flv':
  Duration: 00:03:00.03, start: 0.000000, bitrate: 661 kb/s
    Stream #0.0: Video: h264, yuv420p, 512x288 [PAR 1:1 DAR 16:9], 501 kb/s, 25 tbr, 1k tbn, 2k tbc
    Stream #0.1: Audio: mp3, 44100 Hz, stereo, s16, 160 kb/s
/usr/bin/ffmpeg: unrecognized option '--ac'
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1.1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1.1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar 31 2011 18:53:20, gcc: 4.4.3

Seems stream 0 codec frame rate differs from container frame rate: 2000.00 (2000/1) -> 25.00 (25/1)
Input #0, flv, from '/home/mine/dwhelper/144102.flv':
  Duration: 00:03:00.03, start: 0.000000, bitrate: 661 kb/s
    Stream #0.0: Video: h264, yuv420p, 512x288 [PAR 1:1 DAR 16:9], 501 kb/s, 25 tbr, 1k tbn, 2k tbc
    Stream #0.1: Audio: mp3, 44100 Hz, stereo, s16, 160 kb/s
/usr/bin/ffmpeg: unrecognized option '--ac'
Press Enter to Continue

got this message while doing it via  winff
and when i tried doing it by code which did work but  my player said wrong file formate the differences were

converted by windows
 MPEG 1 Audio, Layer 2
the new code set this as 
MPEG 1 Audio, Layer 3 (MP3)

---

### Post by dniMretsaM on 2011-09-15
> **cowboy7305 said:**
> /usr/bin/ffmpeg: unrecognized option '--ac'
Press Enter to Continue

got this message while doing it via  winff

Ok, I really have no idea where it's getting '--ac' from. It's supposed to be '-ac' so maybe it's a bug in the WinFF code.

> **cowboy7305 said:**
> and when i tried doing it by code which did work but  my player said wrong file formate the differences were

converted by windows
 MPEG 1 Audio, Layer 2
the new code set this as 
MPEG 1 Audio, Layer 3 (MP3)

TeoBigusGeekus used the codec 'libmp3lame' in his FFmpeg code which is what caused that problem. Not sure what the correct one would be. I'll do some digging and see what I can find.

EDIT: Ok, I found the libtwolame codec. So try copy -> paste this into Terminal and see if it works:
```
ffmpeg -i /path/inputvideo.extension -vcodec mpeg4 -vtag xvid -r 15 -s 160x128 -acodec libtwolame -ab 128k -ar 44100 -ac 2 outputvideo.avi
```

---

### Post by FakeOutdoorsman on 2011-09-15
FFmpeg has a MPEG-1 Audio Layer II encoder. Change "-acodec libmp3lame" to "-acodec mp2". I don't think FFmpeg supports twolame.

---

### Post by dniMretsaM on 2011-09-15
> **FakeOutdoorsman said:**
> FFmpeg has a MPEG-1 Audio Layer II encoder. Change "-acodec libmp3lame" to "-acodec mp2". I don't think FFmpeg supports twolame.

Oh ok I didn't know that. Why is this?

---

### Post by cowboy7305 on 2011-09-15
Many thanks for trying

---

### Post by FakeOutdoorsman on 2011-09-15
> **dniMretsaM said:**
> Oh ok I didn't know that. Why is this?
I'm not sure. I guess the simple answer might be that nobody was ever interested in developing a twolame wrapper for FFmpeg (although I think MEncoder is able to encode with it). You can still use ffmpeg to pipe from just about any audio format to twolame:
```
ffmpeg -i IronMan.mkv -f wav - | twolame - -r out.mp2
```

---

### Post by dniMretsaM on 2011-09-15
> **FakeOutdoorsman said:**
> I'm not sure. I guess the simple answer might be that nobody was ever interested in developing a twolame wrapper for FFmpeg (although I think MEncoder is able to encode with it). You can still use ffmpeg to pipe from just about any audio format to twolame:
```
ffmpeg -i IronMan.mkv -f wav - | twolame - -r out.mp2
```

Oh the beauty of pipes.

---

### Post by andrew.46 on 2011-09-17
> **FakeOutdoorsman said:**
> I'm not sure. I guess the simple answer might be that nobody was ever interested in developing a twolame wrapper for FFmpeg (although I think MEncoder is able to encode with it).

I will admit that I have not used it but certainly MEncoder does seem to have that ability:

```

andrew@skamandros~$ mencoder -oac help
MEncoder SVN-r34110-4.5.2 (C) 2000-2011 MPlayer Team

Available codecs:
   copy     - frame copy, without re-encoding (useful for AC3)
   pcm      - uncompressed PCM audio
   mp3lame  - cbr/abr/vbr MP3 using libmp3lame
   lavc     - FFmpeg audio encoder (MP2, AC3, ...)
**[COLOR="Red"]   twolame  - Twolame MP2 audio encoder[/COLOR]**
   faac     - FAAC AAC audio encoder

```

---

### Post by cowboy7305 on 2011-09-18
Ok i had a look and my synaptic says its loaded on the computer but i looked at the codes and says its not there 
have looked on net for twolame and there web site has no deb files for it only tar

---

### Post by cowboy7305 on 2011-09-19
~$ mencoder -oac help
MEncoder SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team

Available codecs:
   copy     - frame copy, without re-encoding (useful for AC3)
   pcm      - uncompressed PCM audio
   mp3lame  - cbr/abr/vbr MP3 using libmp3lame
   lavc     - FFmpeg audio encoder (MP2, AC3, ...)
   faac     - FAAC AAC audio encoder
This my out put to what codecs are on my computer 
but when i go to synaptic it tells me twolame is installed 
but its not showing up

---

### Post by andrew.46 on 2011-09-19
To get twolame output you must compile MPlayer/MEncoder against the twolame headers, which is what I have done. I believe that your best bet is to follow FakeOutdoorsman's advice and pipe the FFmpeg output to twolame, if you are really keen to use twolame...

---

### Post by cowboy7305 on 2011-09-19
pipe the FFmpeg output to twolame, 
how do i do that? 
sorry this has got me lost

---

### Post by andrew.46 on 2011-09-19
> **cowboy7305 said:**
> pipe the FFmpeg output to twolame, 
how do i do that? 
sorry this has got me lost

I should have linked to FakeOutdoorsman's post, sorry :(. Details [here]("http://ubuntuforums.org/showpost.php?p=11255058&postcount=12"). Below is an example of the syntax at work on my own computer:

```

andrew@skamandros~/Desktop$ **[COLOR="Red"]ffmpeg -i Bartók_4tet_1.ogg -f wav - | twolame - -r Bartók_4tet_1.mp2[/COLOR]**
---------------------------------------------------------
Input Filename: STDIN
Output Filename: Bartók_4tet_1.mp2
Raw input format: 2 channels, 16-bit, 44100 Hz
---------------------------------------------------------
[B][COLOR="Red"]LibTwoLame 0.3.13 (http://www.twolame.org)
Input : 44100 Hz, 2 channels
Output: 44100 Hz, Stereo
192 kbps CBR MPEG-1 Layer II psycho model=3 
[De-emph:Off     Copyright:No     Original:Yes]
[Padding:Off     CRC:Off          Energy:Off  ][/COLOR][/B]
---------------------------------------------------------
ffmpeg version N-32674-g9a9ceb8, Copyright (c) 2000-2011 the FFmpeg developers
  built on Sep 18 2011 07:55:46 with gcc 4.5.2
  configuration: --prefix=/usr --mandir=/usr/man --enable-postproc --enable-avfilter --enable-pthreads --enable-shared --disable-static --disable-ffserver --enable-libvorbis --enable-libmp3lame --enable-libx264 --enable-libfaac --enable-libvpx --enable-zlib --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libxvid --enable-libfreetype --enable-x11grab --enable-nonfree --enable-gpl --enable-version3
  libavutil    51. 16. 0 / 51. 16. 0
  libavcodec   53. 15. 0 / 53. 15. 0
  libavformat  53. 12. 0 / 53. 12. 0
  libavdevice  53.  4. 0 / 53.  4. 0
  libavfilter   2. 43. 0 /  2. 43. 0
  libswscale    2.  1. 0 /  2.  1. 0
  libpostproc  51.  2. 0 / 51.  2. 0
Input #0, ogg, from 'Bartók_4tet_1.ogg':
  Duration: 00:29:04.40, start: 0.000000, bitrate: 186 kb/s
    Stream #0.0: Audio: vorbis, 44100 Hz, stereo, s16, 192 kb/s
    Metadata:
      TITLE           : String Quartet no.1 op.7 (1908-1909)
      ARTIST          : Emerson String Quartet
      ALBUM           : Béla Bartók - 6 String Quartets
Output #0, wav, to 'pipe:':
  Metadata:
    encoder         : Lavf53.12.0
    Stream #0.0: Audio: pcm_s16le ([1][0][0][0] / 0x0001), 44100 Hz, stereo, s16, 1411 kb/s
    Metadata:
      TITLE           : String Quartet no.1 op.7 (1908-1909)
      ARTIST          : Emerson String Quartet
      ALBUM           : Béla Bartók - 6 String Quartets
Stream mapping:
  Stream #0.0 -> #0.0 (vorbis -> pcm_s16le)
Press [q] to stop, [?] for help
Encoding frame: 66760size=  300501kB time=00:29:04.40 bitrate=1411.2kbits/s    
video:0kB audio:300501kB global headers:0kB muxing overhead 0.000014%
Encoding frame: 66778
Encoding Finished.
Total bytes written: 39.87 MB.

```

---

