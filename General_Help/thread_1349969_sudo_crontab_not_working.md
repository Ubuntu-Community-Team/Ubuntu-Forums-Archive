---
title: "sudo crontab not working"
date: 2009-12-08
forum: General Help
---

### Post by waspinator on 2009-12-08
Hi,

I have a script named .test.sh:
```

#!/bin/bash
date >> test.log

```

It's permissions are as follows:
```
-rwxrwxrwx 1 user user 29 Dec  8 20:18 .test.sh
```

sudo crontab -e is this:
```

# m h  dom mon dow   command
50 20 * * * /home/user/.test.sh

```


This is what appears in the /var/log/syslog when it runs
```
Dec  8 20:50:01 server cron[856]: (root) RELOAD (crontabs/root)
```

The problem is, that it doesn't do anything.
The same script in just crontab -e works. 

I have no cron.deny or cron.allow files in /etc

why does sudo crontab -e not work?

Thanks

---

### Post by slakkie on 2009-12-08
I don't follow, crontab -e is editting the crontab, not running it.

In case you don't see date in the log file, set your PATH inside your script.

---

### Post by jobix on 2009-12-08
Tacking on to this, the OP could also set the explicit path in the script, i.e.:

> date >> /home/whatever-dirname/test.log

---

### Post by waspinator on 2009-12-11
> **slakkie said:**
> I don't follow, crontab -e is editting the crontab, not running it.

In case you don't see date in the log file, set your PATH inside your script.

Yes I know crontab -e edits. What I don't understand is why crontab -e WORKS and sudo crontab -e doesn't. Yes I know sudo crontab -e edits roots crontab and crontab -e edits mine. But the actual script I want to run requires root permissions, so I need sudo crontab -e to work.

what PATH do you mean?

Thanks

EDIT: SOLVED

crontab -e worked becuase the path in the script was relative for the user, but didn't work for root.

What was most confusing is that ```
sudo ./.test.sh
``` worked but setting ```
sudo crontab -e
``` to run .test.sh did not. I guess it is because the first one just gives my user elevated permissions, while the second one actually runs as user 'root'. Also it seems that I have to give the exact locations for every program when using sudo crontab -e; so if I want to use the shutdown command I cannot just have ```
shutdown -h now
``` in my script, I have to put ```
/sbin/shutdown -h now
```. 

Thanks again,

Waspinator

---

### Post by jobix on 2009-12-12
The reason you have to give it the "exact location" or the full pathname has to do with the environment variable settings. This page has a good explanation of your problem:

[http://blog.spikesource.com/crontab.htm](http://blog.spikesource.com/crontab.htm)

---

