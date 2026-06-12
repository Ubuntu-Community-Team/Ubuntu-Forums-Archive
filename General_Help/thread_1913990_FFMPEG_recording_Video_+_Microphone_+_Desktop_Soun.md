---
title: "FFMPEG: recording Video + Microphone + Desktop Sounds"
date: 2012-01-23
forum: General Help
---

### Post by Yesirom on 2012-01-23
I'm planning on doing some video tutorials and after extensive digging I couldn't find what I need, there is a cool topic here [http://ubuntuforums.org/showthread.php?t=1710642](http://ubuntuforums.org/showthread.php?t=1710642) but it didn't help me since it just crashes when I start the script (I think it's because the pulse setting because I'm using another script that is very similar but uses hw:0,0 instead).

**Here are the things I want to do**:
1. Record the desktop + microphone + desktop sounds at the same time
2. I want my sound file seperate (if possible) so I could touch it up a bit in Audacity

**This is the current script I'm using** for recording (I don't know if even the microphone recording works, gotta try that out, I did only some video quality tests)

```
ffmpeg -f alsa -ac 2 -i hw:0,0 -f x11grab -r 30 -s $(xwininfo -root | grep 'geometry' | awk '{print $2;}') -i :0.0 -acodec pcm_s16le -vcodec libx264 -vpre lossless_ultrafast -threads 0 -y output.mkv
```

I apologize in advance if this topic has been brought up hundred times before but I don't have the time to turn the whole internet upside down for the answers, I just want to do some tutorial :)

---

### Post by Habitual on 2012-01-23
Here's an old command I had archived for comparison.
YMMV... :)

```
ffmpeg -f x11grab -s wxga -r 25 -i :0.0 -sameq ~/mymovie.mpg

```

---

### Post by Yesirom on 2012-01-23
> **Habitual said:**
> Here's an old command I had archived for comparison.
YMMV... :)

```
ffmpeg -f x11grab -s wxga -r 25 -i :0.0 -sameq ~/mymovie.mpg

```

Comparison? :D

---

