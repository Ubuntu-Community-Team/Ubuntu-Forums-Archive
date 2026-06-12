---
title: "cron and notify"
date: 2012-08-20
forum: General Help
---

### Post by pco052 on 2012-08-20
Hi there,

I'm trying to create a cron job that displays a text bubble every minute. I've found notify-osd to work quite well.

I created a Script called test.sh 

```
#!/bin/bash
/usr/bin/notify-send "Example Message" -t 2000
```

It works when I run it manually.

However, I can't get cron to run it for me every minute. My Cron configuration is:

```
* * * * * DISPLAY=0.0 /home/pco052/Scripts/test.sh >> /home/pco052/check.log 2>&1
```

---

### Post by pqwoerituytrueiwoq on 2012-08-20
```
* * * * * /home/pco052/Scripts/test.sh >> /home/pco052/check.log
```
```
#!/bin/sh
DISPLAY=":0.0"
export DISPLAY
notify-send "Example Message" -t 2000
```

---

### Post by pco052 on 2012-08-20
awesome it works!!

I noticed you put the display in the script instead of inside cron, is there a reason for that?

Also what does display exactly do? Thanks for making it work!

---

