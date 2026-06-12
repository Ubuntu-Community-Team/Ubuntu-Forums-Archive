---
title: "karmic on dual screen, login is on wrong screen"
date: 2009-12-17
forum: General Help
---

### Post by juicymixx on 2009-12-17
Hey everyone,

I just did the upgrade to karmic from jaunty, and everything is excellent.   There's only one minor oddity that I've run into...   I'm on a dual-screen system, with the left most monitor as the 'dominant' monitor, and the right most monitor as an extension of the desktop (from the left).   The log-in panel that first appears, will appear on the right monitor, instead of the left (where I want it to appear).   After I log in, the Ubuntu loading logo pops up on the left screen (where I expect it to be).   Is there a way to tell the log-in panel to appear on the left screen?

Thanks!:KS

---

### Post by alex_o on 2009-12-25
this is because the cursor starts on the right, if you move the mouse left quickly it will be on the left where it should be

this is annoying me to, i have auto login and firfox autostarts on the right :(

---

### Post by alex_o on 2010-03-20
solution:

xte 'mousemove 640 512'

to move mouse to 640, 512 :p

---

### Post by juicymixx on 2010-05-18
Well, it has been such a long time since I started this thread...   I just lived with this problem, and recently moved to Lucid Lynx.   This problem is still occurring...

> **alex_o said:**
> solution:
xte 'mousemove 640 512'
to move mouse to 640, 512 :p

Thanks, Alex_O...   I'm not sure where to put this so it runs before the login screen pops up...

Any quick setting I need to check to fix my problem?:confused:

---

