---
title: "Problems with backgrounding scripts in cron"
date: 2012-01-24
forum: General Help
---

### Post by tankinnen on 2012-01-24
Hi

I have a script which I call from cron which causes another script to be run in the background:

#!/bin/bash
bash /usr/local/bin/generateOutput &

The script generateOutput simply echos a text string.

When called from the command line I see the output whether or not generateOutput is backgrounded.  When called from cron, and generateOutput is backgrounded I do not get the resulting output emailed to me as I would expect.

Has anyone seen this before and can you suggest how to capture STDERR and STDOUT from generateOutput and return it to the cron?

Many thanks

---

### Post by Wayne_V on 2012-01-24
See here first:  
[https://help.ubuntu.com/community/CronHowto#Troubleshooting_and_Common_Problems](https://help.ubuntu.com/community/CronHowto#Troubleshooting_and_Common_Problems)

are you running the cronjob as a regular user?

what is your cron entry?

have you tried to tee stdout & stderr to a file as well?

have you checked /var/log/ auth.log and syslog?

---

### Post by dcstar on 2012-01-25
> **Wayne_V said:**
> 
........
have you tried to tee stdout & stderr to a file as well?

have you checked /var/log/ auth.log and syslog?

Or have you asked your tutor?

---

