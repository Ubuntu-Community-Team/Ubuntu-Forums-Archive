---
title: "2 gfx cards, 4 monitors fails X fail cycles"
date: 2010-08-20
forum: General Help
---

### Post by jenkinsp on 2010-08-20
I have 2 nvidia gfx cards, if I use the nvidia settings tool to view 2 monitors with the same gfx card works fine, when i use one gfx card for one monitor and the other gfx card for the other monitor X doesnt start and just cycles through monitor flashes.

Any idea what could be the problem?

---

### Post by amauk on 2010-08-20
The nvidia proprietary driver provides no mechanism to drive more than 2 monitors on one X-screen

This is something only nvidia can address

You do, however, have options

1) Seperate X-screens

You run 2 x-screens
each x-screen uses 2 monitors (with nvidia's twinview)
The 2 x-screens are completely separate (you cannot drag windows between them)

Each x-screen (should) be able to do 3D acceleration


2) Xinerama
Xinerama was created ages ago, and provides a way to chain an arbitrary number of screens together

Xinerama long pre-dates 3D graphical acceleration, so you will have no desktop effects

Xinerama is however being phased out, in favour of RandR (a more modern equivalent)

Nvidia has a poor track record for RandR support, though


3) Use Nouveau

---

### Post by jenkinsp on 2010-08-20
Thank you, i'll give it a go.

---

