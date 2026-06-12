---
title: "Screen resolution randomly changing"
date: 2010-05-06
forum: General Help
---

### Post by daranz on 2010-05-06
Ever since I upgraded to Lucid, I've been experiencing a bizarre problem with the screen resolution randomly changing.

Basically, seemingly at random, my laptop's (Acer AS1410) screen will go black. Then, it will flash back to X several times before finally settling on a resolution lower than the one before. Sometimes during those flashes I get a glimpse of the console (tty you see before GDM comes up if there's no splash, whatever you call that). Sometimes, it'll just seem to redraw all windows and Gnome-panel (window decorations stay, but windows go blank for a second then come back).

The thing I noticed, this seems to happen after the computer is idle for a time. I do not have a screensaver set, and one does not actually engage. But, the behavior seems to happen when I hit some keys after leaving my laptop untouched for a while. This usually surprises me, because I'll start typing and suddenly experience the screen spazing out. I do have screen going to sleep set for one hours in Gnome's power management preferences, but that seems to work fine itself.

I do not even seem to have an xorg.conf anymore (I believe it is now this way by default?), but I don't know whether I should blame X or something in Gnome.

I'd appreciate anyone shedding some light on this.

---

### Post by hewbert on 2010-05-21
I'm experiencing the same issue.  It generally occurs after closing the lid and opening it, but not every time.  The behavior is sporadic.  Sometimes opening the lid will just result in a black screen (backlight is on, though), but the other times the behavior you describe will happen - resolution jumping around.

This is also on an AS1410.

---

### Post by baleks on 2010-05-31
Similar issue, my 1410 after resume trying to change resolution to default one, and even when no external monitor connected, LCD blinks. When my desktop monitor connected, all blinks and desktop monitor appears virtually at the right of notebook LCD (need to press Win+F5 (my own xbindkeys shortcut) to set proper xrandr configuration)

That blinking happens not right after resume, but after i starting to press some keys after resume!

Such a thing happens NOT after EVERY resume, but sometimes.

---

