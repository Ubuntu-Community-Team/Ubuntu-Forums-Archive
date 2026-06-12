---
title: "continous output last log messages like a ticker"
date: 2010-03-06
forum: General Help
---

### Post by pbrille on 2010-03-06
Hi,

I want to have a live-output of e.g. /var/log/syslog but with a filter (grep) so that all new messages are shown live as they are written into the logfile.

Normally I use sth. like:
cat /var/log/syslog | grep cron | tail

But this will only show the last new messages. I'd like the last messages continously showing up.

Can somebody help me?
THX

---

### Post by glepore70 on 2010-03-06
How about adding the -f switch to the tail command:
cat /var/log/syslog | grep cron | tail -f

-f means follow, seems to work.

---

### Post by glepore70 on 2010-03-06
Dang, tail -f doesn't work, back to the drawing board.

---

### Post by sisco311 on 2010-03-06
```
tail -f /path/to/file | grep "whatever"
```

---

