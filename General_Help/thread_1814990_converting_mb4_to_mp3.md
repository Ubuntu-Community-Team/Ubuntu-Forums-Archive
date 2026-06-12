---
title: "converting mb4 to mp3"
date: 2011-07-30
forum: General Help
---

### Post by Gr.Turtle on 2011-07-30
I am trying to take some audio books on a trip and play them off my phone, tried using sound converter but i keep getting a g streamer error. I'm not sure of the syntax I should be using to convert a bunch of files with this command
```
for m4b in $(ls -1 *.m4b); do ffmpeg -i $m4b -acodec libmp3lame -ar 22050 ${m4b}.mp3; done
```
for any help I am grateful.

---

### Post by dog-soldier on 2011-07-30
i have never done this , but this is what i found with google
[http://intuitivenipple.net/10/converting-mp3s-to-m4b-audiobooks-and-m4b-to-mp3](http://intuitivenipple.net/10/converting-mp3s-to-m4b-audiobooks-and-m4b-to-mp3)

---

### Post by Gr.Turtle on 2011-07-30
> **dog-soldier said:**
> i have never done this , but this is what i found with google
[http://intuitivenipple.net/10/converting-mp3s-to-m4b-audiobooks-and-m4b-to-mp3](http://intuitivenipple.net/10/converting-mp3s-to-m4b-audiobooks-and-m4b-to-mp3)


that is the code I was listing above, but I don't know how to enter the filenames properly, I tried this syntax for a single file

```
ffmpeg -i '/home/turtle/Music/Song/thrones/A Game of Thrones A Song of Ice and Fire, Book I (Part 1 of 3).m4b'   -acodec libmp3lame -ab 320k '/home/turtle/Music/Song/thrones/A Game of Thrones A Song of Ice and Fire, Book I (Part 1 of 3).mp3'

```

got this in response

```
FFmpeg version 0.6.2-4:0.6.2-1ubuntu1, Copyright (c) 2000-2010 the Libav developers
  built on Mar 22 2011 15:35:22 with gcc 4.5.2
  configuration: --extra-version=4:0.6.2-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  WARNING: library configuration mismatch
  libavutil   configuration: --extra-version=4:0.6.2-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavcodec  configuration: --extra-version=4:0.6.2-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavformat configuration: --extra-version=4:0.6.2-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavdevice configuration: --extra-version=4:0.6.2-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavfilter configuration: --extra-version=4:0.6.2-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libswscale  configuration: --extra-version=4:0.6.2-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libpostproc configuration: --extra-version=4:0.6.2-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavutil     50.15. 1 / 50.15. 1
  libavcodec    52.72. 2 / 52.72. 2
  libavformat   52.64. 2 / 52.64. 2
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.19. 0 /  1.19. 0
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x848d420]max_analyze_duration reached
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '/home/turtle/Music/Song/thrones/A Game of Thrones A Song of Ice and Fire, Book I (Part 1 of 3).m4b':
  Metadata:
    major_brand     : M4A 
    minor_version   : 0
    compatible_brands: M4A mp42isom
    title           : A Game of Thrones: A Song of Ice and Fire, Book I (Part 1 of 3)
    artist          : George R. R. Martin
    album           : A Game of Thrones: A Song of Ice and Fire, Book I
    genre           : Audiobook
    track           : 1
    encoder         : ChapterMark (1.2.4)
    date            : 1996
  Duration: 11:00:35.67, start: 0.000000, bitrate: 111 kb/s
    Chapter #0.0: start 0.000000, end 1473.073152
    Metadata:
      title           : Chapter 00 - Prologue
    Chapter #0.1: start 1473.073152, end 2599.658141
    Metadata:
      title           : Chapter 01 - Bran
    Chapter #0.2: start 2599.658141, end 3378.710068
    Metadata:
      title           : Chapter 02 - Catelyn
    Chapter #0.3: start 3378.710068, end 5004.834649
    Metadata:
      title           : Chapter 03 - Daenerys
    Chapter #0.4: start 5004.834649, end 6448.493923
    Metadata:
      title           : Chapter 04 - Eddard
    Chapter #0.5: start 6448.493923, end 7648.979320
    Metadata:
      title           : Chapter 05 - Jon
    Chapter #0.6: start 7648.979320, end 8989.010839
    Metadata:
      title           : Chapter 06 - Catelyn
    Chapter #0.7: start 8989.010839, end 10014.606440
    Metadata:
      title           : Chapter 07 - Arya
    Chapter #0.8: start 10014.606440, end 11384.992245
    Metadata:
      title           : Chapter 08 - Bran
    Chapter #0.9: start 11384.992245, end 12212.867029
    Metadata:
      title           : Chapter 09 - Tyrion
    Chapter #0.10: start 12212.867029, end 13008.036508
    Metadata:
      title           : Chapter 10 - Jon
    Chapter #0.11: start 13008.036508, end 14622.118639
    Metadata:
      title           : Chapter 11 - Daenerys
    Chapter #0.12: start 14622.118639, end 15911.681587
    Metadata:
      title           : Chapter 12 - Eddard
    Chapter #0.13: start 15911.681587, end 17395.726168
    Metadata:
      title           : Chapter 13 - Tyrion
    Chapter #0.14: start 17395.726168, end 18946.200136
    Metadata:
      title           : Chapter 14 - Catelyn
    Chapter #0.15: start 18946.200136, end 20883.103492
    Metadata:
      title           : Chapter 15 - Sansa
    Chapter #0.16: start 20883.103492, end 21822.155420
    Metadata:
      title           : Chapter 16 - Eddard
    Chapter #0.17: start 21822.155420, end 22508.995102
    Metadata:
      title           : Chapter 17 - Bran
    Chapter #0.18: start 22508.995102, end 24144.784989
    Metadata:
      title           : Chapter 18 - Catelyn
    Chapter #0.19: start 24144.784989, end 26146.759365
    Metadata:
      title           : Chapter 19 - Jon
    Chapter #0.20: start 26146.759365, end 28131.858639
    Metadata:
      title           : Chapter 20 - Eddard
    Chapter #0.21: start 28131.858639, end 29860.801179
    Metadata:
      title           : Chapter 21 - Tyrion
    Chapter #0.22: start 29860.801179, end 31425.668617
    Metadata:
      title           : Chapter 22 - Arya
    Chapter #0.23: start 31425.668617, end 33189.040544
    Metadata:
      title           : Chapter 23 - Daenerys
    Chapter #0.24: start 33189.040544, end 35112.934921
    Metadata:
      title           : Chapter 24 - Bran
    Chapter #0.25: start 35112.934921, end 36497.008889
    Metadata:
      title           : Chapter 25 - Eddard
    Chapter #0.26: start 36497.008889, end 38385.820816
    Metadata:
      title           : Chapter 26 - Jon
    Chapter #0.27: start 38385.820816, end 39635.191905
    Metadata:
      title           : Chapter 27 - Eddard
    Chapter #0.28: start 39635.191905, end 39635.441905
    Metadata:
      title           : Chapter 27 - Eddard
    Stream #0.0(eng): Audio: aac, 44100 Hz, stereo, s16, 110 kb/s
    Stream #0.1(und): Subtitle: text / 0x74786574
Unknown encoder 'libmp3lame'
```

the final line may be the most relevant
```
Unknown encoder 'libmp3lame
```

---

### Post by Gr.Turtle on 2011-07-30
I am at a complete lost as to listing multiple files using the code from my first post
```

for m4b in $(ls -1 *.m4b); do ffmpeg -i $m4b -acodec libmp3lame -ar 22050 ${m4b}.mp3; done
```

---

### Post by Gr.Turtle on 2011-07-30
apparently simply changing the file name from .mb4 to .mba or .mp3 works. hahahaha.

---

### Post by frytek on 2011-08-01
Try this one, nice and with many options (e.g. speed, pauses length, equalizer, splitting): [http://audina.polip.com/](http://audina.polip.com/)

audina is just a converter. a script is included (audina_nokia) for making nokia audiobook format. the script audina_nokia is in Polish, but audina itself is in English.

---

### Post by lordievader on 2011-08-01
Are you trying to convert a .m4b to an .mp3 file, am I correct in that?
I have done it the other way around, let me see if I can convert it back. 

Okay first up install some codecs:
```
sudo apt-get install mplayer lame faac ffmpeg id3v2
```

Then we take two steps to convert the file,
First we convert the m4a (is quite the same as m4b) to a wav file.
And then we convert this wav file to a mp3 file.

So the first step, renaming the extension.
Change to the right directory using the command 'cd', then rename the file:
```
mv [name of the file].m4b [name of the file].m4a
```

Then the conversion to wav:
```
mplayer -ao pcm [name of file].m4a -ao pcm:file=[name of file].wav
```

And now the conversion to mp3:
```
lame [name of file].wav [name of file].mp3
```

And to clean it up a little bit:
```
rm [name of file].wav
```

Hope this helps, and with problems, ask!

---

### Post by capleton on 2012-08-11
so for anyone reading this, you can also do
```
avconv -i some/file.mb4 some/file.mp3
```

---

### Post by uRock on 2012-08-11
Thanks for sharing.

Old thread

Thread Closed

---

