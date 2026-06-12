---
title: "Graphics card overheating"
date: 2011-04-29
forum: General Help
---

### Post by Tomdarkness on 2011-04-29
Hey,

I'd like to point out that my graphics card (ATI 5770) works fine without overheating in Windows and has done so for over a year and I continue to use it fine when booting into windows for gaming sessions.

When watching flash videos on the internet for any extended period the computer just shuts down with the following message in syslog:

"kernel: [ 9351.460187] Critical temperature reached (90 C), shutting down."

And the graphic card cooler inside the computer is extremely hot to the touch.

Anyone got any ideas what would be causing it to overheat? (I'm thinking along the lines of fan control perhaps.)

Thanks :)

---

### Post by pqwoerituytrueiwoq on 2011-04-29
unless you can control the fan via software i would try a different driver
edit
[http://ubuntuforums.org/showthread.php?t=1341891](http://ubuntuforums.org/showthread.php?t=1341891)

---

### Post by KegHead on 2011-04-29
Hi!

Try a kernel update;

sudo apt-get update

sudo apt-get install linux-image -f

Restart.

Advise.

KegHead

---

