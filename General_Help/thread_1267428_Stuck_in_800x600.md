---
title: "Stuck in 800x600"
date: 2009-09-15
forum: General Help
---

### Post by WinterMadness on 2009-09-15
My monitor and video card both handle 1080p, and thats the resolution while in windows. 

When I goto display, 800x600 is the best res. when I goto the shell and type xrandr -q it just says 800x600 is the best.

Why? jockey-gtk even says i dont have any restricted drivers in use... probably inaccurate 

I forget what the model name for my video card is, I know its  1gb, nivida and it comes with the asus cg2570 computer

---

### Post by overdrank on 2009-09-15
> **WinterMadness said:**
> My monitor and video card both handle 1080p, and thats the resolution while in windows. 

When I goto display, 800x600 is the best res. when I goto the shell and type xrandr -q it just says 800x600 is the best.

Why? jockey-gtk even says i dont have any restricted drivers in use... probably inaccurate 

I forget what the model name for my video card is, I know its  1gb, nivida and it comes with the asus cg2570 computer

Hi and you can use the command in the terminal ```
lspci | grep VGA
``` to identify the nvidia graphics card. Also what version of Ubuntu are you using?

---

### Post by uylug on 2009-09-15
Run the code the person above me said. It should tell us your video card model.

We can then install the drivers :D

---

