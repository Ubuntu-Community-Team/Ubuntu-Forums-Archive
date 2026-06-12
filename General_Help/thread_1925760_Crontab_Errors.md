---
title: "Crontab Errors"
date: 2012-02-15
forum: General Help
---

### Post by Rodney9 on 2012-02-15
I get this error in syslog when I try to run cron -

> Feb 15 18:24:01 9 CRON[2689]: (rodney) CMD (/bin/alarm.sh)
Feb 15 18:24:01 9 CRON[2688]: (CRON) error (grandchild #2689 failed with exit status 1)
Feb 15 18:24:01 9 CRON[2688]: (CRON) info (No MTA installed, discarding output)

The script I am trying to run is called alarm.sh
The script is

```
#!/bin/sh

xterm -e ogg123 -z ~/Music/*.ogg
```

The crontab is 

```
24 18 15 02 * /bin/alarm.sh
```


The script runs from the terminal or 'RUN'

Any clues ?
Rodney

---

### Post by Grenage on 2012-02-15
Try changing your script so that it has absolute paths, then try cron again?

```
xterm -e ogg123 -z ~/Music/*.ogg
```
```
xterm -e ogg123 -z /home/bob/Music/*.ogg
```

---

### Post by Rodney9 on 2012-02-15
> **Grenage said:**
> Try changing your script so that it has absolute paths, then try cron again?

```
xterm -e ogg123 -z ~/Music/*.ogg
```
```
xterm -e ogg123 -z /home/bob/Music/*.ogg
```

Changed script to

```
#!/bin/sh

xterm -e ogg123 -z  /home/rodney/Music/*.ogg
```

Still works in terminal

Still get error

F```
eb 15 19:39:01 9 CRON[3222]: (rodney) CMD (/bin/alarm.sh)
Feb 15 19:39:01 9 CRON[3221]: (CRON) error (grandchild #3222 failed with exit status 1)
Feb 15 19:39:01 9 CRON[3221]: (CRON) info (No MTA installed, discarding output)
```

Rodney

---

### Post by Grenage on 2012-02-15
```
which xterm
```

Will give you xterm's path.  Try using that, rather than just the name in your script.

---

### Post by Cheesehead on 2012-02-15
The 'xterm' command opens a window on your display.

But cron does not have access to your user-level environment variables. It has no idea what display you are using. So it cannot open the window...error.

You must tell cron which display to open.

For example, to determine the current display:
```
$ printenv | grep DISPLAY
DISPLAY=:0.0
```

So alarm.sh would be:
```
DISPLAY=:0.0 /usr/bin/xterm -e ogg123 -z /home/bob/Music/*.ogg
```

---

### Post by Rodney9 on 2012-02-15
> **Cheesehead said:**
> The 'xterm' command opens a window on your display.

But cron does not have access to your user-level environment variables. It has no idea what display you are using. So it cannot open the window...error.

You must tell cron which display to open.

For example, to determine the current display:
```
$ printenv | grep DISPLAY
DISPLAY=:0.0
```

So alarm.sh would be:
```
DISPLAY=:0.0 /usr/bin/xterm -e ogg123 -z /home/bob/Music/*.ogg
```

```
printenv | grep DISPLAY
PRIMARY_DEVICE_FOR_DISPLAY=1
DISPLAY=:
```0

Thankyou that did trick with 

```
DISPLAY=:0.0 /usr/bin/xterm -e ogg123 -z /home/rodney/Music/*.ogg
```


Rodney

---

### Post by ephestione on 2012-07-28
Late to the party, but on a slightly unrelated note, assigning a DISPLAY is necessary also for other tasks, in my case audio-recorder, which fired regularly from crontab but didn't really start recording audio chunks until I specified the destination display as Chesehead suggested.
So thank you Cheesehead ;)

---

### Post by Rahul Chetwani on 2013-01-10
Hi I am getting cron logs but only for CMD and INFO not for errors.
What should i do to get the error logs of cronjobs.
I purposely created a cronjob in crontab which will run a shell script which does not exist..it should log error in cron logs but it is not doing so..

---

