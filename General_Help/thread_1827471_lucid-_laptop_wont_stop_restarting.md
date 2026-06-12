---
title: "lucid- laptop wont stop restarting"
date: 2011-08-18
forum: General Help
---

### Post by KEE on 2011-08-18
after like 5-10 mins of it being logged in it shuts off power by itself. whats doing this? please help

---

### Post by fdrake on 2011-08-18
> **KEE said:**
> after like 5-10 mins of it being logged in it shuts off power by itself. whats doing this? please help

what's your 

```
less /etc/crontab
```

also are you sure you did not run

```
init 6
```

---

### Post by KEE on 2011-08-19
> **fdrake said:**
> what's your 

```
less /etc/crontab
```

also are you sure you did not run

```
init 6
```
```
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user  command
17 *    * * *   root    cd / && run-parts --report /etc/cron.hourly
25 6    * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6    * * 7   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6    1 * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )

```

---

### Post by fdrake on 2011-08-19
> **KEE said:**
> ```
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user  command
17 *    * * *   root    cd / && run-parts --report /etc/cron.hourly
25 6    * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6    * * 7   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6    1 * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )

```

nothing unusual from  the crontab. did you check the start-up applicaion manager and the power-management?

---

### Post by dino99 on 2011-08-19
it can be:

- hardware temp issue:
 do you have fans working ? have you overclocked ? can it catch some fresh air ?  maybe too dusty ;)

- software issue: something is borked, watch logs to know about (/var/log/ & xsession-errors); are you using non genuine repo/package ?

you can also clean the system:
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

---

### Post by KEE on 2011-08-19
this is real bad, my system super heats with ubuntu, but on windows it stays at 50ish. core temp goes up to 95 on ubuntu

---

