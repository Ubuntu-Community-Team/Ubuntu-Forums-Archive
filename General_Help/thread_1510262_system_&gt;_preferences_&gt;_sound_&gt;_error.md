---
title: "system &gt; preferences &gt; sound &gt; error"
date: 2010-06-15
forum: General Help
---

### Post by rex141414 on 2010-06-15
When I go to system > preferences > sound, a window saying "waiting for system to respond" comes up. I was messing around with the sound preferences the other day and this happened after I changed one of the input devices, if I'm not mistaken.

I've tried un/re -installing pulseaudio several times, installing different mixers, and even recompiling ALSA. The only thing I haven't successfully finished is recompiling ALSA, but I'm a modprobe away from getting that done. Problem is, I don't know what to type in the last part of

```

sudo modprobe snd-____

```

I've got a Toshiba Satellite A505-S6969, so I'm running an intel centrino 2 with an ATI graphics card. The point there is that I'd think that I should just be able to throw "hda-intel" into that last part but that doesn't work.

An important note here: my sound DOES work - I just have to manually open up a mixer to control it, and can't change preferences outside of a terminal (also don't know how do do that from terminal). *My sound icon is also missing, even though the other icons that come with the indicator applet are there.*

Really not sure what to do at this point. I found a .deb package for alsa at [http://www.linuxant.com/alsa-driver/](http://www.linuxant.com/alsa-driver/), but still all the same problems. I'm not exactly an expert on linux/ubuntu, but I do feel I could follow even advanced instructions (I've been using it for years and have had to toy around with things in terminal on several occasions). Any help I could get with this would be **greatly** appreciated.

---

### Post by rex141414 on 2010-06-15
Ok, so modprobing did go through fine, but I still can't do anything about my sound preferences =( Any takers?

---

### Post by rex141414 on 2010-06-25
Ok, so I was just silly. After modprobing went through, I completely forgot to run alsaconf.

```
sudo alsoconf
```

 I can now access my sound preferences and alter everything just fine again (which means I can use my hard-button volume controls again!).

---

