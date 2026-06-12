---
title: "Ubuntu keeps logging me out"
date: 2010-08-26
forum: General Help
---

### Post by Deer Hunter on 2010-08-26
Why does my Ubuntu 10.04 keep automatically logging me out after only a few minutes of inactivity?  I would really like to change that.

---

### Post by M4he on 2010-08-26
You mean you need to type in your password after you've interrupted the screensaver?

Go to System -> Settings -> Screen Saver and uncheck the "lock screen when screen saver is active" (or something similar, coz i don't know what the actual english sentence is.)

---

### Post by sikander3786 on 2010-08-26
> **M4he said:**
> You mean you need to type in your password after you've interrupted the screensaver?

Go to System -> Settings -> Screen Saver and uncheck the "lock screen when screen saver is active" (or something similar, coz i don't know what the actual english sentence is.)

Yes that is the screensaver. Either turn it off, or extend its time or set it to resume without password.

---

### Post by Deer Hunter on 2010-08-26
Okay, thanks guys, I'll try that out.  That sounds like what the issue is.

---

### Post by Axis Mann on 2010-11-23
You never did respond back.  I'm wondering if it isn't something else.  I've noticed that if you open a browser window, but don't maximize it, that your x session will crash if your machine is idle for a length of time.  If you then look in the syslog, you will find a render error.  You can tell that x session crashed because your desktop will subsequently display the GDM logon prompt.  If I maximize my browser before the machine goes idle, I don't see this behavior.  Try this: set your computer idle time to one minute, check the Activate screen saver box when computer is idle, and in  power management dialogue, set Action to never and Display to 5 minutes.  Next, close everything but a browser window which you don't maximize and see if that don't crash your x session after a while of inactivity.  If it crashes, then I doubt that it's got anything to do with the lock screen when screen saver is active option.  This doesn't seem to happen when the browser screen is maximized, just when it isn't.

---

### Post by Axis Mann on 2010-12-09
After further use, I've noticed that X only seems to  crash when I have the "Put Display to sleep when inactive" option selected under power management and I was running firefox before the machine went inactive.  I set the option to Never and the crashes seemed to have stopped for me.

---

### Post by alabandit on 2011-02-18
having the same problem here. seems to have been solve be disabling the power saving on screen inactivity... seriously not impressed.

---

