---
title: "System locks up hard - how to figure out what happened?"
date: 2009-08-19
forum: General Help
---

### Post by bwooster47 on 2009-08-19
So I have (K)Ubuntu 9.04 installed for a while, and twice now, the system has completely frozen. The X display is dark, cannot open a shell (CTRL-ALT-F1 etc), cannot connect from other computers on the network.
This started at 4PM. And at 8PM, I noticed it and only way to get it back was to hit the reset button.

Then I went hunting for what could have caused the hang - looked in /var/syslog
Nothing in there. 
Though I find it strange - syslog shows that cron was active, fetchmail was active.
auth.log shows the same rate of script-kiddies trying to get into sshd, around 5 or 10 per minute (this is nothing more than what I see all the time, so can't be suddenly causing a complete system lockup).
But I cannot login to the box, can't see my X11 display.

So am stuck - is there something else I can try to detect what caused the lockup, and is there some other thing I can try to get the system back to normal if I do see this happen?

---

