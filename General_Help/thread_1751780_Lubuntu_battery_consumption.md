---
title: "Lubuntu battery consumption"
date: 2011-05-07
forum: General Help
---

### Post by Zlatan on 2011-05-07
Hello,
I'm thinking of extending battery life on my netbook. Would battery consumption be better while using Lubuntu Natty instead of Ubuntu Natty?
Thank you

---

### Post by TenPlus1 on 2011-05-07
Installing Lubuntu will definately help your battery as it is a light desktop with no fancy 3d effects or unwanted programs draining your battery...

---

### Post by gradinaruvasile on 2011-05-07
You should also install laptop-mode that is a tool that lowers power consumption by turning off hard disks and tweaking certain system options (it has no gui interface, but it does its job nicely).

Other than that, make sure you have something that turns off the display (i mean turn off not just blank) - xscreensaver is very good at this.

Bear in mind that running flash sites (youtube etc) in Firefox or any other browser will drastically reduce the battery time. This is simply because flash is cpu intensive. Html5 video vieweing is no better right now.I recommend using flashblock or similar to disable the flash objects auto-loading (instead will be loaded on demand when clicked).
Only for firefox - there is a plugin that replaces youtube/vimeo videos flash objects with a video player instance (i recommend gnome-mplayer).

BTW The power-managers (gnome-power-manager, xfce4-power-manager) are overrated, since i installed xfce4 and dont run power managers i gained 30 minutes of battery time... (but this is on debian where are no gnome dependencies).

---

### Post by SteveDee on 2011-05-07
> **Zlatan said:**
> ...Would battery consumption be better while using Lubuntu?...

Well I can tell you that cpu% usage is lower on Lubuntu than on Ubuntu when both are doing nothing (i.e. no apps running). But will you notice the difference in battery life?

You might find that taking out some of your RAM (which you may be able to do with Lubuntu) and lowering the working brightness of your display may have a more noticeable affect.

---

### Post by Zlatan on 2011-05-07
Thanks guys.  So it is like that:
1- Lubuntu
2- disable some services (e.g. bluetooth, printing?)
3- try to add some RAM
4- laptop-mode
5- block flash (I have to use Gmail for my work and private mail so will have to check whether it is OK to block flash ;) )

Any more ideas for netbook battery saving? Probably some physical tricks to the battery like full charge, discharge, remove from netbook, etc.?

---

### Post by gradinaruvasile on 2011-05-09
You dont need to disable bluetooth service. Instead turn it off/on with rfkill.
Gmail does not use flash, only for ringing sounds or the like (it is specified on the config page).

---

### Post by idoitprone on 2011-05-09
I will say few things Avoid the 2.6.38+ kernels. There is a power regression and I believe Linus is pushing to fix it in the 2.6.39 release, but I am not too sure if it will be fixed.try a mininist install or a strip down distro, so all the services are only running for you own need which also saves battery life

---

