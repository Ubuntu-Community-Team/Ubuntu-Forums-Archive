---
title: "get video info recursively?"
date: 2012-10-10
forum: General Help
---

### Post by sohlinux on 2012-10-10
Hi,

I have a folder full of videos, I want to use ffmpeg to get the video info from all the videos in the folder and its sub_folders recursively and sent to a file.txt but it must show the folder name and the video info under it.

at the moment I can only get the video info by going in to each directory and typing ffmpeg -i

Input #0, avi, from '06138.avi':
  Metadata:
    ISFT            : Lavf50.6.0
  Duration: 00:20:22.42, start: 0.000000, bitrate: 2620 kb/s
    Stream #0.0: Video: msmpeg4, yuv420p, 720x576, 25 tbr, 25 tbn, 25 tbc
    Stream #0.1: Audio: mp3, 44100 Hz, 2 channels, s16, 112 kb/s


thanks

---

### Post by sohlinux on 2012-10-10
or at least print the output to the screen?

---

### Post by erind on 2012-10-10
> **sohlinux said:**
> Hi,

I have a folder full of videos, I want to use ffmpeg to get the video info from all the videos in the folder and its sub_folders recursively and sent to a file.txt but it must show the folder name and the video info under it.

at the moment I can only get the video info by going in to each directory and typing ffmpeg -i

[...]


Using *ffmpeg *in this manner, you'd be processing *std error* stream instead of the normal *std output*, it'd be slower and the output would be limited, (I've done that too before).

In this case one tool I'd recommend is **mediainfo** (it's in the repos) - it has a cleaner output and more info:

 ```
cd /path/to/videos
find "$(pwd)" -type f -print0 | xargs -0 mediainfo > video_media_info

```Anyway if no other option is available *ffmpeg* slower option is:

 ```
find "$(pwd)" -type f -exec ffmpeg -i {} \; 2> video_ffmpeg_output

```Then you can parse the files' output for each video individually. If needed use *find*'s *-name* (or its other options)  to refine  its output.

---

### Post by FakeOutdoorsman on 2012-10-10
Using ffprobe with the *-print_format* option might be useful here (available formats are: default, compact, csv, flat, ini, json, xml). I'm not sure if the repo version of "ffprobe" can do this since I compile it myself.

[How To Compile FFmpeg and x264 on Ubuntu](https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide)

---

### Post by sohlinux on 2012-10-11
> **erind said:**
> Using *ffmpeg *in this manner, you'd be processing *std error* stream instead of the normal *std output*, it'd be slower and the output would be limited, (I've done that too before).

In this case one tool I'd recommend is **mediainfo** (it's in the repos) - it has a cleaner output and more info:

 ```
cd /path/to/videos
find "$(pwd)" -type f -print0 | xargs -0 mediainfo > video_media_info

```Anyway if no other option is available *ffmpeg* slower option is:

 ```
find "$(pwd)" -type f -exec ffmpeg -i {} \; 2> video_ffmpeg_output

```Then you can parse the files' output for each video individually. If needed use *find*'s *-name* (or its other options)  to refine  its output.

thanks but its also printing the images info which are inside the folders with the videos

I only want to print info related to video types avi, wmv, mpeg, mpg, mp4, mov, m4v, flv, m2t

I added avi ok with -name "*.avi" but how do I add all video types to the command?

thanks
 ```
find "$(pwd)" -type f -name "*.avi" -exec ffmpeg -i {} \; 2> video_ffmpeg_output


```

---

### Post by erind on 2012-10-11
> **sohlinux said:**
> thanks but its also printing the images info which are inside the folders with the videos

I only want to print info related to video types avi, wmv, mpeg, mpg, mp4, mov, m4v, flv, m2t

I added avi ok with -name "*.avi" but how do I add all video types to the command?
...

Try this:

```
find "$(pwd)" -type f -regextype posix-egrep -iregex ".*/.+\.(avi|wmv|mpeg|mpg|mp4|mov|m4v|flv|m2t)" -exec ffmpeg -i {} \; 2> video_ffmpeg_output 
```Note that the *-regex *find expression matches the whole name (the whole path), not just the file name. Besides man pages, *softpanorama.info* has plenty of info too:

[http://www.softpanorama.info/Tools/Find/index.shtml](http://www.softpanorama.info/Tools/Find/index.shtml)

____________________________________________________

The portable way (with non-GNU find) would be something along the lines of:

```
find . \( -name '*.avi' -o -name '*.flv' -o -name ... \)  -exec ...

```

---

### Post by sohlinux on 2012-10-11
> **erind said:**
> Try this:

```
find "$(pwd)" -type f -regextype posix-egrep -iregex ".*/.+\.(avi|wmv|mpeg|mpg|mp4|mov|m4v|flv|m2t)" -exec ffmpeg -i {} \; 2> video_ffmpeg_output 
```Note that the *-regex *find expression matches the whole name (the whole path), not just the file name. Besides man pages, *softpanorama.info* has plenty of info too:

[http://www.softpanorama.info/Tools/Find/index.shtml](http://www.softpanorama.info/Tools/Find/index.shtml)

____________________________________________________

The portable way (with non-GNU find) would be something along the lines of:

```
find . \( -name '*.avi' -o -name '*.flv' -o -name ... \)  -exec ...

```

awesome. thanks ;)

---

