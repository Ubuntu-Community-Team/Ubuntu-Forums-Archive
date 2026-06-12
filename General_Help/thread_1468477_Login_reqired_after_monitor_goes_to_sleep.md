---
title: "Login reqired after monitor goes to sleep"
date: 2010-05-01
forum: General Help
---

### Post by spartan_87 on 2010-05-01
Hey I just did a fresh install of Ubuntu 10.04 yesterday and everything is working great!

One thing that is bugging me though is when the computer is idle and the monitor goes to sleep, I have to login again when I wake up the screen. It does this on my desktop and my laptop. The laptop even has automatic login and it still does this.

I have been trying to figure out how to get it so that login is not required after the monitor goes to sleep. Any ideas on how to do this?

---

### Post by SoulSurvivor on 2010-05-01
alt + F2

type in gconf-editor
then go to:
apps > gnome-power-management > lock

is there a box checked under blank screen?  If not, that's good, else uncheck it.

---

### Post by SoulSurvivor on 2010-05-01
Also check under your
system > preferences > screensaver menu (not in gconf-editor, from your desktop)
does it say to "lock screen when screensaver is active"

---

### Post by spartan_87 on 2010-05-01
Yep, "lock screen when screensaver is active" was checked under screensaver settings. Unchecked it and no more login. I was looking everywhere but there hehe. 

Thanks! :)

---

