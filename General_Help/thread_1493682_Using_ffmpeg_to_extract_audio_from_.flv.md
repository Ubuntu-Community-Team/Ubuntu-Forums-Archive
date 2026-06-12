---
title: "Using ffmpeg to extract audio from .flv"
date: 2010-05-26
forum: General Help
---

### Post by Emmtor on 2010-05-26
Hello,
I've been trying to find a way to grab the audio from youtube videos, because in some cases I cannot find certain rare recordings from anywhere else. Anyway, what i do is wait for the video to load, and then copy-paste the flash file (which i rename with an .flv extention) from the "/tmp" directory to "~/Music/Videos". I then try to extract the sound with ffmpeg:

```

$  ffmpeg -i funeralmarch.flv -vn -acodec copy funeralmarch.mp3
FFmpeg version 0.5-svn17737+3:0.svn20090303-1ubuntu6.2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --extra-version=svn17737+3:0.svn20090303-1ubuntu6.2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --disable-stripping --disable-vhook --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-armv6t2 --disable-armvfp --disable-neon --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 23 2010 15:08:34, gcc: 4.3.3

Seems stream 1 codec frame rate differs from container frame rate: 50.00 (50/1) -> 25.00 (25/1)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'funeralmarch.flv':
  Duration: 00:06:08.40, start: 0.000000, bitrate: 102 kb/s
    Stream #0.0(und): Audio: aac, 44100 Hz, stereo, s16
    Stream #0.1(und): Video: h264, yuv420p, 480x360, 25 tbr, 25 tbn, 50 tbc
Output #0, mp3, to 'funeralmarch.mp3':
    Stream #0.0(und): Audio: mp4a / 0x6134706D, 44100 Hz, stereo, s16
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
size=    1693kB time=134.21 bitrate= 103.3kbits/s    
video:0kB audio:1693kB global headers:0kB muxing overhead 0.001846%

```

Then i open the .mp3 file with totem, but all I get is an error message: "cannot determine type of stream"
The funny thing is that it works when i use some of my old files as input in the very same ffmpeg command. These old files were downloaded via real player, from youtube, back in my Windows XP days.

Can anyone help?

---

### Post by FakeOutdoorsman on 2010-05-26
Using *-acodec copy* is a good idea as this simply copies the audio and doesn't re-encode, but you're copying AAC audio into a MP3 container file.  FFmpeg can tell you the audio format of your input and in your example it shows:
```
Stream #0.0(und): Audio: aac, 44100 Hz, stereo, s16
```
So instead of copying to .mp3, you can try .aac, .mp4, .m4a, or any other container format that supports AAC audio.  If you want MP3 with this particular file, you will need to re-encode.  First you'll need to enable the mp3 encoder in FFmpeg.  It's easy to do.  Since you're using Jaunty, see Option B:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

Now for the command:
```
ffmpeg -i input.foo -acodec libmp3lame -aq 4 output.mp3
```
You can also use *-ab* instead of *-aq*, such as *-ab 128k*, to create a CBR instead of VBR mp3.  I believe the values for *-aq* are the same as *-V* for **lame**.  [Hydrogen Audio](http://wiki.hydrogenaudio.org/index.php?title=LAME) has good suggestions for what *-aq/-V* to use.

---

### Post by Emmtor on 2010-05-26
Your post was very helpful, thanks!

---

### Post by KeyserSoze93 on 2010-05-26
> **Emmtor said:**
> 
  Duration: 00:06:08.40, start: 0.000000, bitrate: 102 kb/s
    Stream #0.0(und): Audio: aac, 44100 Hz, stereo, s16
    Stream #0.1(und): Video: h264, yuv420p, 480x360, 25 tbr, 25 

You could try giving the output file the aac extension. This may allow you to simply rip the audio, instead of transcoding it to MP3, which *should* yield slightly better quality if it works.

---

### Post by Emmtor on 2010-05-30
Hello again.
With your help I wrote a little script that saved flash videos from youtube and then extracted the audio, and then saving it in an mp3 format.It worked fine for the first 4 days.My script is this:

```

#!/bin/bash

cp /tmp/* [Flash] ~/transefer
cd ~/transefer
for i in *; do ffmpeg -i "$i" -acodec libmp3lame -aq 4 $i.mp3; done
cp *.mp3 $1
rm *
echo "files saved in $1!"

```

Today,when I used it again to save 4 videos, the last video's audio was extracted to an empty file(it lasted 0:00 seconds, i could play it with totem).From then on every time i used the script, the output files would be empty, and the output in the terminal would be:

```

scavenger@Power-pc:~/silly-scripting/lame-3.97$ ytaudio ~/Music/Ytdl
cp: cannot open `/tmp/gedit.scavenger.1409938537' for reading: No such device or address
cp: omitting directory `/tmp/gpg-HZFuoI'
cp: omitting directory `/tmp/keyring-Da8XeV'
cp: omitting directory `/tmp/orbit-root'
cp: omitting directory `/tmp/orbit-scavenger'
cp: omitting directory `/tmp/pulse-PKdhtXMmr18n'
cp: omitting directory `/tmp/pulse-SCAx2GrFLvBA'
cp: omitting directory `/tmp/ssh-LeHhwZ3296'
cp: omitting directory `/tmp/virtual-scavenger.zilk6E'
cp: cannot stat `[Flash]': No such file or directory
FFmpeg version 0.5-svn17737+3:0.svn20090303-1ubuntu6.2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --extra-version=svn17737+3:0.svn20090303-1ubuntu6.2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --disable-stripping --disable-vhook --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-armv6t2 --disable-armvfp --disable-neon --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 23 2010 15:08:34, gcc: 4.3.3

Seems stream 0 codec frame rate differs from container frame rate: 2000.00 (2000/1) -> 25.00 (25/1)
Input #0, flv, from 'FlashBpU05H':
  Duration: 00:04:02.00, start: 0.000000, bitrate: 117 kb/s
    Stream #0.0: Video: h264, yuv420p, 320x240 [PAR 1:1 DAR 4:3], 117 kb/s, 25 tbr, 1k tbn, 2k tbc
    Stream #0.1: Audio: aac, 22050 Hz, stereo, s16
Output #0, mp3, to 'FlashBpU05H.mp3':
    Stream #0.0: Audio: libmp3lame, 22050 Hz, stereo, s16, 64 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
Press [q] to stop encoding
[libmp3lame @ 0x95a6c10]lame: output buffer too small (buffer index: 9695, free bytes: 97)
Audio encoding failed
files saved in /home/scavenger/Music/Ytdl!

```


Googling "output buffer too small" resulted in a couple of forum threads, where people had the same problem, and they were using the lame encoder.Some solved their problem with downgrading lame to version 3.97,and others suggested reinstalling ffmpeg.I did both(compiled lame 3.97 from source and removed and then installed ffmpeg via synaptic),and then i got the libavcodec-unstripped-52 and installed it(sudo apt-get install ffmpeg libavcodec-unstripped-52)
I am using Ubuntu Jaunty. What should I do?

Thank you in advance.

---

### Post by Emmtor on 2010-06-05
Bump!

---

### Post by jesuisbenjamin on 2010-06-05
Here is a Python prog i made sometime ago to convert fla's to mp3 using ffmpeg.

It's looking for the flash videos in .tmp, converts them and brings them into your ~/Music. You need to redefine the output path though: out_dir = '/home/USERNAME/Music/' 
Hope it helps

[PHP]#!/usr/bin/python
# Filename: convert.py
""" Look through the /tmp/ for Macromedia Flash Videos
    Converts those files into .mp3 files and store them in ~/Music"""
# We need:
import os
import magic
import commands
tmp_content = []
count = 1
source_dir = '/tmp/'
keyword = 'Macromedia Flash Video'
# 1. Function to find flash files in /tmp and put them in list
for found in os.listdir(source_dir):
    cookie = magic.open(magic.MAGIC_NONE)
    cookie.load()
    found_type = cookie.file(str(source_dir + found.replace(' ', '\ ')))
    if keyword == found_type:
        tmp_content.append(found)
    else:
        pass
        
# (optional) 1.5 Print list of flashfiles in /tmp
if len(tmp_content) != 0:
    print 'The Macromedia Flash Videos found in' , source_dir, 'are: '
    for fla in tmp_content:
        print tmp_content.index(fla), fla
else:
    print 'There are no Macromedia Flash Videos in', source_dir
    quit()
    
# 2. flash_input = Raw input from user to select input-file's name

while count == 1:
    flash_input = raw_input('Type the index of the file you want to convert to mp3:  ')
    if int(flash_input) > (len(tmp_content) - 1):
        print 'Please chose a file from the list.'
    else:
        count = 0
# 3. mp3_output = Raw input from user to define output-file's name
mp3_output = raw_input('Type output-file name: ')
# 4. Define output directory outDir
out_dir = '/home/benjamin/Music/'
# 5. Run ffmpeg -i flash_input -ab 128K outDir/mp3_output
command_line = 'ffmpeg -i /tmp/' + tmp_content[int(flash_input)] + ' -ab 128K ' \
               + out_dir + mp3_output + '.mp3'
os.system(command_line)

[/PHP]

---

### Post by Emmtor on 2010-06-15
Thanks for the script jesuisbenjamin!
I haven't tried it out yet, but thanks for sharing anyway!

---

### Post by Jake007g on 2010-06-15
Might not be what you're wanting, but have you tried the[ Video2Mp3 extension]("http://www.video2mp3.net/firefox_addon.php") for Firefox/Chrome?

I use this a lot, it gives you a nice simple box below YouTube videos and you can download the video as a Low/High quality Mp3 within seconds. Probably the easiest solution in my opinion :D

---

### Post by FakeOutdoorsman on 2010-06-15
> **Emmtor said:**
> ...

Googling "output buffer too small" resulted in a couple of forum threads, where people had the same problem, and they were using the lame encoder.Some solved their problem with downgrading lame to version 3.97,and others suggested reinstalling ffmpeg.I did both(compiled lame 3.97 from source and removed and then installed ffmpeg via synaptic),and then i got the libavcodec-unstripped-52 and installed it(sudo apt-get install ffmpeg libavcodec-unstripped-52)
I am using Ubuntu Jaunty. What should I do?

Thank you in advance.

The **output buffer too small** error is a bug with LAME.  I'm not sure which version of LAME fixed this, but the recent stable 3.98.4 works.  One method to resolve this is to compile LAME, and then compile FFmpeg.  See the following:

[HOWTO: Install FFmpeg and x264 on Ubuntu Jaunty Jackalope 9.04](http://ubuntuforums.org/showpost.php?p=8345112&postcount=636)

On step two, omit installing *libmp3lame-dev*. Now install LAME:
```
wget http://downloads.sourceforge.net/project/lame/lame/3.98.4/lame-3.98.4.tar.gz
tar xzvf lame-3.98.4.tar.gz
cd lame-3.98.4
./configure
make
sudo checkinstall --fstrans=no --install=yes --pkgname="lame" --pkgversion="3.98.4" --backup=no --default
```
Now continue following the guide.  You can omit installing x264, libopencore-amr, and libtheora if you don't think you'll use those.  I didn't actually test this as I am out of town and away from my usual computer.

Another method may be to simply pipe the output from FFmpeg to LAME:
```
ffmpeg -i input.foo -f wav - | lame -V 3 - output.mp3
```
You may not have to compile anything to do this.

---

### Post by Emmtor on 2010-08-28
I'd like to thank everyone for the replies.


To  FakeOutdoorsman:
The piping idea actually worked!
Thanks so much!

---

