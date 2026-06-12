---
title: "cronjob not running properly"
date: 2009-07-13
forum: General Help
---

### Post by Krijk on 2009-07-13
I have a problem with a cronjob that isn't running properly.

Added the job with crontab -e to run a bash-script periodically.

The part that doesn't work in job.sh is:
```

echo "***** $(date +%Y%m%d_%H:%M) START JOB*******************" >>$logfile
/data/maintenance/job_to_run.py >>$logfile
echo "$(date +%Y%m%d_%H:%M) job is finished" >>$logfile

```

In the logfile I see that the job has started (echo 1) and finished (echo 2) but the python script hasn't run. The output to logfile is for troubleshooting purposes.

When i run it manually with ./job.sh it works fine. What can be the problem?

---

### Post by andrew.46 on 2009-07-14
Hi Krijk,

> **Krijk said:**
> In the logfile I see that the job has started (echo 1) and finished (echo 2) but the python script hasn't run. 

Perhaps try giving this:

```
/data/maintenance/job_to_run.py
```

and *absolute* path rather than a *relative* path? 

Andrew

---

### Post by Krijk on 2009-07-18
Apparently it has something to do with logging/output. Not really sure why.

After trying a lot of stuff I inserted the following lines in my python-script (to learn more apart from my normal logging) and it started working :confused:

[PHP]import sys

sys.stdout = open("out.txt","w")
sys.stderr = open("err.txt","w")
[/PHP]

---

