---
title: "timed shutdown pop up"
date: 2011-01-27
forum: General Help
---

### Post by william_lane on 2011-01-27
I wrote a bash script that uses the shutdown command to shutdown in a time frame, in windows it has a pop up box that can't be closed and counts down. Can this be done in ubuntu? Thank You to anyone who responds.

---

### Post by sikander3786 on 2011-01-27
I don't have a specific answer to your original question i.e, a pop up window for shutdown.

However, I have got a few suggestions.

First of all, you can run the command directly in a Terminal and it will keep on counting down (after every 10 minutes) and will shutdown the system after the desired interval.

```
sudo shutdown -h +60
```

Where 60 is time in minutes.

Or, you can install 'gshutdown' from Software Center and use it for scheduling your shutdowns. It is a gui app.

---

### Post by ajgreeny on 2011-01-27
> **sikander3786 said:**
> I don't have a specific answer to your original question i.e, a pop up window for shutdown.

However, I have got a few suggestions.

First of all, you can run the command directly in a Terminal and it will keep on counting down (after every 10 minutes) and will shutdown the system after the desired interval.

```
sudo shutdown -h +60
```Where 60 is time in minutes.

Or, you can install 'gshutdown' from Software Center and use it for scheduling your shutdowns. It is a gui app.
Or you can specify a time ```
sudo shutdown -h 23:00
``` will shutdown the computer at 11.00pm.

If you use that command or put it in a shell script, the system indicator applet will warn of a shutdown going to occur, prior to the shutdown happening, I think.

EDIT:
NO, apparently no warnings are given except in the terminal that is running, which may be underneath other windows and invisible.

---

