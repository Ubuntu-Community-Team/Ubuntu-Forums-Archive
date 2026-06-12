---
title: "fluxbox startup file"
date: 2006-03-10
forum: General Help
---

### Post by winter_mute on 2006-03-10
I generally prefer Fluxbox over GNOME, so one of the things I did was install Fluxbox once I got GNOME working how I wanted it to.  I installed it months ago, and when I was doing some work on it, I accidentally overwrote the ~/.fluxbox/startup script with something entirely different, and now Fluxbox won't start up at all.  Is there some place I can download this, or a nice script I can run to reset the startup file?

---

### Post by IYY on 2006-03-10
There's only one line that's important, I think:

**exec /usr/bin/fluxbox -log ~/.fluxbox/log**

Make that executable (chmod u+x startup), and everything should load just fine.

---

