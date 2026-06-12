---
title: "Dual monitor issue"
date: 2009-09-22
forum: General Help
---

### Post by touch-n-go on 2009-09-22
Need Help,

I using two monitors on an nvidia card. When I am watching an online movie on my secondary monitor and switch it to full screen it opens up on my primary monitor. Does anyone know how to keep it on the secondary monitor? any help would be appreciated. FYI I am using latest version of ubuntu.



ty

---

### Post by scouser73 on 2009-09-22
Drag the screen across to the other monitor.

---

### Post by Grenage on 2009-09-22
> Does anyone know how to keep it on the secondary monitor?

I am in the same boat, some software remembers, some doesn't; some opens across both.  In the end I gave up, dragging where necessary, and when _really_ necessary I disable the second screen with xrandr.

---

### Post by touch-n-go on 2009-09-22
> **scouser73 said:**
> Drag the screen across to the other monitor.

Not possible. When I click to enlarge it pops up in my primary screen. The only thing you can do is hit escape to remove it. So again, how do get it to stay on the secondary monitor.

ty

g.

---

### Post by NoaHall on 2009-09-22
I use two xservers, and it works for me. Maybe try opening it from the terminal on the second one.

---

### Post by touch-n-go on 2009-09-23
> **NoaHall said:**
> I use two xservers, and it works for me. Maybe try opening it from the terminal on the second one.

New to using ubuntu could please walk me through this.

ty
g.

---

### Post by abhilashm86 on 2009-09-23
in system->administration, there is NVIDIA X server settings, you can easily control dual screens in GUI, its easy to configure and make changes,
if its not there, do install it, when you have nvidia drivers installed in system->administration->hardware drivers, its done automatically......

---

### Post by scouser73 on 2009-09-23
> **abhilashm86 said:**
> in system->administration, there is NVIDIA X server settings, you can easily control dual screens in GUI, its easy to configure and make changes,
if its not there, do install it, when you have nvidia drivers installed in system->administration->hardware drivers, its done automatically......

That needs to be done by root using this command: **gksudo nvidia-settings**

---

### Post by touch-n-go on 2009-09-23
> **abhilashm86 said:**
> in system->administration, there is NVIDIA X server settings, you can easily control dual screens in GUI, its easy to configure and make changes,
if its not there, do install it, when you have nvidia drivers installed in system->administration->hardware drivers, its done automatically......

OK. I am familiar with Nvidia settings. But I do not what changes to make, to correct this issue. Once again, If anyone knows,  please share.

ty

g

---

