---
title: "Default Monitor"
date: 2006-03-19
forum: General Help
---

### Post by bobpaul on 2006-03-19
I'm using TwinView for dual monitor support. Apps seem to open on the right screen about 75% of the time, but I tend to leave that monitor off when I don't need the extra desktop space to save on my power bills (70W is pretty sizable, that's like leaving the bedroom light on when you're not in there...).

Anyway, WinXP was pretty nice about it and if a window was not maximized when I closed it, that program would re-open on the same screen it was closed on. With Gnome windows seem to open wherever the hell they want, but usually on the right screen. Firefox download manager ALWAYS opens on the right screen, which is really annoying.

Meta modes work for things like Cedega, but because the actual screen resolution stays at 1280x2048 even though a screen is disabled, this isn't really a solution for day2day activities (scrolling monitor is more annoying than windows I can't see)

Is there anything I can do, save dropping TwinView for dual-x-servers that will make stuff behave a little more friendly? I'm open to the hackiest of hackish solutions; I'm fairly adept and really annoyed ;)

---

### Post by IYY on 2006-03-19
I had the same problem. I'm sure that there is a simple fix for this, but I just switched the two VGA cables, and in xorg.conf changed RightOf to LeftOf. Problem solved. ;)

---

### Post by Zector on 2007-06-09
I have the same problem, and no matter if I switch the cables or not.
I hope someone posts a solution soon, I've run out of ideas. ):

---

