---
title: "Banshee only converts flac to pcm"
date: 2011-07-12
forum: General Help
---

### Post by johnnyslogan on 2011-07-12
Hello everybody,

I have Ubuntu 11.04 and I have some music in flac-format. However, when I try to transfer that music to my ipod nano 5g using Banshee, I only have the option of converting it to pcm, not i.e. mp3. 

Is it possible to set Banshee up, so it converts flac to mp3 instead of PCM?

Best regards.

---

### Post by seawolf167 on 2011-07-12
I'm not sure about Banshee, but you can use *ffmpeg* to convert the files to mp3

```
ffmpeg -i *filename.flac* -ab 320k *filename.mp3*
```

---

### Post by johnnyslogan on 2011-07-13
Cheers mate. However I really would prefer, if Banshee could do it automatically, when required. And it kind of seems like it should be part of the options, when I right click on my iPod in Banshee.

Where it says something like 'convert to:' it looks like there could be other options in the drop down menu apart from pcm, but there is no other options in my drop down ... hope it makes sense.

Best regards

---

