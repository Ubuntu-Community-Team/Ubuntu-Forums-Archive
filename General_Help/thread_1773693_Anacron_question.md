---
title: "Anacron question"
date: 2011-06-02
forum: General Help
---

### Post by krumpy on 2011-06-02
I want a backup script to run daily, however my computer isn't always on therefore anacron seemed to be better than cron.  However, does anacron only run at reboot?  I usually just put my computer to sleep at night rather than rebooting.  So do you need create cron job for anacron in this situation?

---

### Post by Dave_L on 2011-06-02
I do the same as you, suspend my computer rather than shutting it down.  Anacron does run the /etc/cron.daily, /etc/cron.weekly and /etc/cron.monthly scripts a while after the computer comes out of suspend.

---

### Post by krumpy on 2011-06-02
Where are the settings for programs run upon resuming as my anacron jobs don't seem to run on resume?  I see that anacron is run at startup in /etc/init.d/ and that it's run at 7:30 (on my machine) everyday.

cat /etc/cron.d/anacron
# /etc/cron.d/anacron: crontab entries for the anacron package

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

#30 7    * * *   root    test -x /etc/init.d/anacron && /usr/sbin/invoke-rc.d anacron start >/dev/null
30 7    * * *   root    start -q anacron || :

I just noticed that the first bit is commented out though, but that's just checking to see if anacron is installed right?

---

### Post by Dave_L on 2011-06-02
Your /etc/cron.d/anacron looks the same as mine:

```
# /etc/cron.d/anacron: crontab entries for the anacron package

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

#30 7    * * *   root	test -x /etc/init.d/anacron && /usr/sbin/invoke-rc.d anacron start >/dev/null
30 7    * * *   root	start -q anacron || :
```

This is my /etc/anacrontab. I don't think I've changed it:

```
# /etc/anacrontab: configuration file for anacron

# See anacron(8) and anacrontab(5) for details.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# These replace cron's entries
1	5	cron.daily	 nice run-parts --report /etc/cron.daily
7	10	cron.weekly	 nice run-parts --report /etc/cron.weekly
@monthly	15	cron.monthly nice run-parts --report /etc/cron.monthly
```

Are your jobs are in /etc/cron.daily/?

What are the contents of /var/spool/anacron/cron.daily?

---

### Post by krumpy on 2011-06-02
My etc/anacrontab:

```

# /etc/anacrontab: configuration file for anacron

# See anacron(8) and anacrontab(5) for details.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# These replace cron's entries
1    5    cron.daily     nice run-parts --report /etc/cron.daily
7    10    cron.weekly     nice run-parts --report /etc/cron.weekly
@monthly    15    cron.monthly nice run-parts --report /etc/cron.monthly

```Yeah the job is in cron.daily.   /var/spool/anacron/cron.daily just contains a file with a timestamp of the last time anacron ran.  It's not program by program just a single time stamp.  It's weird b/c the job runs fine when I put it in my crontab, but since my computer isn't always on I thought anacron would be better.  Not sure what's going on.

---

### Post by Dave_L on 2011-06-02
If the job runs from your crontab but not from cron.daily, it's probably an issue with paths or other environment variables.

You could try adding a very simple job /etc/cron.daily/test1:

```
#!/bin/bash
/bin/date >>/home/USER/test1.log 2>&1
```

Make sure that /etc/cron.daily/test1 has permissions 755.

If that job runs daily and logs the date into test1.log, then the problem is with your script, not with anacron or cron.

---

### Post by krumpy on 2011-06-02
I had added something similar to my backup script to see if it runs tomorrow.  I don't think it's the pathing though since the paths look identical to me. 

crontab:

```

PATH=/usr/sbin:/usr/bin:/sbin:/bin:/usr/local/sbin:/usr/local/bin
0 * * * * backup.sh 

```

anacron:
```

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

```

---

### Post by krumpy on 2011-06-04
I think this might be it ([http://translated.by/you/man-run-parts-8-run-scripts-or-programs-in-a-directory/original/](http://translated.by/you/man-run-parts-8-run-scripts-or-programs-in-a-directory/original/)).  run-parts which anacron calls: 

"DESCRIPTION
run-parts runs all the executable files named within constraints described below, found in directory directory. Other files and directories are silently ignored.

If neither the --lsbsysinit option nor the --regex option is given then the names must consist entirely of upper and lower case letters, digits, underscores, and hyphens.

My backup program was called backup.sh so I think it wasn't being detected?  Could someone else confirm that I'm reading that correctly.  run-parts by default doesn't accept *.sh.

---

### Post by krumpy on 2011-06-08
That was definitely what was going on ([http://www.oreillynet.com/linux/blog/2007/08/runparts_scripts_a_note_about.html](http://www.oreillynet.com/linux/blog/2007/08/runparts_scripts_a_note_about.html)).

I couldn't get the --lsbsysinit option to work, but the script worked fine once a created a symlink without the .sh extension. (eg ln -s /usr/local/sbin/backup.sh /etc/cron.daily/backup).  

So for anyone having trouble with scripts not running under anacron remember that default behavior for run-parts (the script anacron calls) is to ignore .sh or .anything files.

---

