---
title: "Cron Problem"
date: 2006-02-09
forum: General Help
---

### Post by n00b2ubuntu on 2006-02-09
Hi,

I have a standard installation of Ubuntu 5.10 and I'm having problems with cron.

Basically all I want it to do is run a script at 03:00 each morning so I have the following crontab:

0 3 * * * /home/user/db_backups/do_mysql_backup

The problem is that I get the following mail from cron after the job was meant to run:

> From: [email]root@localhost.loca[/email]ldomain (Cron Daemon)
To: [email]user@localhost.loca[/email]ldomain
Subject: Cron <user@host> /home/user/db_backups/do_mysql_backup
X-Cron-Env: <SHELL=/bin/sh>
X-Cron-Env: <HOME=/home/user>
X-Cron-Env: <PATH=/usr/bin:/bin>
X-Cron-Env: <LOGNAME=user>
Message-Id: <20060209135001.C9E6C128AED@localhost.localdomain>
Date: Thu,  9 Feb 2006 13:50:01 +0000 (GMT)
Status: RO

: No such file or directoryups/do_mysql_backup


/home/user/db_backups/do_mysql_backup has execute permissions and works when called from the command line but it won't run from cron!

Am I missing something obvious? :confused:

---

### Post by BIS on 2006-02-09
Yes,

cron does not have the environment that you do when you run it from the command line.

type the command

env > /home/you/env.txt

and then copy all of the stuff in env.txt to the top of your /home/user/db_backups/do_mysql_backup script

---

### Post by n00b2ubuntu on 2006-02-09
Thanks BIS, tried but still the same error.

What does ": No such file or directoryups/do_mysql_backup" in the email mean? the message is scrambled somehow!

It seems to be saying it can't find the file /home/user/db_backups/do_mysql_backup and yet it is there and I can run it!

/home/user/db_backups/do_mysql_backup now contains:

```

TERM=xterm
SHELL=/bin/bash
USER=user
LS_COLORS=no=00:fi=00:di=01;34:ln=01;36:pi=40;33:so=01;35:do=01;35:bd=40;33;01:$
MAIL=/var/mail/user
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:$
LANG=en_GB.UTF-8
SHLVL=1
HOME=/home/user
LANGUAGE=en_GB:en
LOGNAME=user
LESSOPEN=| /usr/bin/lesspipe %s
LESSCLOSE=/usr/bin/lesspipe %s %s

mysqldump --opt --host=localhost -uuser -ppassword database > /home/user/db_backups/db_backup.sql
```

---

### Post by lamego on 2006-02-09
Are you sure the user on which you setting up the cron with has read/execute permission to the file ?
Is the file accessible to root ?

---

### Post by n00b2ubuntu on 2006-02-09
Yes, both the user and root can run '/home/user/db_backups/do_mysql_backup' from the command line.

However I have noticed this in the cron logs:

```

Feb  9 15:17:18 localhost crontab[20222]: (user) REPLACE (user)
Feb  9 15:18:01 localhost /usr/sbin/cron[7694]: (user) RELOAD (crontabs/user)
Feb  9 15:18:01 localhost /USR/SBIN/CRON[20228]: (user) CMD (/home/user/db_backu
ps/do_mysql_backup^M)

```

is the ^M causing the problems do you think? I am using pico to edit a crontab file and then importing it via 'crontab crontab.file'.

---

### Post by n00b2ubuntu on 2006-02-09
Yep, it was the pesky ^M!!!

Pico wasn't removing it when saving, so I recreated the crontab file, reimported it with crontab and now it works! :mrgreen:

---

### Post by jcl on 2006-02-09
Yeah, always use 'crontab -e' to edit crontabs... 'crontab -l' is useful too.

---

