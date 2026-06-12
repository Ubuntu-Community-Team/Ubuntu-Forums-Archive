---
title: "Graphics card reboot"
date: 2010-07-20
forum: General Help
---

### Post by oopsie on 2010-07-20
How can I reboot/restart my graphics card without having to restart ubuntu?

---

### Post by oustiti on 2010-07-20
Not sure exactly what you mean by restarting your graphics card, but if you are using gnome (ubuntu standard) then you can restart the window manager with :

> sudo /etc/init.d/gdm restart

Which might do the trick?

---

### Post by oopsie on 2010-07-20
I tried what you wrote, but it doesn't seem to work as far as I can tell. Thanks for your reply anyway!

By restarting my graphics card, I mean to just reset it without having to resort to rebooting my entire PC.

---

### Post by leptogenesis on 2011-07-21
I have the same problem--the issue for me is that vdapu slows way down after my laptop has been running for a while, to the point where even 720p is often unwatchable.  I find that suspending or hibernating will fix the problem temporarily, so I think the slowness is just caused by compiz filling up the graphics card's memory.  Hence why I'm looking for a way to restart the graphics card directly without suspending--suspending and un-suspending takes a while, especially when you're trying to show something in front of a group of people.

---

