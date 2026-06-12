---
title: "Forcing 55hz refresh rate"
date: 2010-08-29
forum: General Help
---

### Post by Th0rn0 on 2010-08-29
Hey all,

Just got a spare computer running ubuntu. The monitor it has atm has a problem where the screen goes crazy, the colours flicker and there are lines all over. I'm pretty sure its the refresh rate as the monitor can only support 55hz and 60hz. However, Xserver wont allow me to go below 75hz. Can anyone help me on this?

Specs (very low I know ;D)
nVidia 7600GS
AMD 3200
2 gig ram
AMW M199D

---

### Post by davidmohammed on 2010-08-29
have you got the nvidia driver installed (administration - hardware drivers)?

If you do - you can normally have better control over stuff like refresh rate using the nvidia settings menu.

gksudo nvidia-settings

---

### Post by Th0rn0 on 2010-08-29
I have the nVidia X server installed. When I type gksudo nvidia-settings into the terminal it comes with with X server which is what I've used already. I can choose 60hz, 75hz and auto.

---

### Post by davidmohammed on 2010-08-29
choose the 60hz - save the config and reboot.  I wouldnt got below 60Hz since the flicker is bad enough to be unwatchable.

---

### Post by Th0rn0 on 2010-08-29
its at 60hz currently. I was wanting to force it to go lower. Hmm I think the monitor is just borked >_>

---

