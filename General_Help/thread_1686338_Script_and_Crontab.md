---
title: "Script and Crontab"
date: 2011-02-12
forum: General Help
---

### Post by dreamkhan on 2011-02-12
***[SIZE=2]Begin, i have no knowledge of linux. [/SIZE]***
***[SIZE=2]I'm experimenting with Ubuntu. [/SIZE]***
 
***[SIZE=2]Have made a script called: tabdate.sh. [/SIZE]***
 
***[SIZE=2]Script looks like this: [/SIZE]***
***[SIZE=2]#!/bin/bash [/SIZE]***
***[SIZE=2]iptables-R INPUT 1-p tcp - dport ssh-j ACCEPT [/SIZE]***
 
***[SIZE=2]If i do [COLOR=red]./tabdate.sh[/COLOR], the script works. [/SIZE]***
 
***[SIZE=2]I want, the script runs every 5 minutes using the crontab.[/SIZE]***
 
***[SIZE=2]Please some information, how to do that???[/SIZE]***
 
***[SIZE=2]By the way, in which map you need to place tabdate.sh.[/SIZE]***
 
***[SIZE=2]Sorry for my bad english. Thanks for your reply.[/SIZE]***
 
 
[RIGHT][COLOR=#333]powered by[/COLOR]
[COLOR=#333][IMG]http://www.vertalen.nu/images/google-logo.png[/IMG][/COLOR][/RIGHT]

---

### Post by carl.davis on 2011-02-12
You would need to insert the following line into cron using the "crontab -e" command

```
*/5 * * * * /path/to/tabdate.sh
```

---

### Post by dreamkhan on 2011-02-12
> **carl.davis said:**
> You would need to insert the following line into cron using the "crontab -e" command
 
```
*/5 * * * * /path/to/tabdate.sh
```
 
I have try it, no success.
 
In the /var/log/cron.log, this faulty:
 
Feb 12 13:55:01 ubuntu CRON[7467]: (CRON) error (grandchild #7468 failed with exit status 127)
Feb 12 13:55:01 ubuntu CRON[7467]: (CRON) info (No MTA installed, discarding output)

---

### Post by DaithiF on 2011-02-12
a couple of suggestions:
1. you would need to be root to add an iptables entry, so you should put this in root's crontab rather than your own, ie.
```
sudo crontab -e
```

2. capture the output from the job into a log file so that you can see what errors / other output get generated:
```
*/5 * * * * /path/to/tabdate.sh &> /path/to/tabdate.log
```

---

### Post by dreamkhan on 2011-02-12
> **DaithiF said:**
> a couple of suggestions:
1. you would need to be root to add an iptables entry, so you should put this in root's crontab rather than your own, ie.
```
sudo crontab -e
```
 
2. capture the output from the job into a log file so that you can see what errors / other output get generated:
```
*/5 * * * * /path/to/tabdate.sh &> /path/to/tabdate.log
```
 
Same problem and no tabdate.log!!!!
 
Feb 12 15:05:01 ubuntu CRON[7784]: (root) CMD (/path/to/tabdate.sh &> /path/to/tabdate.log)
Feb 12 15:05:01 ubuntu CRON[7783]: (CRON) error (grandchild #7784 failed with exit status 2)
Feb 12 15:05:01 ubuntu CRON[7783]: (CRON) info (No MTA installed, discarding output)

---

### Post by gmargo on 2011-02-12
> **dreamkhan said:**
> Same problem and no tabdate.log!!!!
 
Feb 12 15:05:01 ubuntu CRON[7784]: (root) CMD (/path/to/tabdate.sh &> /path/to/tabdate.log)
Feb 12 15:05:01 ubuntu CRON[7783]: (CRON) error (grandchild #7784 failed with exit status 2)
Feb 12 15:05:01 ubuntu CRON[7783]: (CRON) info ([SIZE=4]**[COLOR=Red]No MTA installed, discarding output[/COLOR]**[/SIZE])

Install an MTA such as postfix or exim4.  Then you'll get that output as email.  That output is the message telling you what is wrong; don't ignore it.

Update: Using "&>" for redirection won't work; it's a bash extension.  You should use:
```

*/5 * * * * /path/to/tabdate.sh > /path/to/tabdate.log 2>&1

```

---

### Post by CharlesA on 2011-02-12
Use the full path when making scripts that will be run via cron.

---

