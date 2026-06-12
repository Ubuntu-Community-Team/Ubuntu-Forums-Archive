---
title: "What software is needed after a mini install?"
date: 2009-11-03
forum: General Help
---

### Post by souteneur3190 on 2009-11-03
so far i have sudo apt-get install xserver-xorg openbox xterm (important things im forgetting) thunar firefox pidgin obmenu obconf

---

### Post by abyrne on 2009-11-03
ADD
synaptic - package manager
software-center - a more "cuddly" package manager
lxterminal - don't settle for xterm, no copy/paste, no tabs

REPLACE
xserver-xorg with xorg - xorg is a metapackage that install everything xorg-related
thunar with pcmanfm - well this one is my opinon. PCManFM is lighter and can provide a desktop. But it doesn't support shared-mime-info version 0.70 (you can downgrade to 0.60 by adding back the jaunty repo of archive.ubuntu.org and then saying force version in synaptic)

thats not all. thats just everthing i could think of. don't flame me for my choices

---

### Post by etnlIcarus on 2009-11-03
Firstly, shoud use aptitude.

Secondly, should be using the -R argument in aptitude or the --no-recommends argument with apt-get, if your goal is to have a minimal system.

Edit: Should also try xserver-xorg-core and just the drivers you need for your system.

---

