---
title: "&quot;report_id X received&quot; message spam from kernel"
date: 2010-06-26
forum: General Help
---

### Post by N232 on 2010-06-26
Hello,

i've the problem that my log files gets spammed with "report_id X received" messages:

```
Jun 25 22:41:30 ubuntupc kernel: [  537.627864] report_id 0 received
Jun 25 22:41:30 ubuntupc kernel: [  537.627885] report_id 0 received
Jun 25 22:41:33 ubuntupc kernel: [  540.575626] report_id 1 received
Jun 25 22:41:33 ubuntupc kernel: [  540.575648] report_id 1 received
Jun 25 22:41:33 ubuntupc kernel: [  540.577549] report_id 1 received
```

and that about 30-60 times a every few seconds - ubuntu sometimes crashes because of that messages!

Is it possible to shut that messages off? everything is working fine - they just spam the log files and fill the disk...

---

### Post by MJae on 2011-11-08
I am experiencing the same problem right now.

Apparently, no one ever replied to this one. I've been trying to keep the disk space up by using logrotate -force but that doesn't really solve the problem.

How do I fix this?

---

