---
title: "cron troubles"
date: 2009-11-01
forum: General Help
---

### Post by irishbreakfast on 2009-11-01
I can't get transmission to start via cron.

I forgot to save my crontable when doing a clean install of 9.10, so can't check what I had before. However, the script it is running wasn't changed, until I started testing. I've been reading and testing all morning and I've had enough. If it matters, I was using transmission 1.5somthing and now it is 1.75.

Excerpt of script: The original is currently commented out. I tried using the two lines method based on postings.
[INDENT]	export DISPLAY=:0
	transmission >> $log 2>&1 &
#	transmission --display=:0 >> $log 2>&1 &
[/INDENT]

The error messages I get are:
[INDENT]No protocol specified
Cannot open display: [/INDENT]

And the crontab, with times changed for testing
[INDENT]10 * * * * /home/me/scripts/trans.sh start > /home/me/scripts/cron1.err 2>&1
15 * * * * /home/me/scripts/trans.sh stop  > /home/me/scripts/cron2.err 2>&1
[/INDENT]

/var/log/syslog shows that the the scripts are being executed at the given times.

Cheers

---

