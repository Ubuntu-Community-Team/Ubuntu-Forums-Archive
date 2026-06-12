---
title: "Touchpad to big - can I disable the outer region somehow?"
date: 2010-06-20
forum: General Help
---

### Post by QwUo173Hy on 2010-06-20
I have this 17" Dell laptop, and the touchpad is huge. My family use it and when we're typing, we brush of this incredibly large touchpad and end up pumping characters into the middle of a prior paragraph.

They've reduced the size of the touchpad on the newer versions of this model, but I'm wondering is it possible to hack it somehow so the outer perimeter (say 1cm) is 'dead'?

Most configuration software available is of no use to me since I think it's not a synaptics mouse. (I don't have multitouch - that's why I think this)

This is really frustrating. Does anyone know how I can do this?

```
jarlath@vera-laptop:~$ dmesg | grep mouse
[    0.463142] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.626906] mice: PS/2 mouse device common for all mice
jarlath@vera-laptop:~$ lsmod | grep psmouse
psmouse                63245  0 

```

---

### Post by GregBrannon on 2010-06-20
Try Googling "dell touchpad off while typing" or something similar.  I tried it and got several promising hits.

---

### Post by QwUo173Hy on 2010-06-20
Thanks greg - but I don't want to disable it. I have "disable touchpad while typing" enabled already too. It's just that when I stop typing for a moment, the cursor then gets landed somewhere I don't want it. The touchpad is wider than the fullsize spacebar and its about 2.5 to 3 inches high. Craziness.

---

### Post by LacerdaPT on 2011-01-20
Hi. Your post was posted ages ago, but for you if you still have the problem or for anyone else that falls into this thread I think this can answer the problem: [http://art.ubuntuforums.org/showthread.php?t=886449](http://art.ubuntuforums.org/showthread.php?t=886449)

Cheers

---

### Post by LacerdaPT on 2011-01-20
Hi. Your post was posted ages ago, but for you if you still have the problem or for anyone else that falls into this thread I think this can answer the problem: [http://art.ubuntuforums.org/showthread.php?t=886449](http://art.ubuntuforums.org/showthread.php?t=886449)

The problem referred on the link is not the same as your, but with synclient you can define the regions. I was inspired by the post and I think you'll get the idea and use it to your problem.

Cheers

---

