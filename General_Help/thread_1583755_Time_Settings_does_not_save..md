---
title: "Time Settings does not save."
date: 2010-09-28
forum: General Help
---

### Post by cancer10 on 2010-09-28
Hi

I have installed Ubuntu 10.04 as a Windows Program on my machine. For some reason, the time does not gets saved. I set the time everyday and next time when I turn on my PC, ubuntu shows the old time. 

Its working fine when I boot in windows.

Is this a bug?


Kindly  help.


Thanks

---

### Post by quixote on 2010-10-01
Time is an important factor for the system, so only root (ie sudo) can actually set it.  If you set it as a regular user, then it only lasts for that one session.  When you try to set the time, do you get a button on that window that says "unlock"?  You need to click that and it'll ask for your password.  Then you'll be setting the time as root.

---

### Post by cancer10 on 2010-10-01
Nope, I do not get any button that prompts for password :confused:

---

### Post by sikander3786 on 2010-10-01
Try from System > Administration > Time and Date. You'll surely need root priviledges to edit it from there and most probably the settings will stay after a reboot.

---

### Post by gmargo on 2010-10-01
How far off is the time?  Is it the difference between UTC and your local time zone?  If so it's probably a wrong setting in the **/etc/default/rcS** file.  Search that file for the string "UTC=yes" (or no), toggle the value and reboot.  That flag indicates if the computer clock is set to UTC time or local time.

---

