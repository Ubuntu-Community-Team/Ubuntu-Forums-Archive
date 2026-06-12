---
title: "Using crontab to restart pidgin?"
date: 2010-05-23
forum: General Help
---

### Post by Wage on 2010-05-23
Pidgin likes to randomly crash on me, and sometimes it takes me awhile to notice. So I thought why not make a script and cron job to see if pidgin is running and restart it if needed. Sounded easy but having all kinds of problems.

Here's my cron line...
```
*/1 * * * * /home/justin/chkpdgn.sh >> /home/justin/test.log 2>&1
```

I run "tail -f /home/justin/test.log" to keep an eye on the cron output.


Here's the chkpdgn.sh script...
```
#!/bin/bash

SERVICE='pidgin'

if ps ax | grep -v grep | grep $SERVICE > /dev/null
then
    echo "$SERVICE service running, everything is fine"
else
    echo "$SERVICE is not running"
    $SERVICE
fi
```


Running that works fine when I do it, but when cron does it pidgin never starts and I get this error...
```
pidgin is not running

(Pidgin:29525): Gdk-CRITICAL **: gdk_display_get_name: assertion `GDK_IS_DISPLAY (display)' failed

** (Pidgin:29525): WARNING **: cannot open display: unset
Pidgin 2.7.0
```

Someone told me to add "export DISPLAY=:0" to the top of my script but that gives me the following errors...

```
pidgin is not running
error: line 15: bad flag alias index: 0
error: line 15: bad flag vector alias
error: line 16: bad flag alias index: 0
error: line 16: bad flag vector alias
```

That goes on for quite awhile up to like line 60000 and pidgin runs but doesn't show up in the me menu.

Anyone have any idea of whats wrong or know a better way to restart pidgin when it crashes?

---

### Post by Bonster on 2010-05-23
This is what i use for transmission, but u can replace it with pidgin or any other apps. Remove the export line if is not a GUI app.

> #!/bin/bash

#Check if Transmission is running; If running then do nothing; If not then start
export DISPLAY=:0
cd /usr/bin/
if pidof -x transmission; then exit; else transmission -m; fi

---

### Post by Wage on 2010-05-23
> **Bonster said:**
> This is what i use for transmission, but u can replace it with pidgin or any other apps. Remove the export line if is not a GUI app.

That does the bad flag alias/bad flag vector alias thing too. I searched some more on those errors and found out they are caused by the en_ZA dictionaries of myspell. I moved them from /usr/share/myspell/dicts/ and now pidgin starts up fine. Anyone know if these files are something I need or if it'll cause any problems deleting them?

---

