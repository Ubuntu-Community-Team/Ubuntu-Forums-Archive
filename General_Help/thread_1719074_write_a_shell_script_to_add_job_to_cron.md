---
title: "write a shell script to add job to cron"
date: 2011-04-01
forum: General Help
---

### Post by shaoxiao on 2011-04-01
I write a shell script below to add a job to cron.

#!/bin/sh
touch date.cron
echo '*/3 * * * * /usr/sbin/ntpdate 192.168.2.3' >date.cron
crontab date.cron
rm date.cron

But i don't want to create the file date.cron. How can i add the job directly without creating the file.

---

### Post by shaoxiao on 2011-04-01
Bump&#65281;
No solution?

---

### Post by WorMzy on 2011-04-01
```
echo '*/3 * * * * /usr/sbin/ntpdate 192.168.2.3' | crontab -
```

You old crontab will be removed in the process.

---

### Post by shaoxiao on 2011-04-01
I appreciate it. Thank you very much. WorMzy

---

### Post by sj1410 on 2011-04-01
```

crontab -e

```

---

