---
title: "crontab doesn't seem to be working"
date: 2011-05-22
forum: General Help
---

### Post by LordAro on 2011-05-22
hi,

i have recently tried to start using crontab, but it has come to my attention that it doesn't seem to be running.

the things i have entered in my crontab file (my user and root) don't run

is there anything i can do to see what's going on?

---

### Post by tapi0n on 2011-05-22
could you post your cronjobs? And if your cronjobs are scripts post one of the scripts too

---

### Post by LordAro on 2011-05-22
sorry, i was going to do that, but i forgot :)

here: (my user, not root, but they are the same)

```
lordaro@Toby::Ubuntu:~$ sudo crontab -l
[sudo] password for lordaro: 
@reboot /home/lordaro/coding/ottd/pull.sh
@hourly /home/lordaro/coding/ottd/pull.sh

@reboot /home/lordaro/openttd_update.sh
0 21 * * * /home/lordaro/openttd_update.sh

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
# For more information see the manual pages of crontab(5) and cron(8)
# 
# m h  dom mon dow   command

```

and here is pull.sh:
```
#!/bin/bash

echo "starting"
cd cleantrunk
echo "pulling"
hg pull -u http://hg.openttd.org/openttd/trunk.hg
echo "done"
exit;
```

---

### Post by tapi0n on 2011-05-22
You need to add sh in front of your cronjob since you seem to be running sh scripts.
```

0 21 * * * /home/lordaro/openttd_update.sh
```

should be

```

0 21 * * * sh /home/lordaro/openttd_update.sh
```

---

### Post by LordAro on 2011-05-22
thats... quite obvious... :)

i set it to go every minute, so i'll soon see if it works :)

---

### Post by tapi0n on 2011-05-22
Ye it's very obvious, but to be honost first time I was working with crontab I forgot about that too :) 

btw, if your scripts still don't work try adding full paths to your scripts

From example 

```
echo "done"
```

should be 
```
/bin/echo "done"
```

---

### Post by LordAro on 2011-05-22
the scripts work normally (when i run them directly from the terminal)

in other news, it worked! sort of... the openttd_update.sh seems to have worked, but the other hasn't... help?

current crontab:


```
@reboot sh /home/lordaro/coding/ottd/pull.sh
15 * * * * sh /home/lordaro/coding/ottd/pull.sh

@reboot sh /home/lordaro/openttd_update.sh
15 * * * * sh /home/lordaro/openttd_update.sh

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
# For more information see the manual pages of crontab(5) and cron(8)
# 
# m h  dom mon dow   command

```

---

### Post by tapi0n on 2011-05-22
Could you post the openttd script?

Could be a problem with paths, since when running commands from command line the correct path is already interpreted. But when crontab runs a command, crontab doesn't know the required path to the specific command.

---

### Post by LordAro on 2011-05-22
ah, yes, running *sh /home/lordaro/coding/ottd/pull.sh* from the terminal shows that there are path errors, which will fix now :)

thanks for your help!

---

### Post by tapi0n on 2011-05-22
No problem, glad I was of assistence :)

First person I helped solve something. Woop!

---

### Post by ddrake_ on 2011-05-31
> **tapi0n said:**
> You need to add sh in front of your cronjob since you seem to be running sh scripts.


Not true. I have many shell scripts run from cron that don't start with "sh". Almost certainly the problem here is that the OP didn't set execute permissions on the script.

---

### Post by LordAro on 2011-07-11
> **ddrake_ said:**
> Not true. I have many shell scripts run from cron that don't start with "sh". Almost certainly the problem here is that the OP didn't set execute permissions on the script.
I doubt it, as i was previously running to scripts manually, and they were working fine (from the right directory of course :) )

---

