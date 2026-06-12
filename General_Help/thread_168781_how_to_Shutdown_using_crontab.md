---
title: "how to Shutdown using crontab?"
date: 2006-05-01
forum: General Help
---

### Post by Anilkumar on 2006-05-01
Hello everybody,

Thanks for the support here.I am very hapy to use Ubuntu.

I want to schedule some of my programs.In this view i want to shutdown my computer by 8 am everyday morning.What is the that should be inserted in crontab file?

Plz guide me

---

### Post by stojan on 2006-05-01
in console you should type:
sudo shutdown [-akrhHPfnc] [-t secs] time [warning message]
                  -a:      use /etc/shutdown.allow
                  -k:      don't really shutdown, only warn.
                  -r:      reboot after shutdown.
                  -h:      halt after shutdown.
                  -P:      halt action is to turn off power.
                  -H:      halt action is to just halt.
                  -f:      do a 'fast' reboot (skip fsck).
                  -F:      Force fsck on reboot.
                  -n:      do not go through "init" but go down real fast.
                  -c:      cancel a running shutdown.
                  -t secs: delay between warning and kill signal.
                  ** the "time" argument is mandatory! (try "now") **

---

### Post by GTvulse on 2006-05-01
Open a terminal and enter a full root session:
```
sudo su -
```
Then type:
```
crontab -e
```
and add a line like the following:
```
0 8 * * *    /sbin/shutdown -h now
```
Read the manual pages for crontab and for shutdown:
```

man crontab
man 5 crontab
man shutdown

```
to learn what all the above means at all.

---

### Post by ferretti75 on 2007-06-26
Hi,

I have a similar problem . I need the machine to stay off during given time frame. 
I did a script that checks the time and, eventually, shuts the machine off. My problem is that, if the script is run via crontab, the shutdown ( init 0 ) is not executed . 


this is the script ( maybe you see something I don't ) : 
```


#!/bin/bash
time=$(date +%k%M)
morninglow=700
morningup=1430
eveninglow=1630
eveningup=30

if [[ $time < $morninglow ]] && [[ $time > $eveningup ]] # before 7 a.m. but after 0.30 a.m.
then
        echo "$time : poweroff in the morning"
        init 0
else
        if [[ $time > $morningup ]] && [[ $time < $eveninglow ]] # after 14.30 and before 16.30
        then 
                echo "$time : poweroff in the evening"
                init 0
        fi
fi

```

this is root's crontab : 
```

# m h  dom mon dow   command
*/15 *  * * *   /usr/sbin/checktime.sh 2>&1 >> /var/log/checktime.log

```

Any help would be appreciated .

TIA 
Marco

---

