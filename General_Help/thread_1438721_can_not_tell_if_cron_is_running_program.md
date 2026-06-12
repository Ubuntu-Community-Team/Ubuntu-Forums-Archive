---
title: "can not tell if cron is running program"
date: 2010-03-25
forum: General Help
---

### Post by LuniTux on 2010-03-25
hello,

i seem to be having a problem with cron.

I have a python program that checks a specific directory for pending email scripts written in python.

```


#!/usr/bin/python

import os
emaildir = os.environ['HOME']+"/email/"
filelist = os.listdir(emaildir)
for pyfile in filelist:
    if pyfile.find(".py") > -1:
        execfile(emaildir+pyfile)


```

This code has been tested and works fine.

the problem is that I need cron to run this code every 5 minutes but i can't tell if it is running:

here is my cron code:

```


5 * * * * /home/username/custom/CheckEmail.py >>/home/username/custom/email.log 2>&1


```

i activated the log (i think) but all i get is /var/log/cron.log and that only logs when i activate/deactivate or edit the cron file. is there anything else i need to set for this to work? I am running Ubuntu 9.10

Thanks

---

### Post by l.billon on 2010-03-25
Hi!
Cron usually logs its activity in /var/log/syslog

---

### Post by LuniTux on 2010-03-25
is there a way to redirect the log to /home/username/custom/email.log?

---

### Post by yeleek on 2010-03-25
If you are using 9.10 then cron logs should be redirected by default to 

cron.*				/var/log/cron.log

check /etc/rsyslog.d/50-default.conf

It is possible to redirect logs with rsyslog - I for example have this to redirect my fw logs

:msg,contains,"IPTABLES" /var/log/iptables.log

---

### Post by LuniTux on 2010-03-25
thanks

i redirected the log to my new area but i still am not getting any logs about the python scripts. is there something special to run python via cron?

---

### Post by yeleek on 2010-03-25
Would suggest you need to separate the problem into

1) Does the script run via cron - use system monitor?

and

2) rsysloging not as you'd wish.

To my knowledge putting #!/usr/bin/python as you've done should be sufficient.

---

### Post by LuniTux on 2010-03-25
i cant seem to find the cron program on the system monitor. i ran

```

$ sudo service cron start
start: Job is already running: cron
$ sudo service cron restart
cron start/running, process 4418

```

but still nothing.

is this written correctly?
```

5 * * * * python /home/username/custom/CheckEmail.py >>/home/username/custom/email.log 2>&1

```

---

### Post by LuniTux on 2010-03-25
I added the entries to cron via [COLOR="DarkBlue"]crontab -e[/COLOR]

when i check the [COLOR="DarkBlue"]/etc/crontab[/COLOR] file, the task i added is not there. should it appear there?

Here is my [COLOR="DarkBlue"]/etc/crontab[/COLOR] file
```

# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user	command
17 *	* * *	root    cd / && run-parts --report /etc/cron.hourly
25 6	* * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6	* * 7	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6	1 * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
#

```
and here is my [COLOR="DarkBlue"]crontab -l[/COLOR] response
```

$ crontab -l
# m h  dom mon dow   command
5 * * * * python /home/username/custom/CheckEmail.py

```

---

### Post by LuniTux on 2010-03-25
problem solved!!!

the cron job was not set properly

i had:

```
5 * * * * python /home/username/custom/CheckEmail.py
```

when i should have had

```
*/5 * * * * python /home/username/custom/CheckEmail.py
```

Thanks for the help

---

