---
title: "Cannot enter suspend or hibernate"
date: 2009-09-09
forum: General Help
---

### Post by LordVeovis on 2009-09-09
I have a Panasonic CF-73 with UNR installed on it.  When I try to suspend or hibernate the computer I get a blank black screen with a flashing cursor.  Not sure where to go next.

---

### Post by BFG on 2009-09-09
This is a known problem with Ubuntu.  No-one seems to know for sure how to fix it.  I struggled for weeks looking for an answer and gave up.

So - I'm also interested in any responses you get with this thread.  Good luck!

---

### Post by aesis05401 on 2009-09-09
> **BFG said:**
> This is a known problem with Ubuntu.  No-one seems to know for sure how to fix it.  I struggled for weeks looking for an answer and gave up.

So - I'm also interested in any responses you get with this thread.  Good luck!

Have y'all checked your logs for what errors are being thrown?

---

### Post by QIII on 2009-09-09
> **BFG said:**
> This is a known problem with Ubuntu.  No-one seems to know for sure how to fix it.  I struggled for weeks looking for an answer and gave up.

So - I'm also interested in any responses you get with this thread.  Good luck!

Hibernation difficulties are often caused by having a Swap partition that is smaller than the RAM, so the RAM state cannot be stored correctly.  Not a strictly "Ubuntu" issue.  Both have worked fine on my laptops, but I create a Swap partition at least 1.1 times the size of my RAM.

For the OP:

Did the machine originally come with the "other" OS installed and did it work there?

Doing a bit of reading on your machine, I believe it comes with some sort of switch somewhere to activate the suspend, resume and hibernate functions.[FONT=arial,verdana][SIZE=2][FONT=Arial][SIZE=2][COLOR=black][/COLOR][/SIZE][/FONT][/SIZE][/FONT]  It that properly set?

---

### Post by LordVeovis on 2009-09-09
> **QIII said:**
> Hibernation difficulties are often caused by having a Swap partition that is smaller than the RAM, so the RAM state cannot be stored correctly.  Not a strictly "Ubuntu" issue.  Both have worked fine on my laptops, but I create a Swap partition at least 1.1 times the size of my RAM.

For the OP:

Did the machine originally come with the "other" OS installed and did it work there?

Doing a bit of reading on your machine, I believe it comes with some sort of switch somewhere to activate the suspend, resume and hibernate functions.[FONT=arial,verdana][SIZE=2][FONT=Arial][SIZE=2][COLOR=black][/COLOR][/SIZE][/FONT][/SIZE][/FONT]  It that properly set?

It did indeed come preloaded with "other" stuff installed.  It also functioned in the alternate environment just fine.  as for a switch, there is nothing physical, maybe bios (looking now), but I do not think so.

EDIT:  Also the swap is set to nearly 2x the ram value.

---

### Post by LordVeovis on 2009-09-09
> **aesis05401 said:**
> Have y'all checked your logs for what errors are being thrown?

Which log would I check this in?  I read somewhere else to check an xorg log file, however it seems this log is re-written on every boot as it only had that boot's information in it's log.  The system has to be hard reset after I tell it to suspend or hibernate.

---

### Post by aesis05401 on 2009-09-09
I don't have a UNR install handy right now, but /var/log/pm-suspend.log is the place to look on standard Ubuntu installs.  This log is pretty easy to read, most lines should end either in 'success' or 'not applicable' IIRC.  

I can also post a script that will try to send the hibernate command directly through dbus and catch the reply in a logfile if you would like to try that... 

It occurs to me now that my HP desktop hangs at a blank screen with white cursor for up to 20 seconds on hibernate or suspend, then completes... Is it possible the machine is just hanging for a few?  How long have you left it on to check for completion?

---

### Post by LordVeovis on 2009-09-14
> **aesis05401 said:**
> I don't have a UNR install handy right now, but /var/log/pm-suspend.log is the place to look on standard Ubuntu installs.  This log is pretty easy to read, most lines should end either in 'success' or 'not applicable' IIRC.  

I can also post a script that will try to send the hibernate command directly through dbus and catch the reply in a logfile if you would like to try that... 

It occurs to me now that my HP desktop hangs at a blank screen with white cursor for up to 20 seconds on hibernate or suspend, then completes... Is it possible the machine is just hanging for a few?  How long have you left it on to check for completion?


I have left it to set there for several minutes before.  Could you send me the script, I'd like to see that as well.

---

