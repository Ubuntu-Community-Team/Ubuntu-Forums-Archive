---
title: "gstreamer has encountered a general stream error in sound converter"
date: 2010-12-13
forum: General Help
---

### Post by jiggling_john on 2010-12-13
Hi,

I've been trying to get soundconverter to work on ubuntu 10.10, I've checked I've got all the restricted packages installed, gone into synaptic and installed a bunch of gstreamer stuff, downloaded and compiled the latest version of soundconverter but whatever I do, the following happens:

1. open soundconverter
2. open file (wav)
3. set to convert to mp3 (default)
4. Click convert and instantly get the ever so helpful "general stream error" message!

any Ideas?

---

### Post by TeoBigusGeekus on 2010-12-13
Try with ffmpeg:
```
ffmpeg -i filename.wav -acodec libmp3lame -ab 320k filename.mp3
```

---

### Post by jiggling_john on 2010-12-13
that works actually... thanks :)

But, it still doesn't solve the gstreamer problem...!

---

