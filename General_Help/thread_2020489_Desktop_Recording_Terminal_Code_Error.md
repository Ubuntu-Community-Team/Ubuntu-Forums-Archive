---
title: "Desktop Recording Terminal Code Error"
date: 2012-07-08
forum: General Help
---

### Post by nankura on 2012-07-08
hey guys

im trying to record my desktop with the following command

```
ffmpeg -f alsa -ac 2 -i plughw:0,0 -f x11grab -r 15 -s 1280x1024 -i :0.0 -acodec pcm_s16le -vcodec libx264 -preset ultrafast -threads 0 /home/nankura/Desktop/screencast.mkv
```

and i keep recieving the following error

```
[matroska @ 0x1f7df60] Application provided invalid, non monotonically increasing dts to muxer in stream 1: 1 >= 1
av_interleaved_write_frame(): Invalid argument
```

any speedy help will be greatly appreciated

---

### Post by nankura on 2012-07-08
really? my post gets a randomly generated advertisement and no help? admins were you -.-

---

### Post by GreatDanton on 2012-07-08
I reported spam. Unfortunately I cannot help you, unless you want a new conky :)

---

### Post by mc4man on 2012-07-09
You didn't mention what release of Ubuntu you're using & what version of FFmpeg
It's _possible_ you're using some crappy ffmpeg build provided by the Libav boys, they really want you to use avconv instead.

If that's the case then either use avconv & adjust if needed or put in a real FFmpeg build & see how it goes.
[https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide](https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide)

I use FFmpeg to record the Desktop but much simpler, don't need audio.

In any event ran your command & it works ok here, have an FFmpeg build on this install that's from mid-april 
(also tried with .... -c:a pcm_s16le -c:v libx264 .... which presented a 'cleaner' terminal output

---

