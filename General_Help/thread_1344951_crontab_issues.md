---
title: "crontab issues"
date: 2009-12-03
forum: General Help
---

### Post by bitri on 2009-12-03
Hi,

I'm trying to run a php script every 10 minutes and am having major issues debugging my crontab. Right now, it looks like this:

```
*/10 * * * * /usr/bin/php /absolute/path/to/file.php
```

My php script (which accesses a db) runs fine from the command line, but is never run by cron. I tried using a basic write "hello world" to file php script, as well as using cron on a shell script that runs the php file, but neither of these are run by cron either.  My cron logs show that the command is running every 10 minutes though :

```

Dec  3 19:00:01 server /USR/SBIN/CRON[28559]: (user) CMD (/usr/bin/php /absolute/path/to/file.php)
Dec  3 19:10:01 server /USR/SBIN/CRON[28559]: (user) CMD (/usr/bin/php /absolute/path/to/file.php)

```

I did "ps aux | grep cron" which showed that cron was running ("/usr/sbin/cron
").  crond is not showing up however,  i'm not sure if this is supposed to be running as well.

Any suggestions?

Thanks.

---

