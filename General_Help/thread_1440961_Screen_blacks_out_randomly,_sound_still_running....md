---
title: "Screen blacks out randomly, sound still running... Please help"
date: 2010-03-28
forum: General Help
---

### Post by deusdies on 2010-03-28
I have:

AMD Phenom II X2 550 B.E. (4 cores active)
GIGABYTE MA770-UD3P
4 GiB RAM
ATI HD5750 1 GIG VRAM
Karmic

Catalyst 8.660 installed through EnvyNG

The problem is that the screen just randomly turns black. I'd be watching a movie and the screen just turns black (btw it's a desktop, so I'm using an external monitor connected via HDMI cable), but I can hear the sound still running. In this case, CTRL + ALT + BACKSPACE does nothing, neither does CTRL + ALT + F1. However, Alt + SysRq + REISUB works fine and the system reboots. 

I've been monitoring the CPU and the GPU temperatures, none of which are nearly critical (CPU is running at barely 30 deg and GPU about 45 - I have 5 fans in my case).

I tried installing the newest 10.3 drivers, but then I cannot make the image on my screen stretch (ie the resolution shows as 1920x1080 but there's a box around the desktop; it's just not right). I'll try 10.4 and see how that goes.

Anyone have any ideas?

Thanks!

---

### Post by bobcollard on 2010-03-28
> **deusdies said:**
> I have:

AMD Phenom II X2 550 B.E. (4 cores active)
GIGABYTE MA770-UD3P
4 GiB RAM
ATI HD5750 1 GIG VRAM
Karmic

Catalyst 8.660 installed through EnvyNG

The problem is that the screen just randomly turns black. I'd be watching a movie and the screen just turns black (btw it's a desktop, so I'm using an external monitor connected via HDMI cable), but I can hear the sound still running. In this case, CTRL + ALT + BACKSPACE does nothing, neither does CTRL + ALT + F1. However, Alt + SysRq + REISUB works fine and the system reboots. 

I've been monitoring the CPU and the GPU temperatures, none of which are nearly critical (CPU is running at barely 30 deg and GPU about 45 - I have 5 fans in my case).

I tried installing the newest 10.3 drivers, but then I cannot make the image on my screen stretch (ie the resolution shows as 1920x1080 but there's a box around the desktop; it's just not right). I'll try 10.4 and see how that goes.

Anyone have any ideas?

Thanks!
Under Administration Screensavers set your time higher.  Check Power Manager for Sleep, Hybernate or Suspend times.  Set to Never if you choose to.

---

### Post by deusdies on 2010-03-28
It's not the power management (already set to never + running caffeine to prevent sleeping).

I just updated the drivers to 10.3 and was able to resolve the underscan issue... simply by overscanning (don't ask). Off I go to watch The Lord of the Rings and hopefully you won't hear from me again. Thanks!

---

### Post by bobcollard on 2010-03-28
> **deusdies said:**
> It's not the power management (already set to never + running caffeine to prevent sleeping).

I just updated the drivers to 10.3 and was able to resolve the underscan issue... simply by overscanning (don't ask). Off I go to watch The Lord of the Rings and hopefully you won't hear from me again. Thanks!
If this is working for you please Edit your first post and add [Solved] to the Title.

---

