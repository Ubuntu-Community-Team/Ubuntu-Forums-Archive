---
title: "bash script acting different when run from terminal vs cron"
date: 2011-08-30
forum: General Help
---

### Post by balance07 on 2011-08-30
hi all, i maintain the backup script for my company, but i can't get it to work right when launched from root's crontab.  here's the snip of code that's acting up:

```

#!/bin/bash -v
date=`date +%Y-%m-%d`
mavail=`df -m | grep dailybackup | tr -s ' ' | cut -f 4 -d ' '`
echo "Evaluating space available on backup drive..." >> /var/log/bkup_$date.log
spacereq100=`more /etc/scripts/prevbkupsize`
spacereq110=$(($spacereq100 * 11 /10))
echo "Size of previous backup =                    $spacereq100 MB" >> /var/log/bkup_$date.log
echo "Space required for tonight's backup (110%) = $spacereq110 MB" >> /var/log/bkup_$date.log
echo "Space available for tonight's backup =       $mavail MB" >> /var/log/bkup_$date.log
echo >> /var/log/bkup_$date.log
if [ $mavail -gt $spacereq110 ]; then
    echo "There is enough space on the backup drive.  Continuing..." >> /var/log/bkup_$date.log
  else
    echo "Making space on backup drive..." >> /var/log/bkup_$date.log
  fi

```

here's the log file output when i run it from the terminal ('sudo /etc/scripts/daily_bkup'):

```

Evaluating space available on backup drive...
Size of previous backup =                    98604 MB
Space required for tonight's backup (110%) = 108464 MB
Space available for tonight's backup =       181887 MB

There is enough space on the backup drive.  Continuing...

```

here's the output when ran from root's crontab ('/etc/scripts/daily_bkup'):

```

Evaluating space available on backup drive...
Size of previous backup =                    ::::::::::::::
/etc/scripts/prevbkupsize
::::::::::::::
99036 MB
Space required for tonight's backup (110%) =  MB
Space available for tonight's backup =       201048 MB

Making space on backup drive...

```

anyone got any thoughts? thanks!

---

### Post by b0b138 on 2011-08-30
try adding ```
MAILTO=""
```to the top of the crontab.

---

### Post by balance07 on 2011-08-30
@b0b138: OK I've done that, and the job will run overnight tonight, but in the meantime, can you explain why this will possibly fix the problem?

---

### Post by Wayne_V on 2011-08-30
I suspect it is because you are using 'more' when there is no attached terminal.

Change:
spacereq100=`more /etc/scripts/prevbkupsize`
To:
spacereq100=`cat /etc/scripts/prevbkupsize`

---

### Post by balance07 on 2011-08-30
@Wayne_V: thanks, i'll try that too!

---

### Post by sisco311 on 2011-08-30
> **balance07 said:**
> @b0b138: OK I've done that, and the job will run overnight tonight, but in the meantime, can you explain why this will possibly fix the problem?

If MAILTO is defined but empty (MAILTO=""),  no  mail will be sent. For more info, see: **man 5 crontab**.

I don't see how this has anything to do with your issue. 

I think Wayne_V is right, using cat instead of more should solve the problem.

---

### Post by b0b138 on 2011-08-30
I came across it when I was looking for a solution to a problem I had.  I had a command taking pictures for time lapse, but the command run through crontab would stop early, only taking 74 pics instead of 2-3000.

Im not sure why it works, but it did.

---

### Post by balance07 on 2011-09-01
script is running perfectly now, thanks everyone!

meow!

---

