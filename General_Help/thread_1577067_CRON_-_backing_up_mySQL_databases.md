---
title: "CRON - backing up mySQL databases"
date: 2010-09-18
forum: General Help
---

### Post by Fynn on 2010-09-18
Hi,

Trying to set up a backup for mySQL databases in CRON.

I've entered the following line in /etc/crontab:

```

7 13    * * *   root    mysqldump -u root -pMYPASSWORD --all-databases | gzip > /home/myuser/mysql_backups/database_`date '+%Y-%m-%d'`.sql.gz

```

grep CRON /var/log/syslog shows:

```
Sep 18 13:07:01 5f9afe76 /USR/SBIN/CRON[23575]: (root) CMD (^Imysqldump -u root -pMYPASSWORD --all-databases | gzip > /home/myuser/mysql_backups/database_`date '+)

```

If I run the command outside of CRON, it creates the backups no problem, but CRON is not doing anything.

I'm new to CRON, can someone tell me what I'm doing wrong?

Many thanks in advance.

---

### Post by CharlesA on 2010-09-18
Is it in your crontab or roots?

Try doing this:

Dump the command into a script and set cron to run that script.

mysql.sh
```
mysqldump -u root -pMYPASSWORD --all-databases | gzip > /home/myuser/mysql_backups/database_`date '+%Y-%m-%d'`.sql.gz
```

I haven't actually put any commands directly into a crontab in ages, ever since I had problems with them being executed. Now it's just easier to dump the script into a file and tell cron to run the script.

---

### Post by The Cog on 2010-09-18
Two points:

Maybe you need to say /usr/bin/mysqldump rather than just mysqldump - I don't know if it needs the full path, but it's worth a try.

The log contains ^Imysqldump. Now ^I signifies a tab character, which wouldn't be visible in an editor but might be messing up your cron line. Try replacing all tabs with spaces.

---

### Post by Fynn on 2010-09-18
Thanks.

A combination of both of these answers did the trick.

---

