---
title: "mp4 to mp3?"
date: 2010-11-09
forum: General Help
---

### Post by owners4life5 on 2010-11-09
can anyone please tell me how to do this?

i have an mp4 that i need to change to mp3, so that i can open the file in audacity.

any help is appreciated...
thanks,

---

### Post by sully101 on 2010-11-09
this thread should help [http://ubuntuforums.org/showthread.php?t=526435]("http://ubuntuforums.org/showthread.php?t=526435") post #6

but also note #7

or this one [http://ubuntuforums.org/showthread.php?t=138419]("http://ubuntuforums.org/showthread.php?t=138419")

---

### Post by faheemezani on 2010-11-09
I thnik you can do this using VLC. Download and install it. Then launch the program and restream the file that you want to convert to mp3 to a local file (with mp3 encoding selected).

---

### Post by TeoBigusGeekus on 2010-11-10
Try something like this
```
ffmpeg -i yourfile.mp4 -acodec libmp3lame -ab 320k yourfile.mp3
```
Replace 320k with desired mp3 bitrate.

---

### Post by owners4life5 on 2010-11-10
vlc did it. thanks guys.

marking as solved

---

### Post by MooPi on 2010-11-10
I have another alternative which involves mplayer and simple scripts to convert ACC/mp4 files. Very simple to use, just open a terminal where your media is located and type ```
sh mp42lame.sh
``````
sh mp42ogg.sh
```The script just does one file at a time so modify to your needs.

---

