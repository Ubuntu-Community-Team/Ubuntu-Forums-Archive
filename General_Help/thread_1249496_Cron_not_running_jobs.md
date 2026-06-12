---
title: "Cron not running jobs"
date: 2009-08-25
forum: General Help
---

### Post by geek-n-out on 2009-08-25
Hey Guys,


I have scowered the internet trying to find a solution, but nothing I find works.  I have a Cron job set up under the root user (yes I enabled root) and it refuses to run.  Trying everything to adding a line after the command.  The SH file runs fine from comand line, but just won't kick off.  Has anyone else run into this?

Jon

Ubuntu 8.04 64bit

---

### Post by DaithiF on 2009-08-25
can you post the cron file ?

---

### Post by geek-n-out on 2009-08-25
Sure no problemo...

```


# m h  dom mon dow   command
01 20 * * *  /var/lib/vmware/vmware.sh



```

---

### Post by DaithiF on 2009-08-25
I would suggest logging the output of the script to see whats happening:

```
01 20 * * *  /var/lib/vmware/vmware.sh >> /path/to/somefile.log 2>&1
```
it could be that the vmware script is relying on certain PATHs or other environment variables to be set, and crontab processes are run with a cut-down environment.  You can set environment variables at the top of the crontab to get around this, but first lets see what exactly is going wrong in the script.

---

### Post by geek-n-out on 2009-08-25
I thought about that, but I tried a test and it didn't even create the log file.  Not even sure if it tried to run.  Is there a way to tell?

---

### Post by DaithiF on 2009-08-25
check for activity in the logs here:
```
sudo grep -i cron /var/log/syslog
```

how did you create the crontab, like this?
```
sudo crontab -e
```

---

