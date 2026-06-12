---
title: "Power management doesn't care about the mouse. How to make it care?"
date: 2009-12-19
forum: General Help
---

### Post by siddartha on 2009-12-19
Running an app through dosbox means that the power management works for keyboard activity, but the mouse seems to be too suble for it to handle so it will go into standby. Is there a way to fix this stupidity?

---

### Post by rCXer on 2009-12-19
This may be the result of a [well know bug](https://bugs.launchpad.net/gnome-screensaver/+bug/32457). gnome-screensaver which is responsible for power management does not detect keyboard or mouse clicks in fullscreen sdl apps such as dosbox.  Unfortunatly there is no quick solution to this.  I had to fix this by [replacing gnome-screensaver with xscreensaver](http://ubuntuforums.org/showthread.php?t=195557).

---

### Post by dcstar on 2009-12-19
> **siddartha said:**
> Running an app through dosbox means that the power management works for keyboard activity, but the mouse seems to be too suble for it to handle so it will go into standby. Is there a way to fix this stupidity?

Try installing the **gpm** package.

---

### Post by siddartha on 2009-12-21
Well, it's worse than that report. The app is windowed and the problem still exist. For the full screen the reaction is idiotic - no reaction whatsoever and when you end up the dos app everything goes to sleep. The gnome guys are thinking with various body parts, anything but their heads. In the buggy screensaver they have the screen blanker and the screen locker as well. Just because they saw Windows doing that. I wonder - without a Windows to copy there won't be any Gnome.

As for gdm I will try it. It is quite weird to depend on that for propper mouse intercept when X is doing all the work, but because it is Gnome I believe that is very possible.

---

### Post by rCXer on 2009-12-21
> **siddartha said:**
> The gnome guys are thinking with various body parts, anything but their heads.

Now be nice ;)
If you think the problem is significantly different than the bug report, file a differnt one to help the devs out.

---

### Post by siddartha on 2009-12-22
> **rCXer said:**
> If you think the problem is significantly different than the bug report, file a differnt one to help the devs out.

Nope. I use the forums (not very helpful, usually I find the solution by myself later on) to find work-arounds. I have years of filing bug reports only to find out that I have to refill the same form over again because an overzealous user filed all bugs under "solved" because of a new version. And so on. At the moment I do that only for a few apps with a future. The rest is just a waste. Hehehehe, I remember back in the days when the evolution guys rejected quite violently the request for vim integration because they were pushing the (now useless) GtkHTML as a private ambition vs the working KHTML. The main argument was that Vim wasn't bonobo-able. Now bonobo is phased out... this is just a trend, next it will be another. When the time will come for them to ask for more details the most probable answer would be I switched to a working system... can't help you any further. And the bug would be closed just like it never existed. It won't be solved, but they will claim XX bugs solved with the new release. Disgusting.

---

### Post by siddartha on 2009-12-29
So, in short there is no solution. I would have closed the thread as solved, but that would be deceitful to the future readers. A system that needs libweather for the fast user switcher (something that XP had all along and without the weather option) and which depends on the screen-saver to do anything screen-related like screen locking, screen blanking... why not set the screen resolution in the screen-saver? So probably the developers would move to the next cool tech by the year 2020... and in 2025 there will be a solution hailed as "original" on slashdot. Long live the Linux desktop!

---

