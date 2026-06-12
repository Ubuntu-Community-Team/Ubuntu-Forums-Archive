---
title: "Constant HD activity bogging me down!!!"
date: 2010-11-05
forum: General Help
---

### Post by phredbull on 2010-11-05
I'm using Lucid on a laptop, (details in sig). Often after I've been running Ubuntu for a while, like a few hours, my HD activity light will come on and not stop, causing my machine to become laggy. (A link might open 3-5 seconds I click on it, typing appears a second after I press the key, a window or dropdown menu might take 5-10 seconds to be drawn.)  I currently have Firefox with one tab and a Nautilus window open. Conky says the CPU is running at 10-20%, RAM is almost all used, (I assume Firefox's cache is filling up, since I've been surfing for a while), and swap is around 25% full. I just turned Compiz & Emerald off, but the HD is still spinning away. At this point, I usually log out and in again, or reboot. I though slowing performance with usage, resource-hogging background processes and constant rebooting were Windoze traits! What gives?!?
EDIT:
Apparently, this is caused by Update Manager. Unbeknownst to me, Update Manager was waiting for me to give it the go-ahead, but while it's open, instead of patiently waiting, it renders my computer unusably slow, even though it's not supposed to be doing anything. Any ideas why, and how to make it play nicely?

---

### Post by dcstar on 2010-11-05
> **phredbull said:**
> I'm using Lucid on a laptop, (details in sig). Often after I've been running Ubuntu for a while, like a few hours, my HD activity light will come on and not stop, causing my machine to become laggy. (A link might open 3-5 seconds I click on it, typing appears a second after I press the key, a window or dropdown menu might take 5-10 seconds to be drawn.)  I currently have Firefox with one tab and a Nautilus window open. Conky says the CPU is running at 10-20%, RAM is almost all used, (I assume Firefox's cache is filling up, since I've been surfing for a while), and swap is around 25% full. I just turned Compiz & Emerald off, but the HD is still spinning away. **At this point, I usually log out and in again, or reboot.** I though slowing performance with usage, resource-hogging background processes and constant rebooting were Windoze traits! What gives?!?
EDIT:
Apparently, this is caused by Update Manager. Unbeknownst to me, Update Manager was waiting for me to give it the go-ahead, but while it's open, instead of patiently waiting, it renders my computer unusably slow, even though it's not supposed to be doing anything. Any ideas why, and how to make it play nicely?

Ubuntu does a number of things on a scheduled basis (daily, monthly, weekly), some of these things wait a certain amount of time after a restart before commencing.

If you keep interrupting these scheduled tasks and never allow them to complete, they will keep restarting and trying to complete.

---

### Post by phredbull on 2010-11-05
Well, I've just been surfing these forums for a couple of hours, no music or video playing, 1 window, no tabs, and 1 file manager window, and as soon as the auto-updater opens up, the system starts crawling. I tried to patiently wait for the disk activity to stop, but after a half hour or so, it's still spinning away. Updater is not downloading or installing anything, and as soon as I quit it, things go back to normal.

BTW, aside from updates, what are these scheduled tasks of which you speak? Disk checks, or defragging, or cache clearing, or what?

---

