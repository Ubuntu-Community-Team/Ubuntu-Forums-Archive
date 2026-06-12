---
title: "crontab issue"
date: 2012-05-30
forum: General Help
---

### Post by Drenriza on 2012-05-30
Hey guys.

I'am editing a crontab with the -e option.

```
crontab -e
```

And enter a entry as follows
```
31 * * * * /path/to/getOutput_script >> /path/to/log
```

But the script is not started at the specific time, and the log file is not populated.
The script is runnable with 777 rights. And i can run it by hand no trouble.

All commands in the script has its full path, example /bin/grep.
And i only use absolute paths for files and folders.

in the crontab i have tried to have a blank space after my entry and i have tried with no blank spaces. But nothing seems to work.

Is their anyone who can help me find a solution?

Thanks on advance.

---

### Post by ajgreeny on 2012-05-30
Is the script one which starts a GUI application?  If so you will need to specify that with an addition to the cron entry.
```
31 * * * * export DISPLAY=:0 && /path/to/getOutput_script >> /path/to/log
``` Change the display number to suit your own system; it's usually :0

---

### Post by Drenriza on 2012-05-30
> **ajgreeny said:**
> Is the script one which starts a GUI application?  If so you will need to specify that with an addition to the cron entry.
```
31 * * * * export DISPLAY=:0 && /path/to/getOutput_script >> /path/to/log
``` Change the display number to suit your own system; it's usually :0

It's a all based CLI application.

---

### Post by Drenriza on 2012-06-01
Anyone?

---

### Post by Sularco on 2012-06-01
If you run it in a terminal manually and it works and $PATH and the shell are all properly defined then your crontab entry must work. Is the cron daemon running?
If your script can be run on any Ubuntu machine, then post it here and I will try it on my box.

---

### Post by dthacker on 2012-06-01
What do the CRON entries in /var/log/syslog say?

Do you have any other cron logs in /var/log you could check? 

Cheers!
Dave

---

