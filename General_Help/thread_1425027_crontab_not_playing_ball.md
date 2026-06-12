---
title: "crontab not playing ball"
date: 2010-03-08
forum: General Help
---

### Post by Silas (son of Silas) on 2010-03-08
I have tried scheduling a script to run every 5 minutes on my server. Initially I tried with > sudo crontab -ebut that didn't work so I tried editing /etc/crontab

either way the script doesn't run.

Here's what I have put in my crontab, anyone have any ideas why it doesn't run? The script work perfectly if i execute it manually.

 > 
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user    command
17 *    * * *    root    cd / && run-parts --report /etc/cron.hourly
25 6    * * *    root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6    * * 7    root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6    1 * *    root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
#

0,5,10,15,20,25,30,35,40,45,50,55 * * * *  /home/silas/suspend.sh



---

### Post by rnerwein on 2010-03-08
hi
have a look in /var/log/syslog if your script was started by cron.
if yes you have a problem with your environment.
1. cron uses the /bin/sh
2. PATH is only /usr/bin and /bin
3. HOME and LOGNAME is set.
4. if your script needs any graphical stuff you have to set: export DISPLAY=:0.0 in your script.
hope this helps ( you must use: crontab -e because cron is informed that there is a new entry )
ciao

---

### Post by Silas (son of Silas) on 2010-03-08
Thank you for your reply. 

I can see from the log that it is attempting to run but nothing happens.

What do you mean by HOME and LOGNAME is set?

There is nothing graphical in the script, it just suspends the server to RAM if certain critera are met (no locked files, certain IP addresses don't respond to pings and certain apps aren't running)

---

