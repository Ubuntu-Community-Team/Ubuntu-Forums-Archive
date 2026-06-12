---
title: "cron job test not executing"
date: 2012-10-04
forum: General Help
---

### Post by micahpage on 2012-10-04
I am reading through tutorials of how to use crontab, but I think i must of mess something up

```
crontab -e
```

and i appended to the file:
```
*/1 * * * * echo cron job ran success\n

```

I believe that is every minute?
I was expecting a terminal to pop up every minute, except it does not?

---

### Post by micahpage on 2012-10-04
OK so i think it is working somewhat

my crontable file i changed to:
```
*/1 * * * * python3 /home/metulburr/Documents2/ipchecker.py

```

in which my python program is sending me an email every minute, but there is also a desktop notification in the python script that iis not executing with cron, but does when when i execute the python script directly

the desktop notification cmd format is:
```
$ notify-send "my string"

```


So now i am confused as to why this happens?

---

### Post by Cheesehead on 2012-10-04
> **micahpage said:**
> */1 * * * * echo cron job ran success\n


Echo to where? Cron is not logged into your tty, and has no idea which display you are using (if any).

Use the command 'printenv | grep DISPLAY' to find your current display, and preface the cron job with that:
```
* * * * * export DISPLAY=0.0 echo blah blah...
```

Better yet, don't use a display at all. File operations are easy.
```
* * * * * touch /tmp/testfile
```

---

