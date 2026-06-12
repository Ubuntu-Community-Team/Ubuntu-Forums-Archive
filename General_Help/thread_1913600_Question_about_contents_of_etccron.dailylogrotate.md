---
title: "Question about contents of etc/cron.daily/logrotate"
date: 2012-01-22
forum: General Help
---

### Post by warmnscsi on 2012-01-22
So what should be listed in /etc/cron.daily/logrotate? I have a question that says to list when the logrotate utility will run but I am not seeing it when I type cat /etc/cron.daily/logrotate

This is what I see which to me just looks like an error but it's the actual contents of this file

> #!/bin/sh

/usr/sbin/logrotate /etc/logrotate.conf >/dev/null 2>&1
EXITVALUE=$?
if [ $EXITVALUE != 0 ]; then
    /usr/bin/logger -t logrotate "ALERT exited abnormally with [$EXITVALUE]"
fi
exit 0


---

### Post by Toz on 2012-01-22
> **warmnscsi said:**
> So what should be listed in /etc/cron.daily/logrotate?
You've listed the contents of the file below. logrotate is a script that executes the program "logrotate" whose purpose is to rotate logs. See:
```
man logrotate
```

> I have a question...
Homework??? 
> ...that says to list when the logrotate utility will run but I am not seeing it when I type cat /etc/cron.daily/logrotate
You won't, you're seeing the commands that will actually rotate the logs. The real question is "when are the contents of the cron.daily directory run?" Hint:
```
man cron
```

---

