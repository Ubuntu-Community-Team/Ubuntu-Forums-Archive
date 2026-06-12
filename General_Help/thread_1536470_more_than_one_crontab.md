---
title: "more than one crontab?"
date: 2010-07-22
forum: General Help
---

### Post by SSzretter on 2010-07-22
I used 'sudo crontab -e' and added two jobs (the only two in there now).  

 I can tell they are running if I look at the processes at the specified time.   However, I wanted to see if there was a log entry for them.  

 So I looked at 'sudo grep CRON /var/log/syslog', and I see there is an hourly job running :

 ' CRON[3547]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)'

But I do not see my jobs, and I do not see this job in the crontab -e...  ?????

---

### Post by Ryan Dwyer on 2010-07-22
Try adding your job to /etc/crontab instead of using crontab -e.

---

### Post by aeiah on 2010-07-22
from what i remember, cron can remove entries from crontab that are malformed. perhaps this is the case here.

also, if you added stuff with sudo crontab -e (root's crontab), going into it with crontab -e (your own crontab) isnt going to display anything.

---

### Post by SSzretter on 2010-07-22
So my jobs are in sudo crontab -e, and the hourly jobs in the log are in /etc/crontab.

Good to know, thanks.

---

### Post by 8Kuula on 2010-07-22
Your crontab commands should be under your username, like backupping files in your home directory.
Only commands that require root access, like for example backupping system configs (/etc), should be under root's crontab.

---

