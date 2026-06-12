---
title: "Cron Beginner"
date: 2006-05-12
forum: General Help
---

### Post by jonnymccullagh on 2006-05-12
I need to run the folowing command daily:
lftp -f /home/jonny/documents/backups/lftpbackup.txt

I usually run it in a shell/console. I would like to know how to run this using Cron. Can anyone help? I've tried KCron but running the command above didn't work (I don't think) and there is no feedback about when the operation was last run etc.
Any help is appreciated,
thanks,
jonny

---

### Post by tribaal on 2006-05-12
Well actually you'll want to use *crontab*, not cron.

*Cron* is the daemon itself, but you don't get to interact with it directly, it just runs in the background.
*Crontab* on the other hand is what lets you modify cron jobs (basically it edits a file and then notifies the daemon).
[U]
Let's be practical:[/U]

log as the user you want the command to be run as.
At the prompt type ```
crontab -e
``` (no sudo!). -e stands for "edit".
This will fire up nano, opening a file with only the syntax line.

For your particular example you'll want to add the folling line to the crontab file:

```
0 0 * * * lftp -f /home/jonny/documents/backups/lftpbackup.txt > /dev/null
```

This will make the script run at midnight every day, and will not output anything except if an error occurs. Errors are sent to you by internal email (accessed by the "mail" command).

For further help on syntax, type "man crontab" at the prompt, or use  [this]("http://en.wikipedia.org/wiki/Crontab") =)

Hope this helps... cron is really nice and convenient to use once you get used to it :)

One of my favorites, along with ssh. Enjoy!

- trib'

---

### Post by cyracks on 2006-05-12
Or you can create executable bash script and put it in **/etc/cron.daily/**. This way it will be executed every day at 6 o'clock in the morning.

```

#!/bin/sh

lftp -f /home/jonny/documents/backups/lftpbackup.txt > /dev/null


```

btw: the script will be run by program called **run-parts** which doesn't allow dot (.) in the name of the script.

---

### Post by tribaal on 2006-05-12
Hum I didn't even know about /etc/cron.daily/ :)

Thank you :)

- trib'

---

### Post by jonnymccullagh on 2006-05-12
Great info - thanks!
I'll know by Monday when I am back at work if it worked,
thanks,
jonny

---

### Post by Rog131 on 2006-05-12
Or you can use kcron or kdesu kcron (graphical ~ simple to use = point and click).

kdesu kron -> crontab daily/monthly/weekly/hourly

---

