---
title: "AWStats Cron Issue"
date: 2012-03-07
forum: General Help
---

### Post by xathras1982 on 2012-03-07
Hi,
 
I followed the tutorial for installing AWstats on Ubuntu, [https://help.ubuntu.com/community/AWStats](https://help.ubuntu.com/community/AWStats) all looks fine. Except i see a lot of these in the my /var/log/syslog
 
Example:
 
 
Mar 7 06:30:01 ubuntu CRON[29828]: (root) CMD (/usr/lib/cgi-bin/awstats.pl -config=domain.info -update &gt; /dev/null)
Mar 7 06:30:01 ubuntu CRON[29829]: (root) CMD (root /usr/lib/cgi-bin/awstats.pl -config=domain.info -update >/dev/null)
Mar 7 06:30:01 ubuntu CRON[29827]: (CRON) error (grandchild #29829 failed with exit status 127)
Mar 7 06:30:01 ubuntu CRON[29826]: (CRON) error (grandchild #29828 failed with exit status 126)
 
If i run the command in sudo, I get the following:
 
sudo /usr/lib/cgi-bin/awstats.pl -config=domain.info -update &gt; /dev/null
 
[2] 8135
gt: command not found
-bash: /dev/null: Permission denied
root@ubuntu:~# Create/Update database for config "/etc/awstats/awstats.domain.info.conf" by AWStats version 7.0 (build 1.971)
From data in log file "/var/log/apache2/access.log"...
Phase 1 : First bypass old records, searching new record...
Direct access after last parsed record (after line 949)
Jumped lines in file: 949
Found 949 already parsed records.
Parsed lines in file: 0
Found 0 dropped records,
Found 0 comments,
Found 0 blank records,
Found 0 corrupted records,
Found 0 old records,
Found 0 new qualified records.
 
and for the other command, there is no issues if running manually. 
 
any ideas?

---

### Post by Habitual on 2012-03-07
```
sudo vi /root/myawstats.sh
```and add
```

#!/bin/bash
/usr/lib/cgi-bin/awstats.pl -config=domain.info -update >/dev/null [COLOR=Red]2>&1[/COLOR]
```
Save and exit.

```
sudo chmod 700 /root/myawstats.sh
```

Terminal >
```
sudo su -
crontab -e

```and add
xx xx * * *  /root/myawstats.sh > /dev/null 2>&1

Change xx xx to the desired interval.

---

### Post by xathras1982 on 2012-03-09
Hi,
 
I still see errors in the syslog and getting a failure email
/bin/sh: gt: not found/bin/sh: /dev/null: Permission deniedI don't see any listings in cron for all users, or in etc/cron.d, daily etc.  Any ideas?

---

### Post by xathras1982 on 2012-03-12
Ignore me... Sorry missed out the old one in /etc/crontab ;-)

---

