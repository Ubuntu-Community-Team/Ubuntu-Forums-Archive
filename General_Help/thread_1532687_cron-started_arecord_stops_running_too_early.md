---
title: "cron-started arecord stops running too early"
date: 2010-07-16
forum: General Help
---

### Post by rndusr on 2010-07-16
I have a cronjob which is supposed to run every 15 minutes and record with arecord for 900 seconds. When I run the script manually, arecord record for 900 seconds, but when cron starts the script it stops recording after about 90-110 seconds.
 
Why?
 
```
 
rndusr@0x90:~/ralog$ cat rec.sh 
 
#!/bin/bash
YEAR=$(date +"%Y")
mkdir /home/rndusr/ralog/data/$YEAR
MONTH=$(date +"%m")
mkdir /home/rndusr/ralog/data/$YEAR/$MONTH
DAY=$(date +"%d")
mkdir /home/rndusr/ralog/data/$YEAR/$MONTH/$DAY
HOUR=$(date +"%H:%M")
arecord -f cd -d 900 -t raw | oggenc - -r --downmix -o /home/rndusr/ralog/data/$YEAR/$MONTH/$DAY/$HOUR
 
rndusr@0x90:~/ralog$ crontab -l
*/15 * * * * /home/rndusr/ralog/rec.sh
```

---

### Post by rndusr on 2010-07-16
When appended ">> debulog 2 >&1" to the crontab it suddently started working.
 
Sooo, problem solved I guess.. but I still wonder why?

---

### Post by DaithiF on 2010-07-17
> **rndusr said:**
> When appended ">> debulog 2 >&1" to the crontab it suddently started working.
 
Sooo, problem solved I guess.. but I still wonder why?
Hi,
cron was designed to mail the output of the commands it runs.  On desktop machines there often isn't a mailserver set up, so this doesn't happen.  cron still however, opens up a buffer and captures the output of the jobs it runs, with the intention of mailing the contents of that buffer.  If a job produces more stdout/stderr output than the size of the buffer it causes job execution to fail.  So the lesson is to redirect output for verbose jobs (as you have done).

---

### Post by DaithiF on 2010-07-17
also, the good news is that this bug has recently been fixed ([https://bugs.launchpad.net/ubuntu/+source/cron/+bug/151231](https://bugs.launchpad.net/ubuntu/+source/cron/+bug/151231)), so hopefully in 10.10 this will no longer be an issue.

---

