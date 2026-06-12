---
title: "convert an .avi file into a mp3"
date: 2009-10-01
forum: General Help
---

### Post by choallin on 2009-10-01
Hi guy's

I'm wondering with what program it is possible to convert a video (i.e. .avi file) in an audio file (.mp3) I've searched the forum, but i just found a thread about converting one video format in an other, but i just want the adio.
Hope you know such a program.
If this is not the right forum, which one would be better?

so long
chaollin

---

### Post by credobyte on 2009-10-01
```
sudo apt-get install ffmpeg
```
```
ffmpeg -i video.avi -acodec copy sound.mp3

```

---

### Post by Bonster on 2009-10-01
use WinFF or Avidemux

---

