---
title: "how to cronjob"
date: 2011-04-27
forum: General Help
---

### Post by jithendra89 on 2011-04-27
hello?
i need to know how can i setup a cronjob for apache to run a php file inside /var/www/ directory..
:confused::confused::confused::confused::confused:
im using ubuntu 10.10 desktop edition...
thanks in advance...

---

### Post by dino99 on 2011-04-27
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

---

### Post by jithendra89 on 2011-04-27
ya i tried it but i dont understand it.. apache is run as www-data user in ubuntu right?
so how to setup and run the cron tab for www-data user?

---

### Post by jithendra89 on 2011-04-27
hello? anyone?

---

### Post by Lars Noodén on 2011-04-27
```

sudo -u www-data crontab -e

```
See the HowTo posted above by dino99 for more.

---

### Post by jithendra89 on 2011-04-27
now how to check cronjobs are running or not?

---

### Post by pqwoerituytrueiwoq on 2011-04-27
have it create a file (or edit one)
add this command as a task
```
date >> /path/to/chronTest
```

---

### Post by btindie on 2011-04-27
> **jithendra89 said:**
> now how to check cronjobs are running or not?
Check the log files
```
$ grep CRON /var/log/syslog
```

---

