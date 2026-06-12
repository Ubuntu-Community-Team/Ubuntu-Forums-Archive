---
title: "high CPU usage after restoring from backup"
date: 2009-12-09
forum: General Help
---

### Post by ray field on 2009-12-09
after having some nasty troubles with gnome -- which my guess is now weren't so much due to X server but instead with a keyboard setting that wmctrl farked -- I happened onto a backup of this Intrepid installation on an eee PC which I'd made a couple months ago and restored it, & after changing some permissions with some help here, I'm pretty well up & running again.

except that for some reason, it's running really, really hot.  before, the cpu temp was about 49, 51 max -- now it's up to 65.  in fact it's bothering me enough, I just shut it down, let it sit for half an hour, and started it up again.  with nothing but Gnome, cairo-dock, and compiz-fusion running, GKrellM CPU0 shows from 75-90% usage, and after less than five minutes booted, the CPU temp is already up to 58 degrees C.

any hints how to diagnose?

---

### Post by ray field on 2009-12-09
just kicked up System Monitor, and everything is nearly idle except gnome-system-monitor, which is using between 10-50%  I just tweaked the "Nice" priority to 5, but it's still kinda hot

---

### Post by synapsys on 2009-12-09
Have you considered that it might be a coincidental hardware problem? Pop the case and check your fans, dust, and thermal grease.

---

### Post by john newbuntu on 2009-12-10
In case you haven't yet tried this, try installing powertop (sudo apt-get install powertop).  Run (sudo powertop) and see what it recommends.  For more details: [http://www.lesswatts.org/projects/powertop/](http://www.lesswatts.org/projects/powertop/)

---

