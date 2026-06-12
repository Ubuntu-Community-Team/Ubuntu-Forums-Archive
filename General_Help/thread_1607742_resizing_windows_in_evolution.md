---
title: "resizing windows in evolution"
date: 2010-10-28
forum: General Help
---

### Post by ugruntu on 2010-10-28
maybe this is something extremely simple and my brains are just mush after a whole night of struggling (and succeeding) with  wifi driver issues.

i'm running a brand new 10.10 netbook on a brand new asus eee 1015. i am trying to set up my email in evolution and the evolution windows are larger than the netbook screen, which means that the OK, SAVE, etc buttons are outside reach. i tried to resize, move window - resizing doesn't work and it only moves horisontally, not vertically. 

any obvious solution here that i am missing?

---

### Post by ugruntu on 2010-10-28
anyone?

---

### Post by linux-hack on 2010-10-28
juste try in a terminal this :
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by ugruntu on 2010-10-28
isn't that  video card software? how will that solve the fact that evolution windows cannot be resized? my current res is 1024X600 (16:9), which is presumably as high as it gets with a netbook. or is it?

---

### Post by ugruntu on 2010-10-28
by the way, VGA comp controller [0300] Intel Corporation N10 Integrated Graphics Controller (8086:a011)

---

### Post by Quackers on 2010-10-28
If you press the Alt key and then left-click and drag the screen, can you then see the buttons?
And Xorg is basically the method by which Linux handles your screen.

---

### Post by ugruntu on 2010-10-28
yes quackers, that helped. but still - an awkward thing to do on a small touchpad - any way to resize those windows as one pleases?

---

### Post by Quackers on 2010-10-28
I'm not vastly experienced in this kind of thing, but from what I've read it could be an Xorg problem. Sorry I can't offer any more than that. 
I seem to remember other people with something similar with a netbook. Have you tried the forum search, or Googling?

---

### Post by dcstar on 2010-10-29
> **ugruntu said:**
> maybe this is something extremely simple and my brains are just mush after a whole night of struggling (and succeeding) with  wifi driver issues.

i'm running a brand new 10.10 netbook on a brand new asus eee 1015. i am trying to set up my email in evolution and the evolution windows are larger than the netbook screen, which means that the OK, SAVE, etc buttons are outside reach. i tried to resize, move window - resizing doesn't work and it only moves horisontally, not vertically. 

any obvious solution here that i am missing?

Simplest this to do is change your Font DPI to around 62 (and then set it back to 96 afterwards).

That will allow the Evolution windows to fit while you go through the setup steps.

---

### Post by helliewm on 2010-11-09
From the Fedora forums I read ALT F7 to drag the windows around. It works I was having the same issue with Evolution too.

Helen

---

