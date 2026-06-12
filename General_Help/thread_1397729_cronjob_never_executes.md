---
title: "cronjob never executes"
date: 2010-02-03
forum: General Help
---

### Post by neridaj on 2010-02-03
Hello,

I'm trying to setup a cronjob and for some reason my script never executes. I've tried a really simple terminal output that runs from the command line successfully, but does not run from crontab. I've made sure to add newlines and chmod to +x but nothing is working. I also didn't see any error output related to the crontab in the syslog - just normal EDIT crontab output. Here are two scripts I'm trying to run:

#cron/test 
#!/bin/bash

```
echo "this is a friendly message"
```

#cron/syncr
#!/usr/bin/python
```
from syncr.app.tweet import TwitterSyncr
t = TwitterSyncr('username', 'passwd')
t.syncTwitterUserTweets('username')
t.syncFriends('username')
```

#crontab -e
```
1 * * * * python /home/username/cron/syncr.py

1 * * * * sh /home/username/cron/test
```

---

### Post by mgichoga on 2010-02-03
Do they (scripts) run if you ivnoke them manually?

---

### Post by neridaj on 2010-02-03
yeah, they run from the command line.

---

### Post by gmargo on 2010-02-03
Did you wait long enough?

You specified "run at 1-minute past the hour".

Try something like this in your crontab; it will run once per minute:

```
* * * * * env
```

---

### Post by neridaj on 2010-02-03
I tried adding that to my crontab and still nothing happens.

---

### Post by lloyd_b on 2010-02-03
You can NOT use "echo" in a cron job and expect it to show up on the console.  What you *can* do is have it send something to a file that you can inspect:```
#!/bin/bash

echo "Starting script" > /home/myuser/croninfo.txt
```will create/overwrite a file ('/home/myuser/croninfo.txt') with the line "Starting script".  If you want to get more useful info, you can trap the date/time it started, and have it append onto the file rather than overwrite:```
#!/bin/bash

DATE=`date`

echo "Starting cron job at "$DATE >> /home/myuser/croninfo.txt
```

You can also use redirection in the crontab entry, to capture any output from the command:```
* * * * * python /home/username/cron/syncr.py >> /home/user/croninfo.txt

* * * * * sh /home/username/cron/test >> /home/myuser/croninfo.txt
``` will cause those command to run, and capture any output from them and append it onto '/home/myuser/croninfo.txt'.

I have no clue what's wrong with your Python script, but hopefully if you capture the output, it'll show you an error message that provides a clue as to the actual problem (a PATH problem, maybe).

Lloyd B.

---

### Post by mgichoga on 2010-02-03
Suggestions:
1. Is the cron daemon running?

> sudo ps auwx | grep cron

if not start it

> sudo /etc/init.d/cron start

2. Try putting the paths for python. 

> * * * * * /usr/bin/python /home/username/cron/syncr.py

Consult your syslog see if there any errors.

---

### Post by bodhi.zazen on 2010-02-03
> **mgichoga said:**
> Try putting the paths for python. 

The most common problem with cron is with paths. Cron runs with minimal permissions on a minimal shell so often commands are not on cron's $PATH

---

### Post by neridaj on 2010-02-08
it looks like it's running, from the output of syslog, but croninfo.txt contains nothing.

Feb  8 23:43:01 slicename /USR/SBIN/CRON[1458]: (root) CMD (env)
Feb  8 23:43:01 slicename /USR/SBIN/CRON[1461]: (root) CMD (/usr/bin/python /home/username/cron/syncr.py >> /home/username/croninfo.txt)
Feb  8 23:44:01 slicename /USR/SBIN/CRON[1469]: (root) CMD (env)
Feb  8 23:44:01 slicename /USR/SBIN/CRON[1473]: (root) CMD (/usr/bin/python /home/username/cron/syncr.py >> /home/username/croninfo.txt)
Feb  8 23:45:01 slicename /USR/SBIN/CRON[1481]: (root) CMD (env)
Feb  8 23:45:01 slicename /USR/SBIN/CRON[1484]: (root) CMD (/usr/bin/python /home/username/cron/syncr.py >> /home/username/croninfo.txt)
Feb  8 23:46:01 slicename /USR/SBIN/CRON[1494]: (root) CMD (env)
Feb  8 23:46:01 slicename /USR/SBIN/CRON[1497]: (root) CMD (/usr/bin/python /home/username/cron/syncr.py >> /home/username/croninfo.txt)


* * * * * /usr/bin/python /home/username/cron/syncr.py >> /home/user/croninfo.tx

---

### Post by neridaj on 2010-02-08
appending echo statements works:

* * * * * echo "Nightly Backup Successful: $(date)" >> /home/username/croninfo.txt

Nightly Backup Successful: Tue Feb  9 00:13:01 UTC 2010
Nightly Backup Successful: Tue Feb  9 00:14:01 UTC 2010
Nightly Backup Successful: Tue Feb  9 00:14:01 UTC 2010
Nightly Backup Successful: Tue Feb  9 00:15:01 UTC 2010
Nightly Backup Successful: Tue Feb  9 00:15:01 UTC 2010

---

### Post by dcstar on 2010-02-09
> **neridaj said:**
> Hello,

I'm trying to setup a cronjob and for some reason my script never executes. I've tried a really simple terminal output that runs from the command line successfully, but does not run from crontab. I've made sure to add newlines and chmod to +x but nothing is working. I also didn't see any error output related to the crontab in the syslog - just normal EDIT crontab output. Here are two scripts I'm trying to run:

#cron/test 
#!/bin/bash

```
echo "this is a friendly message"
```

#**cron/syncr**
#!/usr/bin/python
```
from syncr.app.tweet import TwitterSyncr
t = TwitterSyncr('username', 'passwd')
t.syncTwitterUserTweets('username')
t.syncFriends('username')
```

#crontab -e
```
1 * * * * python /home/username/cron/**syncr.py**

1 * * * * sh /home/username/cron/test
```

Make up your mind, which one is the correct filename?

---

### Post by dcstar on 2010-02-09
[QUOTE=neridaj]
..........
#cron/syncr
#!/usr/bin/python
```
from **syncr.app.tweet** import TwitterSyncr
t = TwitterSyncr('username', 'passwd')
t.syncTwitterUserTweets('username')
t.syncFriends('username')
```
[/QUOTE]

If that is a file, where is its path?

---

