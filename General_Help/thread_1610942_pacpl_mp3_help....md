---
title: "pacpl mp3 help..."
date: 2010-11-01
forum: General Help
---

### Post by $teve on 2010-11-01
I've converted some video files to mp3 using pacpl but I'm having problems playing them in my car & windows (the gf uses it not me lol). They play fine in ubuntu. Any ideas? Thanks.

---

### Post by maxsideburn on 2010-11-01
You converted VIDEO files to mp3?

You do realize one is video and one is audio right?

Why not just open your video files in something like Pitivi or Openshot, export the audio you want and encode to mp3?

---

### Post by $teve on 2010-11-01
Thats right; the video's are flv format & I want only the audio to play on an mp3 player or in my car. The method you suggested to extract the audio is fairly long-winded & not practical for me. It's ok though as this seems to take care of it:

```
ffmpeg -i INPUTFILE.flv -acodec libmp3lame -ab 128k OUTPUT.mp3
```

Thanks anyway.

---

### Post by fredwbauer on 2011-08-24
I ran into this problem. The version of pacpl in the Ubuntu repository doesn't encode to mp3, but mp2. To do what you want install lame and get the version of pacpl from SourceForge. ([http://pacpl.sourceforge.net](http://pacpl.sourceforge.net))

---

