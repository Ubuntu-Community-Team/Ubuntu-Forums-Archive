---
title: "How to get Amarok to play Mp3."
date: 2010-10-21
forum: General Help
---

### Post by Jetso on 2010-10-21
I downloaded Amarok, but it won't play my MP3 songs. How to I get it to, is there a codec or something I need to download for this?

---

### Post by crisnoh on 2010-10-21
Had the same problem a while back.  Assuming you have restricted extras installed, I was able to resolve this by installing the phonon-xine backend.

---

### Post by mc4man on 2010-10-21
install libxine1-ffmpeg

```
sudo apt-get install libxine1-ffmpeg
```

---

### Post by olgis on 2011-02-10
> **mc4man said:**
> install libxine1-ffmpeg

```
sudo apt-get install libxine1-ffmpeg
```

 Thank you, work like magic.

---

### Post by luciano_sp5 on 2011-03-13
Hello, 
I'm new in Ubuntu. I had the same problem. There are some cases in which installing MPEG plugins directly from terminal don't work, becouse of sources settings I think. The solution would be:

*Applications - Ubuntu software center - Amarok - more info - check MPEG Plugins - Apply changes - Restart Amarok*.

Hope it can help you...

---

### Post by sagirfahmid3 on 2012-02-26
Much thanks!  sudo apt-get install libxine1-ffmpeg Worked perfectly on Mint 9 (Ubuntu 10.04)

---

