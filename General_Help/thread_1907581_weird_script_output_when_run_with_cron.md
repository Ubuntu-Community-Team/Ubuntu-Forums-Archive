---
title: "weird script output when run with cron"
date: 2012-01-11
forum: General Help
---

### Post by netmonky on 2012-01-11
Hi All,

I planned on adding a quick script to cron to email me if a backup didnt run - this is only short term until I can amend the perl script to handle some errors. 

This might be a simple mistake but I just cannot see it! I can run the below command manually but when run via cron the $LASTBKUP variable displays 'Jan' instead of the date in format '20110111' -- any ideas why? 

its really annoying me :-(!

#!/bin/bash
#Quick script to email if backup doesnt run

BKUP_DIR='/share/BACKUPS/';
LASTBKUP=$(/bin/ls -ltr $BKUP_DIR | /usr/bin/tail -1 | /usr/bin/awk '{print $6}' | /bin/sed 's/\-//g');
MAIL='blahblahblah@gmail.com';
D=$(/bin/date \+\%Y\%m\%d);

if [ ${LASTBKUP} -ne ${D} ]; then
        echo "backup failed, Date:${D} , Last_backup: ${LASTBKUP}" | mail -s "backup failed" ${MAIL} ;
fi

---

### Post by amauk on 2012-01-11
```
#!/bin/bash
#Quick script to email if backup doesnt run

BKUP_DIR='/share/BACKUPS/';
LASTBKUP=$(/bin/ls -ltr [COLOR="Red"]--time-style="+%Y%m%d"[/COLOR] $BKUP_DIR | /usr/bin/tail -1 | /usr/bin/awk '{print $6}' | /bin/sed 's/\-//g');
MAIL='blahblahblah@gmail.com';
D=$(/bin/date \+\%Y\%m\%d);

if [ ${LASTBKUP} -ne ${D} ]; then
        echo "backup failed, Date:${D} , Last_backup: ${LASTBKUP}" | mail -s "backup failed" ${MAIL} ;
fi
```

---

### Post by netmonky on 2012-01-11
WOW - thats amauk! 

Any reason why cron would change the output?

---

### Post by amauk on 2012-01-11
no problem :)

It's not really changing the output, per se

The format that 'ls' displays timestamps in is configurable
Your user account is configured to display them as "YYYYMMDD"
When run via cron, the format is not configured that way

So the solution is to expressly tell 'ls' what format to show timestamps in
this is done by the --time-style switch
this eliminates any ambuguity

---

