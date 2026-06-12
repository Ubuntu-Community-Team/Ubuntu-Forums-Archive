---
title: "using FFMPEG to convert to a dvd format"
date: 2012-08-14
forum: General Help
---

### Post by ColeNi on 2012-08-14
Hi I'm trying to figure out how to use ffmpeg to convert mp4, avi, mkv, etc file types to a dvd format. I was able to convert it to .vob, but the result doesn't work properly as a dvd. 

More specifically I want to convert so that I can burn it to a dvd and play that dvd on a regular dvd player.

Any ideas?

---

### Post by Cheesemill on 2012-08-14
I don't know the specific ffmpeg commands but you could always use [DeVeDe]("apt://devede").

---

### Post by FakeOutdoorsman on 2012-08-14
> **ColeNi said:**
> Any ideas?

What was your ffmpeg command? How did you build the DVD with the resulting files?

ffmpeg has the **-target** option that includes parameters for dvd video:
```
ffmpeg -i input -target ntsc-dvd output.vob
```
or
```
ffmpeg -i input -target pal-dvd output.vob
```

---

