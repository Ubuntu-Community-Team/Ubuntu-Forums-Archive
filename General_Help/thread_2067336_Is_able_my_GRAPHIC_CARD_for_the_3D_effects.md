---
title: "Is able my GRAPHIC CARD for the 3D effects?"
date: 2012-10-06
forum: General Help
---

### Post by MrBledi on 2012-10-06
Hello... i got this notebook... 
CPU: Intel Core i5 2450m
**VRAM: NVIDIA GT520MX gDDR3 1GB_HBR**
MEMORY: 4GB DDR3
HDD: 500GB
ODD: Super Multi Dual Layer (SATA)
... 

I want to find drivers for my graphic card and is it able to RUN 3D acceleration?? 
Cos it's strange, when i use windows go to DXDIAG and to displays it shows INTEL graphic cards but it got installed even nvidia drivers and pannel
Please help...  if you need other details please tell me...

---

### Post by akoskm on 2012-10-06
Hybrid graphics currently is supported by [bumblebee]("https://wiki.ubuntu.com/Bumblebee") and [ironhide]("https://launchpad.net/~mj-casalogic/+archive/ironhide/").
[Bumblebee or Ironhide?]("http://askubuntu.com/questions/108648/bumblebee-or-ironhide")

---

### Post by MrBledi on 2012-10-06
this two things... i should chose one of them by reading the article you tagged or what support my VRAM?

P.S: is it good my graphic card?

---

### Post by MrBledi on 2012-10-06
i'm starting installing this 
[B][Bumblebee]("https://wiki.ubuntu.com/Bumblebee") 
[/B]



then see what happens. i don't know what is or how to install the other one!

---

### Post by MrBledi on 2012-10-06
great... it worked... the bumble... bla bla bla 

now myunity is able ...
i'm a little bit confuse what is all this mess here, or what i've done, but now i will read all the stuf you told me and others! THANKS!

---

### Post by akoskm on 2012-10-07
> **MrBledi said:**
> great... it worked... the bumble... bla bla bla 

now myunity is able ...
i'm a little bit confuse what is all this mess here, or what i've done, but now i will read all the stuf you told me and others! THANKS!

This is mostly due to the fact that currently there is no official support from NVidia for hybrid graphics on linux.

Which is really bad and made linux/nvidia users really angry (including [Linus Torvalds]("http://www.youtube.com/watch?v=MShbP3OpASA&feature=youtu.be&t=48m10s")).

If you find that your problem is solved please mark this thread as [[SOLVED]]("http://ubuntuforums.org/showthread.php?t=1883734").

More info about hybrid graphics support:
[X Server 1.13 has Better Hybrid Graphics Support]("http://www.linux.com/news/hardware/servers/630065-x-server-113-has-better-hybrid-graphics-support")
[Hybrid graphics support in NVIDIA's Linux driver]("http://www.h-online.com/open/news/item/Hybrid-graphics-support-in-NVIDIA-s-Linux-driver-1697756.html")

---

