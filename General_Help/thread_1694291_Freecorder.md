---
title: "Freecorder"
date: 2011-02-24
forum: General Help
---

### Post by jezzyjez on 2011-02-24
Has anyone found a decent alternative for freecorder on Ubuntu?

If you dont know what it is it records sound directly from your soundcard to a mp3.

I tried mp3mymp3 with wine but it doesnt seem to work.

---

### Post by An Sanct on 2011-02-24
I used to "rip" a radio show a long time ago, I used VLC, network streaming and encode/save as, as described [here]("http://www.howtogeek.com/howto/2719/how-to-convert-video-files-formats-to-mp3-with-vlc/")

---

### Post by dino99 on 2011-02-24
[http://alternativeto.net/software/freecorder-toolbar/?platform=linux](http://alternativeto.net/software/freecorder-toolbar/?platform=linux)

---

### Post by jezzyjez on 2011-02-24
These are both good but they dont offer the same flexability as freecorder

I want to beable to record any sound my laptop is playing. Whether from online streams to downloaded content.

---

### Post by ajgreeny on 2011-02-24
Have a look at arecord.

Type **man arecord** in terminal to see the manual with all the options available, and by piping it through ffmpeg, you can have it record what you want.  Use various options and you can get an mp3 from it.

---

