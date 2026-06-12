---
title: "run script at login that requires root privileges"
date: 2010-08-03
forum: General Help
---

### Post by Eredeath on 2010-08-03
I have the script below that I want to run when my sister logs into her account. But the problem is that `ifconfig up` or `ifconfig down` requires root privileges. How do I initiate the program when she logs in and have root the the runner of the program. 
```
#!/bin/bash

while true
do
	elevenpm=`date +%s --date "2300"`
	sevenam=`date +%s --date "0700"`
	timenow=`date +%s`
	if [[ ($timenow -gt $sevenam) && ($timenow -lt $elevenpm) ]]; then
		echo "Internet is up"
		`ifconfig eth0 up`
	else
		echo "Internet is going down"
		`ifconfig eth0 down`
	fi 
	sleep 5m

done
```

---

### Post by prodigy_ on 2010-08-03
You don't need a script for this at all. A cron job would do just fine. Read [this HOWTO](https://help.ubuntu.com/community/CronHowto).

---

### Post by Eredeath on 2010-08-03
> **prodigy_ said:**
> You don't need a script for this at all. A cron job would do just fine. Read [this HOWTO](https://help.ubuntu.com/community/CronHowto).

Reading through it I would have to set up a root crontab file, and I would have to let it run no matter who is logged on. I want it to run just when my sister is logged in.

---

### Post by prodigy_ on 2010-08-03
> **Eredeath said:**
> I would have to let it run no matter who is logged on.
You can make it conditional. For example: ```
[ -n "$(who -u|grep 'tty'|grep '<account_name>')" ] && /sbin/ifdown eth0
``` where <account_name> is the account for which you want the connection to go down.

---

### Post by Eredeath on 2010-08-03
But if cron is running it in the root process wouldn't the who be "root"?

---

