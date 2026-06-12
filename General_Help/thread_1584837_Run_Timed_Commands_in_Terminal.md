---
title: "Run Timed Commands in Terminal"
date: 2010-09-29
forum: General Help
---

### Post by Greg Xix on 2010-09-29
I was wondering if there was a way for me to run a command in the Terminal at specific times? Like from a script or something?

For Example(not real):


*sudo ifconfig eth0 down*.....      <<<run that at 4 o'clock and 6 o'clock


How would I go about doing this?

---

### Post by CharlesA on 2010-09-29
Put it in a crontab.

---

### Post by DaithiF on 2010-09-29
Cron:
see [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

---

### Post by Greg Xix on 2010-09-30
Thanks for all of your help. 

Your info gave me a good starting point. I ended up installing the package: **gnome-schedule** from Synaptic(Also called Scheduled Tasks in the Software Center). This appears to be a pretty decent Graphical Front-end for Crontab related tasks. Making things a bit easier.


:KS

---

