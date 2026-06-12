---
title: "Cron not working"
date: 2006-04-26
forum: General Help
---

### Post by jorfermo on 2006-04-26
Hi all.

I'm trying to program some task through cron.

I've edited cronfile using "crontab -e" as root. I've added a test line like this one:

```
* * * * * /usr/bin/touch /tmp/`/bin/date +%H:%M`.tmp
```

It's supossed to create a file y /tmp which name is the hour and minute the task was executed. Cron is being executed:

```
# ps aux | grep cron
root      4684  0.0  0.1   1960   772 ?        Ss   12:50   0:00 /usr/sbin/cron
```


The result is nothing happens and nothing special is writed in /var/log/cron.log

Any idea of what's going on?

Thanks!!

---

