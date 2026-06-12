---
title: "No more scroll in gnome-terminal"
date: 2012-04-29
forum: General Help
---

### Post by SleepWalkerX on 2012-04-29
I upgraded from 11.10 to 12.04 and now when I use the gnome-terminal, there's no way to scroll up and see output from previous commands.  When I use my mouse scroll wheel it cycles through my command history.  

Is there a way to revert it back?

---

### Post by williejones on 2012-04-29
In the terminal you have to fill up the screen and then some for scrolling to become active.
After filling up the screen the left side should change colors.  Move your mouse to the left side to scroll with mouse wheel.  See screenshot:

---

### Post by SleepWalkerX on 2012-04-29
It still doesn't work.  :(

---

### Post by SleepWalkerX on 2012-04-29
Ah, I fixed it!  dpkg-reconfigure gnome-terminal did the trick  :D

---

