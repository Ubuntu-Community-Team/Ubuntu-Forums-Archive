---
title: "World of Warcraft Login Graphics"
date: 2010-12-01
forum: General Help
---

### Post by sk8erboy321 on 2010-12-01
Hey, I'm new to ubuntu, but i have wow running through wine, and everything is all good, except my log in screen is flashing funky colors, all i can see are the flames in the log in screen, when i log in I can't see my character's bodies, and if i try logging in the world on a character, as soon as the world loads it crashes.  Some wine error comes up.  

[U]Things I've Tried
[/U]
[LIST=1]
[*]SET gxAPI "openGL" (and the other SET fixes like glow and what not)
[*]Got my video card's vendor and device IDs and Changed the registry to reflect those IDs. (regedit)
[*]Made an OpenGL key for regedit
[/LIST]
[U]Computer and Video Card Specs
[/U]
[LIST=1]
[*]Computer: Inspiron 1545 Laptop
[*]Video card:                       p { margin-bottom: 0.08in; }  00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)
[*]Ubuntu version: 10.10
[/LIST]

---

### Post by sk8erboy321 on 2010-12-01
Below is a screen shot of my login screen if it helps.

---

### Post by sk8erboy321 on 2010-12-02
Anyone? Please? I really want to get this working.

---

### Post by HiImTye on 2010-12-02
try cleaning your GPU fan and also check out the winehq page for WoW, there's lots of stuff at the bottom to troubleshoot with

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=20549](http://appdb.winehq.org/objectManager.php?sClass=version&iId=20549)

---

### Post by sk8erboy321 on 2010-12-02
Tried both of those, still no luck :( thanks for trying though.

---

### Post by HiImTye on 2010-12-02
you tried every option in the link at the bottom? and you also cleaned out your GPU fan and heat sink? you are one fast mofo!

---

### Post by HiImTye on 2010-12-02
oh yeah try deleting your cache too
```
world of warcraft/cache/
```

---

### Post by sk8erboy321 on 2010-12-02
Haha, I meant I had tried all of those methods before I even made this thread :P and thanks for some more ideas, I tried them too but still nothing.  I emailed bliz tech support because I saw they solved a few ubuntu issues for some people.

---

### Post by Immolatus on 2010-12-02
Try disabling the desktop effects. It may not look like it but they are on by default. They used to give me a hard time running those and flash at the same time on my old laptop.

---

### Post by sk8erboy321 on 2010-12-03
What desktop effects are you talking about? The 3d cube? or what?

---

### Post by BjOrN Ultimatum on 2010-12-19
I am having the same probalem... same exact screen. i tried to change the wow video settings and nothing worked. and i cant even find what my graphics card is. I have a vaio vgn-fw260j i looked everywhere. all i know is that i have an intel chipset and linux doesnt configure it or something

---

### Post by DarkAmbient on 2010-12-19
> **sk8erboy321 said:**
> What desktop effects are you talking about? The 3d cube? or what?

I think he means that, by default (after you've installed graphic drivers) you get the "normal" settings under 'visual effects'. Try set it to 'none'.

---

