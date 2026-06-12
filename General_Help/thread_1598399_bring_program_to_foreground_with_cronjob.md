---
title: "bring program to foreground with cronjob"
date: 2010-10-16
forum: General Help
---

### Post by davidstoll on 2010-10-16
Essentially I want to make sure a particular program is running and if it is, make sure it is brought to the foreground.

Here is my script...

```
#!/bin/bash

if [ "$(ps aux | grep -v grep | grep -c mythfrontend.real)" -eq 1 ]    # is mythfrontend running?
    then
    echo "mythfrontend is running"
    $(wmctrl -ia `wmctrl -l | grep 'MythTV Frontend' | cut -d ' ' -f1`)    # bring mythfrontend to the forground
fi

if [ "$(ps aux | grep -v grep | grep -c mythfrontend.real)" -eq 0 ]    # is mythfrontend running?
    then
    echo "mythfrontend is NOT running, restarting now"
    $(mythfrontend)                # if not, then run it
fi


if [ "$(ps aux | grep -v grep | grep -c mythfrontend.real)" -ge 2 ]
    then
    echo "too many instances of mythfrontend are running, killing and restarting"
    $(killall mythfrontend.real)
    $(mythfrontend)
    #$(kill -9 `ps aux | grep mythfrontend.real | cut -d ' ' -f5 | sed -n 1p`)    # kill the extra process
    #$(wmctrl -ia `wmctrl -l | grep MythTV | cut -d ' ' -f1`)    # bring mythfrontend to the forground
fi
```

It works if run by hand, but when run as a cron job nothing happens.  Can someone help me figure out why?

entry in /etc/crontab
45 13	* * *	user	/home/user/runmythfrontend.sh &

I've also tried with and without the & and also as root.

---

