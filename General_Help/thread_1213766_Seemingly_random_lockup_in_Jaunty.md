---
title: "Seemingly random lockup in Jaunty"
date: 2009-07-15
forum: General Help
---

### Post by GrumpyBob on 2009-07-15
I've been using Jaunty on my Sony Vaio notebook since a couple of days after release.  This was installed as an upgrade from Intrepid.
Over the last couple of weeks, a problem has surfaced: at a seemingly random point after booting (anything from 4h to 35h), the system becomes unresponsive, with the keyboard and trackpad buttons being inoperable (so I can't drop to the command line).  The mouse cursor can still be moved around the screen.

In an effort to see what's happening to cause this, I've been looking at the log files, but I'm a bit hampered by not knowing what I should be looking for!

I'd really welcome a few pointers on which logs to focus on, and whether anyone else has experienced this problem.

---

### Post by GrumpyBob on 2009-07-16
Here's an update.  The lock up happened again this morning, about 1 minute into a scheduled backup to my home server.  I was able to log in to the notebook from the server, and the system still seemed functional (e.g. the backup completed and I was able to install update packages from the command line).

It would seem that what's hanging is the display, which is frozen except for the mouse pointer, and also the keyboard and trackpad buttons - as far as I can tell.

---

