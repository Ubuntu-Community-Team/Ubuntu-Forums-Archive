---
title: "screen tearing when screencasting"
date: 2012-03-28
forum: General Help
---

### Post by jerome1232 on 2012-03-28
If I use gtk-record my desktop or ffmpeg to capture my screen, I get some pretty bad screen tearing if I rotate my desktop cube, is there any way to fix this? The tearing is only in the resulting playback video, not on my actual screen.

Nvidia GTS 450, Driver version 280.13

The command I used (with varying framerates tried, I don't really know what else I can try changing)

```
ffmpeg -f alsa -ac 2 -ab 256k -i pulse -acodec vorbis -f x11grab -r 60 -s 1920x1080 -i :0.0+0,0 -aspect 16:9 -vcodec libvpx -threads 0 new_screencast.webm
```

The resulting output
[http://voiceserv.dyndns.org/Video/new_screencast2.webm]("http://voiceserv.dyndns.org/Video/new_screencast2.webm")

---

### Post by Paddy Landau on 2012-03-29
The only thing I can suggest is that your hardware may not be quite fast enough for the settings you are using.

When using gtkrecordmydesktop, set the frames-per-second to a lower value. Try 5 frames per second. I don't know the equivalent setting in ffmpeg.

---

### Post by jerome1232 on 2012-03-30
I'll give that a try, unfortunately I flashed my bios with an update for the wrong motherboard (doh!) So I am waiting on a new bios chip atm.

When I was recording I never spiked above 75% cpu usage, and the actual effects are smooth (I think that particular recording I used 30 or 15 frames/second) the lower I go on fps the more stuttery the recording comes out.

I was thinking that it was simply catching frames that were mid-refresh due to it (possibly?) not being in sync with everything else, which is why I was trying 60 frames/second with every vsync option I could find in my settings elsewhere.

---

### Post by Paddy Landau on 2012-03-30
There is a thread somewhere that addresses your problem, to do with performance issues -- perhaps of your graphics card rather than your CPU. Unfortunately, I cannot find it again. Perhaps you will have more luck.

---

### Post by jerome1232 on 2012-04-03
Got the new bios in (yay, not confined to a netbook), the lower I go with the frame rate the progressively worse the recording gets, it has more tearing and it's very choppy with low framerates, almost smooth and fewer tears at high fps (I tried 60 and it almost looked good)

I'll try and look into it more later, right now I have lots and lots of precalc to do.

---

