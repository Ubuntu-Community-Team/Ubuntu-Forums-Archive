---
title: "Execute Python Code before shutdown"
date: 2010-12-02
forum: General Help
---

### Post by pajoohesh on 2010-12-02
Dear folks,

I have written a backup script backing up the data I have worked during the day with rsync and sends me a log in my email. now it works perfect but i want to execute it each time i shutdown my computer in the evening not during reboot or logout. 

It seems that i can not run it by putting it in init.d and softlinking in rc0.d as K00backup. I think it is because script uses many services like python or smtplib, gnome-keyrings that in that time might have been already shutdown. Any idea what I can do?

Thanks

---

### Post by pajoohesh on 2010-12-03
OK. I gave up doing that for the moment. I put my script in user cron tab (crotab -e), but it is not executed completely to the end. 
```
SHELL=/bin/bash
PATH=/sbin:/bin:/usr/sbin:/usr/bin:/usr/local/bin
00 18 * * * "/home/user/Documents/bash Scripts/backup.py"
```

The part which does not work is reading password through gnomekeyring and send email using smtp to my gmail. What should I add to cronjob to execute it properly??

Thanks

---

### Post by pajoohesh on 2011-01-10
Hey folks,

The gnome-terminal which is executed from crontab is completely different from what I run in gnome. it does not have most of the env variables. I think this is the cause of the problem in which I can not access gnome-keyring to extract a password. any idea here????

Thanks

---

