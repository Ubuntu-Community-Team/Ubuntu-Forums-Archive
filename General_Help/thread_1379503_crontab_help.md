---
title: "crontab help"
date: 2010-01-12
forum: General Help
---

### Post by wsp_scott on 2010-01-12
I have a cron job that I set up with crontab following this page [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto) It sucessfully runs based on both the log the script creates as well as syslog. 

My problem is that there is no crontab. When I type "crontab -e" I get "no crontab for scott - using an empty one". I also tried "sudo crontab -e", again "no crontab...". How can I change my existing cron jobs if there is no crontab? 

I don't know if it matters, but I am using 9.04.

*** this was what my crontab looked like ***
01 01 * * 0-6 /home/scott/backup/scripts/local-backup-daily
01 05 * * 7 /home/scott/backup/scripts/s3-backup-weekly
************

---

### Post by Puck7 on 2010-01-12
Being on 9.04 I tried this myself.

Typing 'crontab -e' will tell you:
```
no crontab for <username> - using an empty one

Select an editor.  To change later, run 'select-editor'.
  1. /usr/bin/vim.tiny
  2. /bin/ed
  3. /bin/nano        <---- easiest
```

So if you press '3' then ENTER, you'll get to see the crontab file and setup the cron jobs.

---

### Post by drs305 on 2010-01-12
If you set it up as 'root', have you tried running "sudo crontab -e"?

---

### Post by wsp_scott on 2010-01-12
> **drs305 said:**
> If you set it up as 'root', have you tried running "sudo crontab -e"?

I did try "sudo crontab -e" since I wasn't sure if I set it up as root, this also yields "no crontab..." When I look at /var/log/syslog it shows that it is running under my username.

---

### Post by hwttdz on 2010-01-12
You can try "crontab -r" which removes the current crontab.  Maybe it's for some reason using a different file?  

You could also edit "/home/scott/backup/scripts/local-backup-daily" to be
#!/bin/bash
whoami > /home/scott/crontab-info.txt
pwd >> /home/scott/crontab-info.txt
#whatever else you might be interested in knowing

of course if you're not really scott or root then it might have trouble writing there.

---

### Post by wsp_scott on 2010-01-15
> **hwttdz said:**
> You can try "crontab -r" which removes the current crontab.  Maybe it's for some reason using a different file?  

You could also edit "/home/scott/backup/scripts/local-backup-daily" to be
#!/bin/bash
whoami > /home/scott/crontab-info.txt
pwd >> /home/scott/crontab-info.txt
#whatever else you might be interested in knowing


"crontab -r" said no crontab for scott

I also tried changing the script (thanks for the idea), and now I am more confused. Now the script doesn't run, i.e. no crontab-info.txt was created and nothing appears in syslog. However, it still looks like something is going on from Amazon's POV (I am using AWS S3 to backup files). I am going to explore a little more and see if I can figure this out.

---

### Post by hwttdz on 2010-01-15
Can amazon tell you the ip address of where this is coming from? maybe you put the script in the crontab of a different machine?

---

