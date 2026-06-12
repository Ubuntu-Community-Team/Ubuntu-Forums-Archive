---
title: "ffmpeg x11grab without compositing has lots of tears"
date: 2011-12-28
forum: General Help
---

### Post by J V on 2011-12-28
Trying to record a section of my screen with ffmpeg results in a LOT of tearing, I'm not on a DE (Openbox and conky comprise most of my system) and xcompmgr has given me problems, how do I get x11grab to give me a clean image?

---

### Post by FakeOutdoorsman on 2011-12-28
I just use Openbox and I have no tearing issues. I'm not sure what is causing the tearing, but please show your ffmpeg command and the complete output. Does the tearing also occue if you play the output with ffplay?

---

### Post by J V on 2011-12-29
The command I used was:
```
ffmpeg -f alsa -i pulse -f x11grab -r 10 -s hd720 -i :0.0+320,180 -vcodec libx264 -vpre lossless_ultrafast -acodec libmp3lame -threads 1 -y -sameq out.avi
```

10FPS is about the fastest it will go

To speed it up it's writing to a tmpfs mount

---

### Post by FakeOutdoorsman on 2011-12-30
> **J V said:**
> The command I used was:
```
ffmpeg -f alsa -i pulse -f x11grab -r 10 -s hd720 -i :0.0+320,180 -vcodec libx264 -vpre lossless_ultrafast -acodec libmp3lame -threads 1 -y -sameq out.avi
```

10FPS is about the fastest it will go

To speed it up it's writing to a tmpfs mount

I can't duplicate the issue, but I am using a [compiled FFmpeg](http://ubuntuforums.org/showthread.php?t=786095). I'm guessing you're using ffmpeg or libav from the repository, but it's hard to say without the ffmpeg console output.

You may be able to increase encoding speed by changing *-threads 1* to *-threads 0* which will automatically choose an appropriate threads value, and *-r 10* to a higher value such as *-r 30*.

Does the tearing also occur if you play the output with ffplay?
```
ffplay out.avi
```

---

