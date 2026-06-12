---
title: "Crontab - Is there a way to create a log sheet?"
date: 2009-08-30
forum: General Help
---

### Post by Roasted on 2009-08-30
I have a crontab command which auto-runs an rsync script twice a day. I was just curious if there's a way I can somehow have it write an entry every time it's ran in a simple FAIL / SUCCESS format with a time and date stamp.

I can easily tell if it ran simply by looking at my file systems in my system monitor, seeing as though the space used up in my home directory must match my backup hard drive identically, and it does.

But I was just curious if it was possible to somehow create that log file for crontab to reference each time it completes an action.

---

### Post by Liolikas on 2009-08-30
Look in /var/log you will see cron1 cron2 etc. files. HF with them.

---

### Post by DaithiF on 2009-08-30
depending on your setup, cron may just log to /var/log/syslog rather than to a separate cron log file.  But in any case, this may not give you what you want, as it only logs the commands executed, it does not (for me at least), log the exit status.

So I would suggest if you want to capture success or failure then you do that from your own script.  Test for errors along the way -- if any then log a failure by echoing a message & a timestamp to a logfile, and if no errors then echo out a success status.
```
echo "Success|Failure $(date)" >> /path/to/some/logfile.log
```

---

