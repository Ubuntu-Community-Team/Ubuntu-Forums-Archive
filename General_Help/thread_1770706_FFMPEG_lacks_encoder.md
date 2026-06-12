---
title: "FFMPEG lacks encoder"
date: 2011-05-29
forum: General Help
---

### Post by aninona on 2011-05-29
I got the folowing error from vlc
```
Streaming / Transcoding failed:
It seems your FFMPEG (libavcodec) installation lacks the following encoder:
MPEG Audio layer 1/2/3.
If you don't know how to fix this, ask for support from your distribution.

This is not an error inside VLC media player.
Do not contact the VideoLAN project about this issue.


```

What should I do to fix it?

thanks and have a wonderfull life & day!:KS:P

---

### Post by lemonchicken on 2011-05-29
vlc's encoder is pretty standard. I would suggest handbrake.

if you really want to use VLC, there will probably be a folder with the codecs/plugins used to encode, in which you will have to place the file. there are loads of mp3 encoder variations, I'm sure someone here (or google) will know of one that works well with VLC & Linux

:grin:

---

### Post by TeoBigusGeekus on 2011-05-29
Open synaptic, search for the libavcodec-extra package and install it.

---

