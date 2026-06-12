---
title: "Xorg freezes for 60secs, intermittantly"
date: 2009-08-08
forum: General Help
---

### Post by raccoonone on 2009-08-08
I'm having problems with my computer freezing for 60secs (exactly), every now and then. I can't figure out exactly what triggers it, but it seems to be GUI interaction. Often opening a new window, or responding to an IM in Pidgin will cause a freeze.
The kernel is obviously not frozen because if I have music playing in Songbird it will continue playing, so I suspect this is a GNOME/Xorg issue.
While it's frozen the mouse does not respond, and keyboard presses aren't handled either. However keyboard presses are buffered, pressing Ctrl-Alt-F1 will switch to a terminal after it unfreezes.

Does anyone have suggestions as to how I can start debugging this? One this I've noticed is that it happens more often if I restart my computer, which leads me to believe this may be a time-out related to initialising something for the first time.

Some of my hardware specs:
Motherboard: P5B Deluxe
CPU: Core 2 Duo (E6400 I think)
RAM: 6GB, OCZ
Graphics card: 260GTX

---

### Post by raccoonone on 2009-08-11
I searched the forums, and it seems like some other people have had this problem but haven't found a solution. Anyone know how I could start debugging this?

---

