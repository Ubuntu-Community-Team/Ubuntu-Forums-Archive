---
title: "scripting to convert .wav to .mp3 files"
date: 2011-06-24
forum: General Help
---

### Post by iconoclast hero on 2011-06-24
I have a set of 5 files:
Tell-All -- Disc 1.wav
Tell-All -- Disc 2.wav
Tell-All -- Disc 3.wav
Tell-All -- Disc 4.wav
Tell-All -- Disc 5.wav

on which I need to perform the following actions:
mp3sEncoder -if "Tell-All -- Disc 1.wav" -of "Tell-All -- Disc 1.mp3" -br 24000 -mono
mp3sEncoder -if "Tell-All -- Disc 2.wav" -of "Tell-All -- Disc 2.mp3" -br 24000 -mono
mp3sEncoder -if "Tell-All -- Disc 3.wav" -of "Tell-All -- Disc 3.mp3" -br 24000 -mono
mp3sEncoder -if "Tell-All -- Disc 4.wav" -of "Tell-All -- Disc 4.mp3" -br 24000 -mono
mp3sEncoder -if "Tell-All -- Disc 5.wav" -of "Tell-All -- Disc 5.mp3" -br 24000 -mono

I will have other files in the future which I will need to convert from .wav to .mp3.

How would I go about automating this so that it would automatically take every .wav in a directory and convert it with mp3sEncoder to .mp3 with the options of -br 24000 -mono while retaining the filename?

Thanks

---

### Post by LordNeo on 2011-06-24
```

while [ $# -ge 1 ];
do
    filename=`echo "$1" | sed 'y/ABCDEFGHIJKLMNOPQRSTUVWXYZ/abcdefghijklmnopqrstuvwxyz/'`
    case "$filename" in
        *.wav)
           mp3sEncoder -if "$1" -of "$1".mp3 -br 24000 -mono
            ;;
        *)
            echo "not doing anything"
            exit 0
            ;;
    esac
    shift
done

```

This will do a file that you can drag files on, and automatically convert every file.

I'm not sure if the "$1".mp3 part will work. Try it first

PS: It will also make the file be called "blablabla.wav.mp3"

---

### Post by TeoBigusGeekus on 2011-06-24
```
find ./ -maxdepth 1 -iname "*.wav"| while read file; 
do
	fn=$(basename "$file") 
	n="${fn%.*}"
	mp3sEncoder -if "$fn" -of "$n".mp3 -br 24000 -mono
done
```

---

### Post by iconoclast hero on 2011-06-28
Ok, I couldn't get either of these to work...

I put them in a text file and then chmod +777 to make it executable and I get...
```
wavmp3: command not found

```

am I missing something?

---

### Post by iconoclast hero on 2011-07-01
Any help on this?

---

### Post by TeoBigusGeekus on 2011-07-01
```
find ./ -maxdepth 1 -iname "*.wav"| while read file; 
do
	fn=$(basename "$file") 
	n="${fn%.*}"
        ffmpeg -i "$fn" -acodec libmp3lame -ab 24k -ac 1 "$n".mp3
done
```

Try this one.

---

### Post by iconoclast hero on 2011-07-01
But how do I execute it?

Like I said, I tried pasting it into a text file and giving  chmod 777 the file but when i type in the file name I gave it, it said command not found.

I really thought that was all I needed to do?

[code]
~/Music$ chmod 777 wavtomp3
~/Music$ ls
wavtomp3
Where Men Win Glory -- Disc 01.wav
Where Men Win Glory -- Disc 02.wav
Where Men Win Glory -- Disc 03.wav
Where Men Win Glory -- Disc 04.wav
Where Men Win Glory -- Disc 05.wav
Where Men Win Glory -- Disc 06.wav
Where Men Win Glory -- Disc 07.wav
Where Men Win Glory -- Disc 08.wav
Where Men Win Glory -- Disc 09.wav
Where Men Win Glory -- Disc 10.wav
Where Men Win Glory -- Disc 11.wav
~/Music$ wavtomp3
wavtomp3: command not found

---

### Post by TeoBigusGeekus on 2011-07-01
My last one uses ffmpeg instead of mp3sEncoder (I don't even know what this is). So, yeah, paste it in a text file, save it as wav2mp3, make it executable
```
chmod +x wav2mp3
```
execute it
```
/path/wav2mp3
```
and post back with results.

EDIT: If you're in the same folder as the script, then you execute it with
```
./wav2mp3
```

---

### Post by sisco311 on 2011-07-01
> **TeoBigusGeekus said:**
> ```
find ./ -maxdepth 1 -iname "*.wav"| while read file; 
do
	fn=$(basename "$file") 
	n="${fn%.*}"
        ffmpeg -i "$fn" -acodec libmp3lame -ab 24k -ac 1 "$n".mp3
done
```

Try this one.

Please check out: [http://mywiki.wooledge.org/BashFAQ/020](http://mywiki.wooledge.org/BashFAQ/020)

I would go with something like:
```
#!/bin/bash

usage ()
{
  echo "Usage: $0 DIRECTORY"
  exit 1
}>&2

if (( $# != 1 ))
then
  usage
fi

cd "$1"  || usage

shopt -s nullglob
for file in ./*.wav
do
  ffmpeg -i "$file" -acodec libmp3lame -ab 24k -ac 1 "${file%.wav}".mp3
done

```

---

### Post by iconoclast hero on 2011-07-01
> **TeoBigusGeekus said:**
> My last one uses ffmpeg instead of mp3sEncoder (I don't even know what this is). So, yeah, paste it in a text file, save it as wav2mp3, make it executable
```
chmod +x wav2mp3
```execute it
```
/path/wav2mp3
```and post back with results.

EDIT: If you're in the same folder as the script, then you execute it with
```
./wav2mp3
```

Ok smart guy, I needed the execute with the path!  :)  ~/Music/wavmp3 works with the mp3sEncoder with is the linux Fraunhoffer encoder that I love for compressing audio books because it does such a great job at low bit rates.  I could have sworn I tried the ./wavmp3 but perhaps I did not (which is what I named your original script).

It appears to be encoding right now!

---

### Post by FormatSeize on 2011-07-01
> **iconoclast hero said:**
>  
I put them in a text file and then chmod +777 to make it executable and I get...
```
wavmp3: command not found

```
 
am I missing something?
Did you cut and paste them or did you type it yourself? The reason I ask is because neither of those scripts contain the string "wavmp3" anywhere in them, so I can't imagine how that command is being passed to bash.

---

### Post by TeoBigusGeekus on 2011-07-01
> **FormatSeize said:**
> Did you cut and paste them or did you type it yourself? The reason I ask is because neither of those scripts contain the string "wavmp3" anywhere in them, so I can't imagine how that command is being passed to bash.

He probably saved the script as wavmp3 and tried to execute it with
```
wavmp3
```

@sisco311
Could you please elaborate?

@iconoclast hero
Glad to hear that, though I personally use ffmpeg for everything audio/video related - why should I change it?: it's perfect :P
Don't forget to mark the thread as solved.

---

### Post by iconoclast hero on 2011-07-01
> **FormatSeize said:**
> Did you cut and paste them or did you type it yourself? The reason I ask is because neither of those scripts contain the string "wavmp3" anywhere in them, so I can't imagine how that command is being passed to bash.

I started with nano wavmp3 then chmod 777 wavmp3 then executed the file without the ./ or path...so anyway, it worked:

```

-rw-r--r--  1  admin   13419198 2011-07-01 17:13 Where Men Win Glory -- Disc 01.mp3
-rw-r--r--  1  admin  396377900 2011-06-28 22:47 Where Men Win Glory -- Disc 01.wav
-rw-r--r--  1  admin   13575042 2011-07-01 17:11 Where Men Win Glory -- Disc 02.mp3
-rw-r--r--  1  admin  400983116 2011-06-28 23:21 Where Men Win Glory -- Disc 02.wav
-rw-r--r--  1  admin   13731042 2011-07-01 17:10 Where Men Win Glory -- Disc 03.mp3
-rw-r--r--  1  admin  405589508 2011-06-28 23:27 Where Men Win Glory -- Disc 03.wav
-rw-r--r--  1  admin   13194714 2011-07-01 17:14 Where Men Win Glory -- Disc 04.mp3
-rw-r--r--  1  admin  389748788 2011-06-29 00:04 Where Men Win Glory -- Disc 04.wav
-rw-r--r--  1  admin   12136488 2011-07-01 17:22 Where Men Win Glory -- Disc 05.mp3
-rw-r--r--  1  admin  358489532 2011-06-29 00:10 Where Men Win Glory -- Disc 05.wav
-rw-r--r--  1  admin   13486044 2011-07-01 17:08 Where Men Win Glory -- Disc 06.mp3
-rw-r--r--  1  admin  398353580 2011-06-29 00:23 Where Men Win Glory -- Disc 06.wav
-rw-r--r--  1  admin   12069954 2011-07-01 17:09 Where Men Win Glory -- Disc 07.mp3
-rw-r--r--  1  admin  356524436 2011-06-29 10:35 Where Men Win Glory -- Disc 07.wav
-rw-r--r--  1  admin   11705772 2011-07-01 17:16 Where Men Win Glory -- Disc 08.mp3
-rw-r--r--  1  admin  345767564 2011-06-29 10:42 Where Men Win Glory -- Disc 08.wav
-rw-r--r--  1  admin   12624690 2011-07-01 17:20 Where Men Win Glory -- Disc 09.mp3
-rw-r--r--  1  admin  372910820 2011-06-29 10:56 Where Men Win Glory -- Disc 09.wav
-rw-r--r--  1  admin   13699296 2011-07-01 17:12 Where Men Win Glory -- Disc 10.mp3
-rw-r--r--  1  admin  404652236 2011-06-29 11:05 Where Men Win Glory -- Disc 10.wav
-rw-r--r--  1  admin   11662482 2011-07-01 17:15 Where Men Win Glory -- Disc 11.mp3
-rw-r--r--  1  admin  344488076 2011-06-29 14:42 Where Men Win Glory -- Disc 11.wav

```

---

### Post by iconoclast hero on 2011-07-01
> **TeoBigusGeekus said:**
> He probably saved the script as wavmp3 and tried to execute it with
```
wavmp3
```@sisco311
Could you please elaborate?

@iconoclast hero
Glad to hear that, though I personally use ffmpeg for everything audio/video related - why should I change it?: it's perfect :P
Don't forget to mark the thread as solved.

I use LAME when I'm encoding music and I've been using rubyripper instead of CDex@wine.  When I'm doing disc-at-once rips for audio books, a) rubyripper can't do that and b) the mp3sEncoder has issues downmixing from stereo to mono in linux.  With CDex, I can save the wav as a mono file and then the encoder does not have to downmix.  If you look at my file sizes, it does pretty well for itself.

Thanks for the help...and I was planning on hitting solve anyway!  :)

---

### Post by sisco311 on 2011-07-01
> **TeoBigusGeekus said:**
> 
@sisco311
Could you please elaborate?


If you don't have to search for the files recursively, you can use filename expansion:
```
for file in ./*.wav
do
  something
done
```

If you have to use find, then the following form is preferred:
```

while IFS= read -r -d '' file
do
  something
done< <(find PATH OPTIONS -print0)
```

---

### Post by iconoclast hero on 2011-07-01
Oh, before I do mark solved, please see the following and let me know how to get the proper file:

```
 
FFmpeg version 0.6-4:0.6-2ubuntu6.1, Copyright (c) 2000-2010 the FFmpeg developers
  built on Mar 31 2011 18:42:12 with gcc 4.4.5
  configuration: --extra-version=4:0.6-2ubuntu6.1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  WARNING: library configuration mismatch
  libavutil   configuration: --extra-version=4:0.6-2ubuntu6.1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavcodec  configuration: --extra-version=4:0.6-2ubuntu6.1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavformat configuration: --extra-version=4:0.6-2ubuntu6.1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavdevice configuration: --extra-version=4:0.6-2ubuntu6.1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavfilter configuration: --extra-version=4:0.6-2ubuntu6.1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libswscale  configuration: --extra-version=4:0.6-2ubuntu6.1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libpostproc configuration: --extra-version=4:0.6-2ubuntu6.1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavutil     50.15. 1 / 50.15. 1
  libavcodec    52.72. 2 / 52.72. 2
  libavformat   52.64. 2 / 52.64. 2
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.19. 0 /  1.19. 0
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0
[wav @ 0x87e1420]max_analyze_duration reached
[wav @ 0x87e1420]Estimating duration from bitrate, this may be inaccurate
Input #0, wav, from 'Seek My Face -- Disc 3.wav':
  Duration: 01:13:19.68, bitrate: 705 kb/s
    Stream #0.0: Audio: pcm_s16le, 44100 Hz, 1 channels, s16, 705 kb/s
Unknown encoder 'libmp3lame'
~/Music$ sudo apt-get libmp3lame
E: Invalid operation libmp3lame

```

This is for the second code, not the one with the mp3sEncoder...

---

### Post by TeoBigusGeekus on 2011-07-01
Why don't they pack a proper version of ffmpeg with ubuntu?
[http://ubuntuforums.org/showthread.php?t=1385688]("http://ubuntuforums.org/showthread.php?t=1385688")

---

### Post by TeoBigusGeekus on 2011-07-01
> **sisco311 said:**
> If you don't have to search for the files recursively, you can use filename expansion:
```
for file in ./*.wav
do
  something
done
```

If you have to use find, then the following form is preferred:
```

while IFS= read -r -d '' file
do
  something
done< <(find PATH OPTIONS -print0)
```
But why?

---

### Post by sisco311 on 2011-07-01
> **TeoBigusGeekus said:**
> But why?

Because they work with any possible filename. Check out the link from my first  post.

---

### Post by TeoBigusGeekus on 2011-07-01
> **sisco311 said:**
> Because they work with any possible filename. Check out the link from my first  post.

Ok, thanks for the info, appreciated.

---

### Post by iconoclast hero on 2011-07-01
> **TeoBigusGeekus said:**
> Why don't they pack a proper version of ffmpeg with ubuntu?
[http://ubuntuforums.org/showthread.php?t=1385688](http://ubuntuforums.org/showthread.php?t=1385688)

Ok, I did that but that second script did not work...  It only did one wav file and exited.  Why it picked the sixth disk of the alphabetically second book, I don't know, but it did.  I don't care because the Fraunhoffer encoder works, but if someone comes looking at this thread, the FFmpeg/LAME encoder does not work with more than one file.  For the record, the difference is size between the two encoders is 4 580 066 bytes.

The output is below:

```

~/Music$ ./wavtomp3
FFmpeg version 0.6-4:0.6-2ubuntu6.1, Copyright (c) 2000-2010 the FFmpeg developers
  built on Mar 31 2011 18:42:12 with gcc 4.4.5
  configuration: --extra-version=4:0.6-2ubuntu6.1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  WARNING: library configuration mismatch
  libavutil   configuration: --extra-version=4:0.6-2ubuntu3.1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libmp3lame --enable-gpl --enable-postproc --enable-x11grab --enable-libfaad --enable-libxvid --enable-libx264 --enable-librtmp --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavcodec  configuration: --extra-version=4:0.6-2ubuntu3.1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libmp3lame --enable-gpl --enable-postproc --enable-x11grab --enable-libfaad --enable-libxvid --enable-libx264 --enable-librtmp --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavformat configuration: --extra-version=4:0.6-2ubuntu6.1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavdevice configuration: --extra-version=4:0.6-2ubuntu6.1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavfilter configuration: --extra-version=4:0.6-2ubuntu6.1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libswscale  configuration: --extra-version=4:0.6-2ubuntu6.1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libpostproc configuration: --extra-version=4:0.6-2ubuntu6.1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavutil     50.15. 1 / 50.15. 1
  libavcodec    52.72. 2 / 52.72. 2
  libavformat   52.64. 2 / 52.64. 2
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.19. 0 /  1.19. 0
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0
[wav @ 0x9e2dbc0]max_analyze_duration reached
[wav @ 0x9e2dbc0]Estimating duration from bitrate, this may be inaccurate
Input #0, wav, from 'Where Men Win Glory -- Disc 06.wav':
  Duration: 01:15:16.48, bitrate: 705 kb/s
    Stream #0.0: Audio: pcm_s16le, 44100 Hz, 1 channels, s16, 705 kb/s
Output #0, mp3, to 'Where Men Win Glory -- Disc 06.mp3':
  Metadata:
    TSSE            : Lavf52.64.2
    Stream #0.0: Audio: libmp3lame, 44100 Hz, 1 channels, s16, 24 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
size=   17643kB time=4516.52 bitrate=  32.0kbits/s    
video:0kB audio:17643kB global headers:0kB muxing overhead 0.000183%

```

---

