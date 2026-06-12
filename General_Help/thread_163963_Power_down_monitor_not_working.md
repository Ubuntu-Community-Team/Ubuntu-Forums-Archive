---
title: "Power down monitor not working"
date: 2006-04-21
forum: General Help
---

### Post by berlinbrown on 2006-04-21
I would like my monitor to power down after 20 minutes or so.  I can't find any settings through the screensaver or anywhere else to do this.

Right now I have it set to blank the screen, but ideally I would like to power down the monitor or standby it or whatever.

Any ideas?  So far, I have this:

Section "Monitor"
        Identifier      "DELL E770p"
        Option          "DPMS"
        HorizSync       30-70
        VertRefresh     50-160
EndSection

But, this still doesnt do it?

---

### Post by berlinbrown on 2006-04-21
Ok, I am trying this and then going to restart X:

xset dpms 1200 1200 1200

xset -q
DPMS (Energy Star):
  Standby: 1200    Suspend: 1200    Off: 1200
  DPMS is Enabled
  Monitor is On

---

