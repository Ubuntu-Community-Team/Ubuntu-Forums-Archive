---
title: "Ubuntu 10.04 doesn't go idle when it should"
date: 2010-05-02
forum: General Help
---

### Post by Stille on 2010-05-02
As it says on the tin. I have it set up to go idle after 5 minutes and ask for a password to unlock, and none of these happens.

---

### Post by WorMzy on 2010-05-02
The only thing that I can think of that might be causing this problem is: if you have a context menu open then gnome-screensaver won't work. Solution: close the context menu.

---

### Post by Stille on 2010-05-02
No context menu open either.

---

### Post by WorMzy on 2010-05-02
Silly question, but are you sure you've checked the "Activate screensaver when computer is idle" box under System -> Preferences -> Screensaver?

Also, run gconf-editor and have a look in /apps/gnome-screensaver to see if anything in there looks amiss.

My settings:
[[IMG]http://www.ubuntu-pics.de/thumb/55870/configuration_editor___gnome_screensaver_089_9Yu2Qj.png[/IMG]]("http://www.ubuntu-pics.de/bild/55870/configuration_editor___gnome_screensaver_089_9Yu2Qj.png")

---

### Post by Stille on 2010-05-02
Everything seems fine in both gconf-editor and the screensaver settings

---

### Post by mrintegrity on 2011-01-15
Have you got a right click menu (context menu) open at the time perhaps? 

[https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/49579](https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/49579)

---

