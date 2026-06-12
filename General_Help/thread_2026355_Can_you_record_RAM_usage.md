---
title: "Can you record RAM usage?"
date: 2012-07-15
forum: General Help
---

### Post by robtygart on 2012-07-15
Is there a way to record RAM useage? I keep getting freeze ups and I want to see where the RAM was when it happens. 

Thanks 
Rob

---

### Post by codemaniac on 2012-07-15
The  top program provides a dynamic real-time view of a running system.  It can display system summary information as well as a list of tasks currently being managed by the Linux kernel .

**while running top use shift+M to see top resource eating tasks .**

---

### Post by cryptotheslow on 2012-07-15
If you have another machine on your network you could look into using SNMP to remotely trap memory usage on the problem machine, even use something like mrtg to produce pretty graphs from the trapped data.

For something quick and dirty you could create a script like this in your home directory:
```

#!/bin/bash
date >> /home/your_user_name/mem_monitor.log
free -m >> /home/your_user_name/mem_monitor.log

```

You can create that in a text editor like gEdit or from commandline nano / vi etc., save it as mem_monitor.sh 

Then add it to your crontab with the command:
```
crontab -e
```

Add a line like this:
```
*/10 * * * * /home/your_user_name/mem_monitor.sh
```

That should cause the script to run every 10 minutes and put the date / time and current memory usage in the .log file.

Amend the cron entry if you need it to run more frequently.

I'm sure someone will be along with a better answer soon :D

---

### Post by mc4man on 2012-07-15
You may find the sysstat package useful, after install look at 
man pidstat
The other other things included, check in synaptic or elsewhere for add comm, & man's

---

### Post by robtygart on 2012-07-15
> **cryptotheslow said:**
> If you have another machine on your network you could look into using SNMP to remotely trap memory usage on the problem machine, even use something like mrtg to produce pretty graphs from the trapped data.

For something quick and dirty you could create a script like this in your home directory:
```

#!/bin/bash
date >> /home/your_user_name/mem_monitor.log
free -m >> /home/your_user_name/mem_monitor.log

```

You can create that in a text editor like gEdit or from commandline nano / vi etc., save it as mem_monitor.sh 

Then add it to your crontab with the command:
```
crontab -e
```

Add a line like this:
```
*/10 * * * * /home/your_user_name/mem_monitor.sh
```

That should cause the script to run every 10 minutes and put the date / time and current memory usage in the .log file.

Amend the cron entry if you need it to run more frequently.

I'm sure someone will be along with a better answer soon :D


```
crontab -e
```
At first asked me to pick one of three options, I tried to cancle it, (Until I posted and asked) 

Now it givs me this...

```
  GNU nano 2.2.6        File: /tmp/crontab.aZufod/crontab                       

# Edit this file to introduce tasks to be run by cron.
#
# Each task to run has to be defined through a single line
# indicating with different fields when the task will be run
# and what command to run for the task
#
# To define the time you can provide concrete values for
# minute (m), hour (h), day of month (dom), month (mon),
# and day of week (dow) or use '*' in these fields (for 'any').#
# Notice that tasks will be started based on the cron's system
# daemon's notion of time and timezones.
#
# Output of the crontab jobs (including errors) is sent through
# email to the user the crontab file belongs to (unless redirected).
#
# For example, you can run a backup of all your user accounts
# at 5 a.m every week with:
# 0 5 * * 1 tar -zcf /var/backups/home.tgz /home/
#
                               [ Read 22 lines ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Text^T To Spell

```

---

### Post by codemaniac on 2012-07-15
```
crontab -e
```

opens up the crontab file in you preferable console based editor to be open up in edit mode.In your system it is nano .

You need to add the health check commands as separate cron entries .
They will get fired periodically with certain conditions .

You can add the below comments to your crontab file in order to memorize the cron syntax better .

```
# minute (0-59),
# |      hour (0-23),
# |      |       day of the month (1-31),
# |      |       |       month of the year (1-12),
# |      |       |       |       day of the week (0-6 with 0=Sunday).
# |      |       |       |       |       commands
 

```

Is there any special reasons you want to call the system health check utilities via cron ?

---

### Post by robtygart on 2012-07-15
> **codemaniac said:**
>  Is there any special reasons you want to call the system health check utilities via cron ?

No special reason, It was cryptotheslow suggestion, I want to monitor my memory and see where it was when it freezes.


So should I add the code at the end of that entry that I posted? "GNU nano 2.2.6        File: /tmp/crontab.aZufod/crontab"

---

