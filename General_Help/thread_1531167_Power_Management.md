---
title: "Power Management"
date: 2010-07-14
forum: General Help
---

### Post by tripower on 2010-07-14
I have my Power Management functions set to keep the computer alive always when on AC power yet everytime I disconnect AC power my laptop immediately shuts down and the battery is fully charged. What gives?

---

### Post by mikewhatever on 2010-07-14
Seems to me a know issue.
> 
Ubuntu shuts down after unplugging Laptop power cord
A problem known with MSI wind and some Vostro users.

Current workaround is to open gconf-editor and browse to:
Code:

/apps/gnome-power-manager/general

And de-select the option use_time_for_policy

There is no need to restart, just close the configuration editor.

Source: [http://ubuntuforums.org/showthread.php?t=1469475](http://ubuntuforums.org/showthread.php?t=1469475)

---

### Post by mr clark25 on 2010-07-14
will it turn back on while it is unplugged? (just lights coming on, fans spinning up, etc.)

what version of ubuntu are you running?

if you think it is the power manager, you might try to remove it from the list of applications that run on startup. (no fully removing it, but removing the check mark beside it)


EDIT: i would see if the above post works first ;)

---

### Post by tripower on 2010-07-14
> **mikewhatever said:**
> Seems to me a know issue.

Source: [http://ubuntuforums.org/showthread.php?t=1469475](http://ubuntuforums.org/showthread.php?t=1469475)

Thanks, I think this worked but you have to reboot.

---

### Post by tripower on 2010-07-22
That did work but now when I leave my computer for any extended period of time the computer goes into permanent hibernation mode and I can't wake it back up.

---

### Post by tripower on 2010-07-23
bump

---

