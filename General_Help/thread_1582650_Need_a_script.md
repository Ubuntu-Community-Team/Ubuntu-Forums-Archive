---
title: "Need a script"
date: 2010-09-26
forum: General Help
---

### Post by Colo2 on 2010-09-26
Hello. I need a script which I can execute in a particular directory full of .avi files. I need the script to convert all the .avi files within to .mp4 files. (using FFmpeg, I have that installed)

So does anyone know what script to use, so it automatically finds all the .avi files within, and converts them all, and outputs them to the same directory with the same name, just different extension

thanks :)

---

### Post by Colo2 on 2010-09-26
or something similar...

---

### Post by btindie on 2010-09-26
A basic script would look something like
```
#!/bin/sh
for AVI in $(find . -name '*.avi'); do
    MP4=${AVI%%avi}mp4
    ffmpeg -i $AVI $MP4
done
```
Save the script somewhere and make it executable. Change to the directory where your AVI's are stored then run it - /home/USERNAME/bin/avi-to-mp4
 
You may want to adjust the options to ffmpeg depending on what type of mp4 you want to create. Take a look [here]("http://www.catswhocode.com/blog/19-ffmpeg-commands-for-all-needs") for possible options.

---

### Post by amauk on 2010-09-26
take a look at ffmpeg's man page
there's a huge array of options possible
and the defaults may not be what you're looking for

not setting the video bitrate, for example, will mean it defaults to 200 kbps, which (depending on the resolution) may not be enough for any sort of decent quality

---

### Post by asmoore82 on 2010-09-26
> **btindie said:**
> A basic script would look something like
```
#!/bin/sh
for AVI in $(find . -name '*.avi'); do
    MP4=${AVI%%avi}mp4
    ffmpeg -i $AVI $MP4
done
```
This is close but the find is unnecessary and adds bugs -
like not being able to handle filenames with special characters or spaces.

It can be simplified to just this:
```
#!/bin/bash
for avifile in *.avi
do
    ffmpeg -i "$avifile" "${avifile%.avi}.mp4"
done
```
^also, in shell scripts, quotations are your friend!

---

### Post by SeijiSensei on 2010-09-26
> **asmoore82 said:**
> 
```
#!/bin/bash
for avifile in *.avi
do
    ffmpeg -i "$avifile" "${avifile%.avi}.mp4"
done
```

I've read a goodly chunk of "man bash", but there are always new things to learn.  I've often wondered how to strip an extension and rename a file.  In the past I've used sed to remove the extension and store the result in an environment variable. Now I've learned I can use the ${parameter%word} construction to do this very thing instead!  

Thanks a lot, asmoore82!

---

### Post by FakeOutdoorsman on 2010-09-27
I haven't tested this script, but I'll add some FFmpeg options to give a better output quality than the defaults:
```
#!/bin/bash
for avifile in *.avi
do
    ffmpeg -i "$avifile" -acodec libfaac -aq 100 -vcodec libx264 -vpre medium -crf 22 \
    -threads 0 -map_meta_data 0:0 "${avifile%.avi}.mp4"
done
```
Note that you will need to use a different *-vpre*, such as *-vpre hq*, if you are using an older FFmpeg.  You may also need to enable some encoders that are, by default, not present in the repository FFmpeg:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

---

### Post by Colo2 on 2010-09-27
Thank you all for your replies. I think this is exactly what I needed.

I'll know when I finish work :)

Take care!

Tom
:)

---

### Post by Colo2 on 2010-09-27
> **FakeOutdoorsman said:**
> I haven't tested this script, but I'll add some FFmpeg options to give a better output quality than the defaults:
```
#!/bin/bash
for avifile in *.avi
do
    ffmpeg -i "$avifile" -acodec libfaac -aq 100 -vcodec libx264 -vpre medium -crf 22 \
    -threads 0 -map_meta_data 0:0 "${avifile%.avi}.mp4"
done
```
Note that you will need to use a different *-vpre*, such as *-vpre hq*, if you are using an older FFmpeg.  You may also need to enable some encoders that are, by default, not present in the repository FFmpeg:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

Could someone tell me how to put in the iphone resolution in the params?

thanks

---

### Post by ron999 on 2010-09-27
Hi
Find out what resolution your iPhone has then add it to the script like this:-
```
#!/bin/bash
for avifile in *.avi
do
    ffmpeg -i "$avifile" -acodec libfaac -aq 100 -vcodec libx264 -vpre medium -crf 22 \
    -threads 0 [COLOR="Red"]-s 480x320[/COLOR] -map_meta_data 0:0 "${avifile%.avi}.mp4"
done
```

---

### Post by Colo2 on 2010-09-27
Thank you! :) I'm just going to try that now.

---

### Post by Colo2 on 2010-09-27
```
#!/bin/bash
for avifile in *.avi
do
    ffmpeg -i "$avifile" -acodec libfaac -aq 100 -vcodec libx264 -vpre medium -crf 22 \
    -threads 0 -s 480x320 -map_meta_data 0:0 "${avifile%.avi}.mp4"
done
```

> dump@STORAGE-DUMP:~/Desktop/file$ sh /home/dump/Desktop/AVI-MP4.sh
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:35:30, gcc: 4.4.3

Seems stream 0 codec frame rate differs from container frame rate: 23.98 (65535/2733) -> 23.98 (2997/125)
Input #0, avi, from 'codename.avi':
  Duration: 01:31:13.97, start: 0.000000, bitrate: 1075 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 592x320 [PAR 1:1 DAR 37:20], 23.98 tbr, 23.98 tbn, 23.98 tbc
    Stream #0.1: Audio: mp3, 48000 Hz, stereo, s16, 32 kb/s
File for preset 'medium' not found
dump@STORAGE-DUMP:~/Desktop/file$ 



:| Any ideas?

---

### Post by ron999 on 2010-09-27
> **Colo2 said:**
>  Any ideas?
Yes

From fakeoutdoorsman's post:-
> Note that you will need to use a different -vpre, such as -vpre hq, if you are using an older FFmpeg.


So look in the folder in /usr/local/share/ffmpeg.
There should be a list of presets in there.
Use one of them instead of medium.

---

### Post by Colo2 on 2010-09-27
In the FFpresets folder, there's just a load of .ffpreset files. Such as this one:

libx264-baseline.ffpreset & others.

What do I do with them?

---

### Post by ron999 on 2010-09-27
Are there ones such as these?
libx264-hq.ffpreset
libx264-normal.ffpreset
libx264-default.ffpreset

---

### Post by Colo2 on 2010-09-27
Ok. I found default, and added that instead of medium, now I'm getting:

> Unknown encoder 'libfaac'

---

### Post by ron999 on 2010-09-27
> **Colo2 said:**
> Ok. I found default, and added that instead of medium, now I'm getting:

Your aac encoder isn't enabled.

From fakeoutdoorsman's post again:-
> You may also need to enable some encoders that are, by default, not present in the repository FFmpeg:

HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg

Follow the advice in the thread here:-[http://ubuntuforums.org/showthread.php?t=1117283]("http://ubuntuforums.org/showthread.php?t=1117283")

---

### Post by Colo2 on 2010-09-27
> dump@STORAGE-DUMP:~/Desktop/file$ sudo apt-get install ffmpeg libavcodec-extra-52
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ffmpeg is already the newest version.
libavcodec-extra-52 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 51 not upgraded.
dump@STORAGE-DUMP:~/Desktop/file$ 


hmm :(

---

### Post by ron999 on 2010-09-27
Which operating system are you using?

---

### Post by Colo2 on 2010-09-27
Ubuntu 10.04

---

### Post by ron999 on 2010-09-27
OK
Go back to the link and use **option C) Medibuntu**.
Copy and paste the long command that starts like this:- sudo wget [http://www.medibuntu.org/sources.list](http://www.medibuntu.org/sources.list)...
Then afterwards paste in:-
```
sudo apt-get install ffmpeg libavcodec-extra-52
```

---

### Post by Colo2 on 2010-09-27
Fixed perfectly
Thank you loads for your help! :)

---

### Post by ron999 on 2010-09-27
Good.

Just test your script with one video first.
See if it looks OK and make sure that it plays in your iPhone.
:guitar:

---

### Post by Colo2 on 2010-09-27
> **ron999 said:**
> Good.

Just test your script with one video first.
See if it looks OK and make sure that it plays in your iPhone.
:guitar:

Yep! I tested it and it works beautifully.

Thank you very much :)

---

