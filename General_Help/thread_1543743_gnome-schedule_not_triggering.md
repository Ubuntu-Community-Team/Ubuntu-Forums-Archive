---
title: "gnome-schedule not triggering"
date: 2010-08-01
forum: General Help
---

### Post by Shay Guy on 2010-08-01
Scheduled Tasks is giving me a hard time. I have a command set for 23:00 daily as "gthumb -f ~/Pictures/ScheduledPic.jpg", but when the time rolls around, nothing happens. The strange thing is, it *does* work when I press "Run scheduled task." I get the same results if I select a different time or change it to "google-chrome ~/Pictures/ScheduledPic.jpg". My other scheduled task, a Perl script, works fine, though.

---

### Post by ajgreeny on 2010-08-01
The problem is that gthumb is a GUI application and a perl script is just that; a script.  You can either convert your gthumb command into a shell script and run that script with gnome-schedule, or you can simply select the X Application box in the task setting dialog, as in my screenshot.

---

### Post by Shay Guy on 2010-08-01
Thanks! I still haven't quite figured out all the layers of the operating system and how they interact.

---

