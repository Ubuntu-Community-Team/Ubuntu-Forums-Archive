---
title: "Change video filetypes."
date: 2011-02-26
forum: General Help
---

### Post by MourningsEnd on 2011-02-26
How can I change .ogv to something that would work on YouTube?

---

### Post by acrazyplayer on 2011-02-26
there are many video conversion tools available, probably the easiest are 

avidemux
arista transcoder
handbrake

just convert it into anything like avi h264 mp4 or anything besides ogv

---

### Post by gerowen on 2011-02-26
I've written a script that I use on a regular basis that converts videos to an AVI format that works on Youtube.  It converts the video with very little to no loss in quality and maintains the original resolution/aspect ratio.  Use, modify and redistribute as you see fit, just take my name and contact info out of the comment lines if you make any changes.  It's attached to this post.  The only pre-requisite to running this is that you have mencoder installed.  Just make sure you run it in the terminal.

Edit: For some reason when you download it with firefox the file is not marked as executable, so you may have to manually mark it as executable before you will get prompted to "run" it when you double click the icon.

---

### Post by MourningsEnd on 2011-02-26
None of those programs let me load .ogv?  |:

How do I use your program, gerowen?

---

### Post by Perfect Storm on 2011-02-27
Try winFF

---

### Post by gerowen on 2011-02-28
> **MourningsEnd said:**
> None of those programs let me load .ogv?  |:

How do I use your program, gerowen?

Just like you would any other shell script, cause' that's all it is.  Just download it, then open a terminal in the location that you saved it to and run it with:

```
./anyavi.sh
```

You may have to make it executable with this first:
```
sudo chmod a+rx anyavi.sh
```

---

### Post by Matt__ on 2011-02-28
[Mobile media converter](http://www.miksoft.net/mobileMediaConverterDown.htm) can convert MP3, WMA, WAV, OGG, MP4, MPEG, AVI, FLV, Xvid, MOV, WebM and some other stuff, all in an easy GUI with drag n drop.
(uses ffmpeg and mencoder)

---

