---
title: "Techsmith tscc Codec"
date: 2011-03-03
forum: General Help
---

### Post by gavinjb on 2011-03-03
Hi,

Does anyone know if it is possible to install TechSmith tscc Codec under wine with WMP, I have some videos that are encoded with this codec and the only way I can think of to view these is to install WMP under wine and then the Codec.

Only problem is after doing this when I try and run the video in WMP I still cant view it.

Any ideas if what I am trying to do is possible, or am I going to have to build a Virtual Machine to view these videos?


Thanks,



Gavin,

---

### Post by jae18708 on 2011-05-23
FFMPEG + MPlayer should work..

---

### Post by andrew.46 on 2011-05-23
I believe this is the codec:

```


andrew@skamandros~$ **[COLOR="Red"]mplayer -vc help | grep -i tscc[/COLOR]**

camtasia    vfw       working   TechSmith Camtasia Screen Codec  [tsccvid.dll]

```

---

