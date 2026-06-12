---
title: "Moblock &amp; TTY Sessions"
date: 2009-08-09
forum: General Help
---

### Post by trench.me on 2009-08-09
When logged into tty sessions I receive "moblock is running" messages at regular intervals and I'm not sure why. I have to keep clearing the screen in order to get any work done. It's very annoying... 

Not sure if it matters but I use mobloquer as the frontend for moblock. 

Any help or ideas tossed at me would be greatly appreciated.

---

### Post by jre on 2009-08-11
That should be the watchdog. I hope to have fixed this in the next version.
Until then just stop the watchdog. See /etc/blockcontrol/blockcontrol.conf and /usr/lib/blockcontrol/blockcontrol.defaults

---

### Post by jre on 2009-08-12
Was it the watchdog?

Are you on Jaunty?
Can you please send me your /lib/lsb/init-functions.
If it was the watchdog, please reenable it and try with the setting LSB="" in /etc/blockcontrol/blockcontrol.conf

---

