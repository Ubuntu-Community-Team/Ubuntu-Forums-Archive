---
title: "video editing"
date: 2010-08-20
forum: General Help
---

### Post by dfd001 on 2010-08-20
I use Ubuntu 10.4

I have just learned to use WinFF (near as I can tell it is a gui for ffmpeg), but it apparently does not join/seperate video files.

Anybody know a video splitter/joiner?

even better, does anybody know of a program that converts video/audio formats and can split/join video files?

thanks

---

### Post by jakupl on 2010-08-20
You should have a program for that already, Pitivi comes with ubuntu by default.

---

### Post by zeroseven0183 on 2010-08-20
You can try Avidemux, Kino, Openshot and a lot more from the Ubuntu Software Center.

---

### Post by FakeOutdoorsman on 2010-08-20
FFmpeg can split videos.  It can do this without re-encoding your videos, and therefore it preserves the quality and is much faster.
```
ffmpeg -ss 00:01:20.00 -i input.foo -t 5 -acodec copy -vcodec copy output.foo
```
[indent]**-ss 00:01:20.00** - Skip the first 1 minute and 20 seconds of the input.
**-i input.foo** - The input file.
**-t 5** - The duration of the output file in seconds. Can also be in the same format as the *-ss* example.
**-acodec copy** - Copy the audio stream. Do not re-encode.
**-vcodec copy** - Copy the video stream. Do not re-encode.
**output.foo** - The output file.[/indent]
FFmpeg can also join some videos. See my posts in the [How do I write a Script or shell?](http://ubuntuforums.org/showthread.php?t=1551113) thread for some examples.

---

