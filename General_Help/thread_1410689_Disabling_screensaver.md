---
title: "Disabling screensaver"
date: 2010-02-19
forum: General Help
---

### Post by mark9950 on 2010-02-19
How do I disable the screensaver?When I watch a movie the screen goes black.

---

### Post by NT4usB on 2010-02-19
```
killall gnome-screensaver gnome-power-manager
```

---

### Post by lidex on 2010-02-19
For a GUI: "Applications>System>Preferences>Screensaver"

Uncheck "Activate screensaver when computer is inactive"

---

### Post by NT4usB on 2010-02-19
> **lidex said:**
> For a GUI: "Applications>System>Preferences>Screensaver"

Uncheck "Activate screensaver when computer is inactive"

fwiw, I find this doesn't stop screensaver and/or power-manager from interrupting videos. For some reason Ubuntu thinks paused video=inactive computer.
My MythTV frontend is very annoying that way. If I disable those services, it still blanks.
If I wait too long after a restart, and the screen blanks once, killing or disabling doesn't prevent further blanking.
Only way I can get a display to stay visible on the TV is to restart, wait a few (but not too many) minutes then kill the processes. 
Then I'm good until the next restart...

Of course, your results may vary. Past performance does not guarantee future results. Consult your doctor before engaging in an exercise program. Void where prohibited. Not valid with any other offer.

---

