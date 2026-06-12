---
title: "GLC Will Not Encode"
date: 2011-08-19
forum: General Help
---

### Post by Joseph Schwenker on 2011-08-19
Though I've already figured out the commands to use from my previous thread of the same name, I'm having a problem encoding videos with glc now. I have been able to encode previously on this installation, but for some reason, whenever I run the command ```
glc-play video -y 1 -o - | ffmpeg -i - -sameq test.avi
``` to encode my videos, the encoder runs for a few seconds, then stops, outputting just a few seconds of the file. This is really frustrating as I just recorded for several hours, generating a large (~70GB) file that I'd like to compress, but am unable to. Here's the output.

```
joseph@joseph:~/Desktop$ glc-play video -y 1 -o - | ffmpeg -i - -sameq test.avi
FFmpeg version 0.6.2-4:0.6.2-1ubuntu1, Copyright (c) 2000-2010 the Libav developers
  built on Mar 22 2011 15:35:22 with gcc 4.5.2
  configuration: --extra-version=4:0.6.2-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  WARNING: library configuration mismatch
  libavutil   configuration: --extra-version=4:0.6.2-1ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libfaad --enable-libdirac --enable-libfaad --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavcodec  configuration: --extra-version=4:0.6.2-1ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libfaad --enable-libdirac --enable-libfaad --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
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
[yuv4mpegpipe @ 0x88abbc0]Estimating duration from bitrate, this may be inaccurate
Input #0, yuv4mpegpipe, from 'pipe:':
  Duration: N/A, bitrate: N/A
    Stream #0.0: Video: rawvideo, yuv420p, 426x240, 30 fps, 30 tbr, 30 tbn, 30 tbc
Output #0, avi, to 'test.avi':
  Metadata:
    ISFT            : Lavf52.64.2
    Stream #0.0: Video: mpeg4, yuv420p, 426x240, q=2-31, 200 kb/s, 30 tbn, 30 tbc
Stream mapping:
  Stream #0.0 -> #0.0
frame=  545 fps=  0 q=0.0 Lsize=    1084kB time=18.17 bitrate= 488.7kbits/s    
video:1065kB audio:0kB global headers:0kB muxing overhead 1.727547%
joseph@joseph:~/Desktop$ 
```

Perhaps the line "WARNING: library configuration mismatch" is why my problem is occurring. Unfortunately, not much information is provided in the output, so I can't really tell what libraries are misconfigured. Can anyone help? I'm using GLC on Ubuntu 11.04 32-bit.

---

### Post by Joseph Schwenker on 2011-08-20
The issue might be with ffmpeg, as [several]("http://askubuntu.com/questions/26169/warning-library-configuration-mismatch-when-running-ffmpeg") [other]("http://us.generation-nt.com/answer/bug-619530-ffmpeg-backport-4-0-6-1-5-unstable-produces-warning-library-configuration-mismatch-help-202676282.html") [people]("http://forums.clip-bucket.com/showthread.php?3562-ffmpeg-conversion-issue") see the same error (WARNING: library configuration mismatch), so the problem might be with ffmpeg and not glc.

---

### Post by Desti on 2011-08-21
Does enconding a normal file work? I don't think this message is the reason, but you could compile ffmpeg from source and IIRC it goes away then.

---

### Post by Joseph Schwenker on 2011-08-22
I asked around on #ubuntu on freenode and people were confused that the command worked in the first place. One guy reasoned that the short videos was the result of ffmpeg encoding faster than glc. He suggested that I try running the command without the pipe. I did so, but the file generated is more than twice the size of the original, and I killed it before its filesize got too out of control.
Also, how can I test encoding a "normal file"?

---

### Post by Desti on 2011-08-23
> **Joseph Schwenker said:**
> I asked around on #ubuntu on freenode and people were confused that the command worked in the first place. One guy reasoned that the short videos was the result of ffmpeg encoding faster than glc. He suggested that I try running the command without the pipe. I did so, but the file generated is more than twice the size of the original, and I killed it before its filesize got too out of control.
Also, how can I test encoding a &quot;normal file&quot;?

 Just test if encoding a standard video file works. Also, sameq is broken by design, if you don't use a lossless codec.

---

### Post by Joseph Schwenker on 2011-08-23
> **Desti said:**
> Just test if encoding a standard video file works. Also, sameq is broken by design, if you don't use a lossless codec.

Got a command I could use to encode a standard video file? I'm just using this command because it's worked well for me in the past. Is sameq broken if I'm going from a lossless, uncompressed codec, to a lossless, compressed one? It's worked before.

---

### Post by Desti on 2011-08-24
So does   ffmpeg -i a_video_file -sameq -an test.avi  work?

---

### Post by Joseph Schwenker on 2011-08-25
> **Desti said:**
> So does   ffmpeg -i a_video_file -sameq -an test.avi  work?

Just tried that command on an mp4 file, and it seemed to successfully encode the entire video's length, though there was no audio.
Since the glc file I'm trying to encode doesn't have audio, I'm going to manually sync audio with it from another source.

---

### Post by Desti on 2011-08-26
The option -an means audio_no, so your ffmpeg seems to work properly. I will test some things with glc in the next days and come back.

---

### Post by Joseph Schwenker on 2011-09-03
Have you finished testing things yet? I'd really like to free the whopping 30GB of disk space that my uncompressed video takes up.

---

### Post by Desti on 2011-09-03
Hi,  I was ill last days and I hope to get back OK in the next days.

---

### Post by Joseph Schwenker on 2011-09-04
> **Desti said:**
> Hi,  I was ill last days and I hope to get back OK in the next days.

Oh, alright. Get well soon!

---

### Post by Joseph Schwenker on 2011-09-08
I could really use some help with this now, as I have some outstanding video footage I'd like to upload to YouTube. Are you well enough yet to help me out?

---

### Post by Desti on 2011-09-10
Hi,  havn't forgot you and I will reserve some time on monday for it. :)  Have you tried to use mencoder instead of ffmpeg?

---

### Post by Joseph Schwenker on 2011-09-11
Actually, in the days while you were gone, I got help from a friend of mine who is experienced with glc, and he gave me a command that pipes to mencoder instead of ffmpeg.

```
glc-play video -y 1 -o - | mencoder -demuxer y4m - -ovc lavc -lavcopts vcodec=mpeg4:vqscale=2 -vf eq2=1.3 -o test.avi
```

This command works perfectly for me, though I only have one slight issue left, which is how to get mencoder to handle resolution changes in the glc video. Currently, when I try to encode a video that changes resolution halfway through, the video keeps the first resolution and crops out the rest of the video when the resolution changes. My friend proposed a solution for this: 

```
-vf scale=<width>:<height>
```

which I have yet to test, though I'll try to get around to it tomorrow. If that command doesn't fix that issue, I'll still need your help.

---

### Post by Desti on 2011-09-11
Ah, you recorded with changing window size, I need to check if this causes the problems. Normaly also your basic command should work. Try this little more detailed one and lock what  it gives you.  glc-play video.glc -y 1 -o - | ffmpeg -i - -vcodec libvpx -b 1M -r 30 -s 426x240 -an -threads 2 video.webm

---

### Post by Joseph Schwenker on 2011-09-11
I tried that command, but encoding stopped prematurely. When I encode with mencoder, everything works okay except the issue with the video being cropped out because I resized the window. I've yet to resolve that issue, and my friend's help didn't seem to do anything.

---

### Post by Desti on 2011-09-12
Do you have enough free disk space left? I think, you need first make the video to single frame pictures, then resize them all to the same size and then make a new video stream from them.

---

### Post by Joseph Schwenker on 2011-09-12
> **Desti said:**
> Do you have enough free disk space left?

I don't know. Will 615.8 GB be sufficient?

> **Desti said:**
> I think, you need first make the video to single frame pictures

How do I do that?

> **Desti said:**
> then resize them all to the same size

O_O

> **Desti said:**
> and then make a new video stream from them.

How do I do that??

---

### Post by Desti on 2011-09-12
Hi,  I can now confirm, that ffmpeg quits when trying to process a glc file with changing pixel size.  But I found an easy way to bypass it, we where looking at the wrong side for rescaling!  glc-play has it own rescale function, use it and it should work.  ```
 glc-play video.glc -r 400x200 -y 1 -o - | ffmpeg -i - -vcodec libvpx -b 500k -an -threads 2 video.webm 
```

---

### Post by Joseph Schwenker on 2011-09-12
> **Desti said:**
> Hi,  I can now confirm, that ffmpeg quits when trying to process a glc file with changing pixel size.  But I found an easy way to bypass it, we where looking at the wrong side for rescaling!  glc-play has it own rescale function, use it and it should work.  ```
 glc-play video.glc -r 400x200 -y 1 -o - | ffmpeg -i - -vcodec libvpx -b 500k -an -threads 2 video.webm 
```

Whoa! You just found the source of all my problems! Sweet! This also seems to have fixed my issue with premature quitting in ffmpeg as well as the rest of the video being cropped out in mencoder.
Thanks so much for your help!

---

