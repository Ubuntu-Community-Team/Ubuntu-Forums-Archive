---
title: "viewing images in firefox logs me out of ubuntu"
date: 2011-04-25
forum: General Help
---

### Post by eival on 2011-04-25
this has happened alot ever since i upgraded to 10.4 from 8.04 a few months ago but i could never pinpoint if it was precisely just images, but it happened again just now while i simply tried to load an image off Wikipedia

[http://en.wikipedia.org/wiki/File:Redsea_sandstorm_May13-2005.jpg](http://en.wikipedia.org/wiki/File:Redsea_sandstorm_May13-2005.jpg)

i clicked it to view the full resolution version and was instantly logged out of my session an taken to the login screen.

now i click it and it loads fine....

can someone please patch this, or tell me how to fix it, its very annoying since its completely random

---

### Post by eival on 2011-04-27
how does nobody know anything about this?

just happened again, ridiculously annoying...

---

### Post by hawthornso23 on 2011-04-27
If it is erratic then perhaps some sort of hardware triggered issue.
A memory problem perhaps? Try running memtest from the grub 
menu.

---

### Post by eival on 2011-04-28
> **hawthornso23 said:**
> If it is erratic then perhaps some sort of hardware triggered issue.
A memory problem perhaps? Try running memtest from the grub 
menu.

is there a faster way to run that test?

i let it run for like 30 minutes and it was only 40% done.

i have like 8 gigs of memory so idk if thats why it was going to take so long.

what about the hardware test in the System > Administrator menu?

---

### Post by eival on 2011-04-28
> **hawthornso23 said:**
> If it is erratic then perhaps some sort of hardware triggered issue.
A memory problem perhaps? Try running memtest from the grub 
menu.

is there a faster way to run that test?

i let it run for like almost an hour and it was only 40% done.

i have like 8 gigs of memory so idk if thats why it was going to take so long.

what about the hardware test in the System > Administrator menu?

---

### Post by hawthornso23 on 2011-04-29
Short answer is no - not if you want your memory tested properly. Any test run from inside ubuntu is going to be a lot slower and less efficient than memtest which has teh hardware to itself. I usually leave it running overnight. It loops back to the start after a while. But if you got to 40% complete without picking up any errors, you probably don't have a serious memory issue. Any serious problem will usually get picked up quicker than that.

---

### Post by eival on 2011-04-29
okay ill run it before i go to sleep, yeah i didnt have any errors up to that point

---

