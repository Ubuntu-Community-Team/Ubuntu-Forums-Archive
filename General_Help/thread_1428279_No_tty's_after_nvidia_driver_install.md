---
title: "No tty's after nvidia driver install"
date: 2010-03-12
forum: General Help
---

### Post by Klump on 2010-03-12
Hey, guys...

I know this might be rather a common problem, but none of the solutions I've found so far worked. Currently, my tty1 is just showing text from bootup, others show blinking cursor only and no login prompt whatsoever. So, here's the story. After installing recommended NVIDIA's drivers (185 that is) tty's stopped working (they were fine before). I've tried playing with vga=xxx setting under the grub configuration, I've tried gfxpayload=keep command also. I've even tried disabling nvidia's UseVBios setting and probably already tried all the possible GRUB resolutions with and without quiet splash, etc... None of them worked and I'm starting to loose faith to see my ttys ever again. Any lifebelt thrown down is highly appreciated.

Oh, right:

System: Ubuntu 9.10 Karmic
Video Card: 8600M GT (native screen resolution 1280x800 (@63 Hz)

---

### Post by Klump on 2010-03-13
Hi again, 

after tweaking settings all over again so far the best result was ttys with messed up colors all over the screen (still unusable) but there were no cursor at all. Any further ideas?

---

