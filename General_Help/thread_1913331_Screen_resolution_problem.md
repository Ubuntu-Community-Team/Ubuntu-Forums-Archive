---
title: "Screen resolution problem"
date: 2012-01-22
forum: General Help
---

### Post by Splatted on 2012-01-22
Hi, I've been using lubuntu for about week now, but this morning the screen resolution suddenly changed. I'm not sure what it was on before, probably around 1024x768, but the highest I can set it to is now 640x480. I've searched for solutions to this problem, but none of them work because when I try and run xrandr I get this error message:

> xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 640 x 480, maximum 640 x 480
default connected 640x480+0+0 0mm x 0mm
   640x480        50.0* 
   320x240        51.0  
Does anyone have any idea what's gone wrong?

Thanks for any help.

---

### Post by SteveDee on 2012-01-22
> **Splatted said:**
> ...but the highest I can set it to is now 640x480...Does anyone have any idea what's gone wrong?

If you can boot your machine from a LiveCD/USB it may help determine whether its likely to be hardware or software related.

For example:-
 - if the display resolution is OK with LiveCD/USB then the problem is software/config related.
 - if the display is not OK with LiveCD/USB then the problem could be due to your graphics (card or integrated circuitry).

---

### Post by Splatted on 2012-01-22
Thanks for replying. I booted up with puppy linux and it all looked fine. I hadn't even considered that the computer itself might be broken, so that's quite a relief. XD

---

### Post by Splatted on 2012-01-25
I hope no one minds if I bump this, since it seems to have fallen in to obscurity.

---

