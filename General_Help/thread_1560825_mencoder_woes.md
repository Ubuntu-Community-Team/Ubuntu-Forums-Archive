---
title: "mencoder woes"
date: 2010-08-25
forum: General Help
---

### Post by shortridge11 on 2010-08-25
I'm using mencoder on 10.04 to transcode mkv to avi. At for most files i have no problem, but a few of them give me error codes. So then i tried following this guide
[http://www.howforge.com/how-to-convert-mkv-to-avi-using-mencoder](http://www.howforge.com/how-to-convert-mkv-to-avi-using-mencoder)
But that didn't work.  Any ideas how i can examine the files i have to figure out what flags to use for converting?
1st command used
```
mencoder -mc 0 -noskip -vf expand=:::::16/9,scale=720:480,hqdn3d,harddup -ovc xvid -oac mp3lame -xvidencopts fixed_quant=3.8:me_quality=6:noqpel:nogmc:trellis:chroma_me:chroma_opt:hq_ac:vhq=4:lumi_mask:max_key_interval=300:quant_type=mpeg:max_bframes=2:closed_gop:nopacked:profile=asp5:autoaspect:bvhq=1 -lameopts vbr=2:q=6:aq=2 -o newfile.avi file.mkv

```

The second one i used was a script from a tutorial
```
#!/bin/sh

INPUT=$1
OUTPUT=$2

mplayer "$INPUT" -ao pcm:fast:file=audio.wav -vc null -vo null
mencoder "$INPUT" \
    -ffourcc divx \
    -ovc lavc -lavcopts vcodec=mpeg4:vhq:vbitrate=400 \
    -audiofile audio.wav \
    -oac mp3lame -lameopts vbr=3 \
    -slang eng \
    -sws 2 -vf scale=352:-3 \
    -o "$OUTPUT"

rm -f audio.wav

```
The error i got when running the first command was 
```
Too many audio packets in the buffer: (4096 in 8255101 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
```

The error i got with the second command was duplicate frames and Error while decoding frame. I tried using the -ni flag in mencoder but that didn't have any visible effect. Any ideas?

---

### Post by inameiname on 2010-08-25
Here's the script I use. I'll attach it too. Works just fine. However, it uses ffmpeg.

```

#!/usr/bin/python
# Little script to depack Matroska file, and repack them
# in a AVI + subtitle format.

import sys
import os

def message(msg):
    print "=" * 78
    print "= %s" % msg
    print "=" * 78

def usage():
    print "Mastroka repacker script"
    print "  Usage: "+sys.argv[0]+ " filename"

if __name__ == "__main__":
    if len(sys.argv) < 2:
        usage()
    else:
        filename = sys.argv[1]
        basename = filename[:-4]

        message("Unpacking file: %s" % filename)
        os.system("mkvextract tracks %s 1:temp_video.avi 2:temp_audio.ogg 3:%s.srt" % (filename,basename) )

        message("Repacking file: %s.avi" % basename)
        os.system("ffmpeg -i temp_audio.ogg  -i temp_video.avi  -vcodec copy  %s.avi" % (basename) )

        message("Cleaning files")
        os.system("rm temp_video.avi temp_audio.ogg")

```

---

### Post by shortridge11 on 2010-08-25
attempted to use script
```
xxx@xxxx:/foo/bar$ mkv2avi foo.mkv
==============================================================================
= Unpacking file: foo.mkv
==============================================================================
sh: mkvextract: not found
==============================================================================
= Repacking file: foo.avi
==============================================================================
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:41:55, gcc: 4.4.3
temp_audio.ogg: no such file or directory
==============================================================================
= Cleaning files
==============================================================================
rm: cannot remove `temp_video.avi': No such file or directory
rm: cannot remove `temp_audio.ogg': No such file or directory
xxx@xxxx:/foo/bar$

```

Am i missing ogg or something?

---

### Post by luigi_mb on 2010-08-25
Install (Synaptic) "mkvtoolnix". 

/luigi

---

### Post by inameiname on 2010-08-25
I don't really know. I've never had an issue with it. I think what it does is it extracts the audio and video from the mkv file, which has ogg audio and avi video, and repacks it into avi. So regarding your ogg concern, just seems as though it wasn't finding the audio. Of course, if it didn't have audio to begin with, maybe that's why. Still should have made the avi though if that was the case. So idk. It's possible your version of ffmpeg just isn't capable for converting mkv to avi. I know the ffmpeg that comes with Ubuntu is limited and lacks a lot of things (due to non-free stuff not being added) the full ffmpeg has that you can get in PPAs. I have the latter so maybe that's why.

Perhaps you should try luigi_mb's option.

---

### Post by shortridge11 on 2010-08-25
installing that last package seems to be doing the trick. I'll let you know how it goes after the conversion

---

### Post by inameiname on 2010-08-25
The last package?

---

### Post by shortridge11 on 2010-08-25
> **luigi_mb said:**
> Install (Synaptic) "mkvtoolnix". 

/luigi

this one

---

### Post by inameiname on 2010-08-25
OH...gotcha.

---

