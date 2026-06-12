---
title: "first time cron job help pls"
date: 2009-07-09
forum: General Help
---

### Post by Ascenti0n on 2009-07-09
Hi all

I am attempting to setup my first cronjob.

I have created a bash script that backups up a couple of files. this script works fine if I execute it in a terminal.

I've tried the best I can to understand the CronHowto, but it's too much clutter for my tiny brain.

I have setup a folder in /usr/local/bin called cron_jobs and I have copied my bash script which is called daily-backups, to that folder.

I want to run this script every night a 7:00pm, is my crontab below correct?

0 19 * * * /usr/local/bin/cron_jobs/sh ./daily-backups.sh

Also, can someone verify if I need to adjust the cron paths to include /usr/local/bin?

thanks

---

### Post by credobyte on 2009-07-09
```
0 19 * * * /usr/local/bin/cron_jobs/daily-backups.sh
```This one looks more realistic ( weird slash-.sh-slash combination removed ) :rolleyes:

---

### Post by Ascenti0n on 2009-07-09
```
0 19 * * * /usr/local/bin/cron_jobs/daily-backups.sh
```

don't I need to add "sh" before "daily-backups.sh" to tell bash to 'run' the script?

---

### Post by credobyte on 2009-07-09
> **Ascenti0n said:**
> ```
0 19 * * * /usr/local/bin/cron_jobs/daily-backups.sh
```don't I need to add "sh" before "daily-backups.sh" to tell bash to 'run' the script?

No, you don't need to add "sh" ( it's an extension ).

---

### Post by Ascenti0n on 2009-07-09
I changed the time to test and run the cron job earlier and it didn't run.

Anyone know why this might be?

---

### Post by credobyte on 2009-07-09
1. Check [COLOR=Blue].sh[/COLOR] permissions ( should be executable )
2. Where did you added your cron-line ( probably [COLOR=Blue]crontab -e[/COLOR] ) ?

---

### Post by t4thfavor on 2009-07-09
in your script make sure you have the #!/bin/bash at the very top. then setup your cronjob using crontab -e

add 
```

0 19 * * * /path/to/your/file.sh >> /full/path/to/the/log.log

```

Then check the log.log file, and any output your script has will be there.

---

