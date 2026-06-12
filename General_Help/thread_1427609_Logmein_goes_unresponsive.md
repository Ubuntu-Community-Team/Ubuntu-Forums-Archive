---
title: "Logmein goes unresponsive"
date: 2010-03-11
forum: General Help
---

### Post by Rocket J Squirrel on 2010-03-11
I'm using Logmein ([www.logmein.com]("http://www.logmein.com")) on a laptop running Ubuntu 9.10, trying to connect to a remote Windows machine. 

I have no problem when I boot into Windows 7 on the laptop, using Firefox (3.6) and the Logmein Windows plugin. Works for hours.

However, when I boot into Ubuntu and try the same thing (using Logmein's Linux plugin for Firefox, with Firefox at namoroka beta level), I only get about two minutes of usability before the remote desktop freezes -- goes unresponsive. 

pkill firefox and re-launching and reconnecting to the remote machine restores operability, but only for a couple minutes again. 

Sometimes closing the FF tab with the remote session causes FF to crash entirely.

---

### Post by Rocket J Squirrel on 2010-03-13
The issue was resolved by updating the wireless adapter driver. See [http://ubuntuforums.org/showthread.php?t=1428858](http://ubuntuforums.org/showthread.php?t=1428858)

:D

---

