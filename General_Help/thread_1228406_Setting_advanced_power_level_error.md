---
title: "Setting advanced power level error"
date: 2009-07-31
forum: General Help
---

### Post by sdlyr8 on 2009-07-31
I'm currently running 2 monitors on my GeForce 6600, and am trying to hook up a third on a new graphics card (GeForce 8600). I keep trying to configure the third monitor and am having no success! Right now, when I try to enable the third monitor as a separate X screen, I restart, and the computer wont boot past a screen that keeps flashing a message...
> Checking battery state
/dev/sda
setting advanced power level
0xfe (254)

Not sure if it matters at all, but sda is a secondary hard drive. sdb is where Ubuntu lives...

What's causing this error or what should I be doing differently to get the third monitor to work?

---

### Post by dcstar on 2009-07-31
> **sdlyr8 said:**
> I'm currently running 2 monitors on my GeForce 6600, and am trying to hook up a third on a new graphics card (GeForce 8600). I keep trying to configure the third monitor and am having no success! Right now, when I try to enable the third monitor as a separate X screen, I restart, and the computer wont boot past a screen that keeps flashing a message...


Not sure if it matters at all, but sda is a secondary hard drive. sdb is where Ubuntu lives...

What's causing this error or what should I be doing differently to get the third monitor to work?

The text screen you see has nothing to do with your problem (misconfigured X server), it is just what is left to display when your graphics are not working correctly.

---

