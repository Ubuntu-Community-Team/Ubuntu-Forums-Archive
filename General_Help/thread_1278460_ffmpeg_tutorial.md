---
title: "ffmpeg tutorial"
date: 2009-09-29
forum: General Help
---

### Post by arnab_das on 2009-09-29
where can i get a tutorial for ffmpeg command line?

or at least i need a command which can help me convert a file to 720x480 res, ac3 audio 5.1 channel. what command can i use for it?

any help is much appreciated.

---

### Post by FakeOutdoorsman on 2009-09-29
What does FFmpeg output when you enter this command?
```
ffmpeg -i your_input_file.avi
```
The output will give useful information in making a proper command.  What is the final destination of this file (viewing on computer, dvd, etc.)?

---

### Post by arnab_das on 2009-09-30
> **FakeOutdoorsman said:**
> What does FFmpeg output when you enter this command?
```
ffmpeg -i your_input_file.avi
```The output will give useful information in making a proper command.  What is the final destination of this file (viewing on computer, dvd, etc.)?


when i enter that command in the terminal this is what i get:

```
FFmpeg version SVN-r20091, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  built on Sep 30 2009 13:10:20 with gcc 4.3.3
  configuration: --enable-gpl --enable-nonfree --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil     50. 3. 0 / 50. 3. 0
  libavcodec    52.36. 0 / 52.36. 0
  libavformat   52.39. 0 / 52.39. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0. 7. 1 /  0. 7. 1
your_input_file.avi: no such file or directory


```final destination is an LG DVD player (supports xvid and divx, although divx support isnt great, thats y i prefer xvid) and then onto an HD ready tv after upscaling.

---

### Post by credobyte on 2009-09-30
Take a look at this one: [http://howto-pages.org/ffmpeg/](http://howto-pages.org/ffmpeg/)

---

### Post by arnab_das on 2009-09-30
> **credobyte said:**
> Take a look at this one: [http://howto-pages.org/ffmpeg/](http://howto-pages.org/ffmpeg/)

awesome! thank u!

---

### Post by FakeOutdoorsman on 2009-09-30
> **arnab_das said:**
> when i enter that command in the terminal this is what i get:

```
FFmpeg version SVN-r20091, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  built on Sep 30 2009 13:10:20 with gcc 4.3.3
  configuration: --enable-gpl --enable-nonfree --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil     50. 3. 0 / 50. 3. 0
  libavcodec    52.36. 0 / 52.36. 0
  libavformat   52.39. 0 / 52.39. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0. 7. 1 /  0. 7. 1
[color=#FF0000]your_input_file.avi[/color]: no such file or directory


```final destination is an LG DVD player (supports xvid and divx, although divx support isnt great, thats y i prefer xvid) and then onto an HD ready tv after upscaling.

I should have mentioned to replace *your_input_file.avi* with the name of the file you want to convert.  For example, if I wanted to convert *drzaius.mp4*, I would use:
```
ffmpeg -i drzaius.mp4
```

---

