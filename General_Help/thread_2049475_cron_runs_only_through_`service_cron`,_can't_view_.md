---
title: "cron runs only through `service cron`, can't view logs"
date: 2012-08-28
forum: General Help
---

### Post by ellmo on 2012-08-28
Hey there, I have a virtual server that runs Ubuntu 12 and I have a problem with **cron**.
The OS was basically naked when I got the server so I never had to install **cron**, it was there from the beginning.

I can **start / restart / stop** cron via **service cron `option`**, but whenever I try to simply run **sudo cron** I get a

```
cron: can't lock /var/run/crond.pid, otherpid may be 14560: Resource temporarily unavailable
```

Before I ran **service cron start** I had no **cron** or **crond** process running. Now I have:

```

$ ps ax | grep cron
> 14560 ?        Ss     0:00 cron
> 14727 pts/0    S+     0:00 grep --color=auto cron

```

I put a test task in **crontab**:

```
* * * * * touch touch_me.txt
```

And I could see that the file is touched every minute, but I also have a task in my crontab that is supposed to make weekly backups of a selected database:

```
30 21 * * 2 mysqldump -u root --password=[le_password] le_database | gzip > backup/le_database_`date +'%m-%d-%Y'`.sql.gz
```

To my knowledge (*and I have only started using cron today*) it should fire on each tuesday, at 9:30PM, but I haven't seen it make an automatic sqldump yet, so I'd like to know why it didn't work, but there's no way I can read the logs.

The file **/var/log/cron** does not exist, even tho **cron** was obviously touching the file mentioned previously.

Can you tell me what am I doing wrong?

---

### Post by spjackson on 2012-08-28
> **ellmo said:**
> To my knowledge (*and I have only started using cron today*) it should fire on each tuesday, at 9:30PM, but I haven't seen it make an automatic sqldump yet, so I'd like to know why it didn't work, but there's no way I can read the logs.

The file **/var/log/cron** does not exist, even tho **cron** was obviously touching the file mentioned previously.
I agree with 9:30pm on Tuesday.

With the default Ubuntu install, the job details are logged in /var/log/syslog and an entry also goes to /var/log/auth.log, However, syslog can be configured to do otherwise.

---

