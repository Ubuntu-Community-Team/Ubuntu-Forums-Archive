---
title: "Cron daily"
date: 2011-05-28
forum: General Help
---

### Post by Lupajz on 2011-05-28
I am totaly confused of crontab setting :P Let's say I want to run info.sh from /home/xxx/bin/info.sh every day at 12 o'clock ?

---

### Post by Toz on 2011-05-28
0 12 * * * /home/xxx/bin/info.sh

Meaning the 0th minute, of the 12th hour, of every day of the month, of every month, of every day of the week ([http://en.wikipedia.org/wiki/Cron](http://en.wikipedia.org/wiki/Cron))

---

