---
title: "Problem ffmpeg/avconv during export"
date: 2012-06-12
forum: General Help
---

### Post by Bromden on 2012-06-12
I'm extracting some frames from a movie, the only problem is that I can't name the exported jpgs in a proper way.
Actally I'm using this script:

```
avconv -i End10040-0635.mp4 -qscale 2 -r 5 -f image2 -vcodec mjpeg temp[%3d]=pippo_monk_fragola_%3d.jpg
```

It works very well but if I use this name:
temp[%3d]=pippo_monk_fragola_%3d.jpg

It gives me an error because I use for two times the %3d that generate an increasing number of 3 digit.
If I use "%3d" only one time (ex.  temp[%3d]=pippo_monk_fragola.jpg" I get no problems.

How can I have the increasing number repeated two times in the name of the files?

---

