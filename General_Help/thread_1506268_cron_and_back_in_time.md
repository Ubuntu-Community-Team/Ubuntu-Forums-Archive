---
title: "cron and back in time"
date: 2010-06-10
forum: General Help
---

### Post by windyrij on 2010-06-10
Hello:
10.04 (Lucid)
Linux  Kernel 2.6.32-22-generic
GNOME 2.30.0
2.0 GB memory
AMD Athlon 64 Processor 3200+
18.4 GB disk free.

I have installed Back in Time (BiT), as I cannot get sbackup to run (bug?). I set up BiT as user (not root) to run daily. It ran once, but has not run daily.
cron is running - checked status.
To try and see if cron will run at 1 minute intervals, I added a line to crontab, to get it to run dillo. This does not happen, but possibly I have not directed the output correctly. There is also a newline after each command in crontab.

Code from terminal:
-------------------------------
john@john-desktop:~$ crontab-l
crontab-l: command not found
john@john-desktop:~$ crontab -l
*/1 * * * * /usr/bin/dillo

#0 0 * * * nice -n 19 /usr/bin/backintime --backup-job # JOB_ID_2

john@john-desktop:~$ crontab -e
crontab: installing new crontab
john@john-desktop:~$ crontab -l
*/1 * * * * /usr/bin/dillo

0 0 * * * nice -n 19 /usr/bin/backintime --backup-job # JOB_ID_2

john@john-desktop:~$ status cron
cron start/running, process 759
john@john-desktop:~$ ^C
john@john-desktop:~$ 
-----------------------------------

Code from syslog (end part)
-----------------------------------------
Jun 10 10:35:41 john-desktop crontab[2228]: (john) LIST (john)
Jun 10 10:35:57 john-desktop crontab[2230]: (john) BEGIN EDIT (john)
Jun 10 10:36:01 john-desktop CRON[2243]: (john) CMD (/usr/bin/dillo)
Jun 10 10:36:01 john-desktop CRON[2242]: (john) MAIL (mailed 39 bytes of output but got status 0x0001#012)
Jun 10 10:36:13 john-desktop crontab[2230]: (john) REPLACE (john)
Jun 10 10:36:13 john-desktop crontab[2230]: (john) END EDIT (john)
Jun 10 10:37:01 john-desktop cron[759]: (john) RELOAD (crontabs/john)
Jun 10 10:37:01 john-desktop CRON[2248]: (john) CMD (/usr/bin/dillo)
Jun 10 10:37:02 john-desktop CRON[2247]: (john) MAIL (mailed 39 bytes of output but got status 0x0001#012)
Jun 10 10:37:38 john-desktop crontab[2252]: (john) LIST (john)
Jun 10 10:38:01 john-desktop CRON[2255]: (john) CMD (/usr/bin/dillo)
Jun 10 10:38:01 john-desktop CRON[2254]: (john) MAIL (mailed 39 bytes of output but got status 0x0001#012)
--------------------------------

The command in crontab for BiT was set up by BiT (General|Schedule|Every day).

Anyone got any ideas where I have gone wrong?

Thanks a lot, John

---

### Post by arrange on 2010-06-10
Not sure what you're trying to achieve, but your *cron* seems to be working normally. If you want to test it, do not use a graphical front-end, use f.e.```
* * * * * touch /tmp/test
```and see if the file */tmp/test* gets created/updated every full minute.

If so, test the command *nice -n 19 /usr/bin/backintime --backup-job* first from [Terminal](https://help.ubuntu.com/community/GnomeTerminal). If it works, I'd suggest creating a script in your home directory, name it e.g. *~/backmeup.sh*```
#! /bin/sh
nice -n 19 /usr/bin/backintime --backup-job > /tmp/backmeup.log 2>&1
exit 0

```
give it execution rights, and then put in your crontab```
0 0 * * * /home/your_username/backmeup.sh
```

---

### Post by windyrij on 2010-06-11
Hello arrange:

Thanks for your help. It is a case of RTFM - I had overlooked that CRON assumes that the system never shuts down! My PC is switched of when not in use!

I edited anacrontab to include the line to run Back in Time -

(anacrontab from gedit)
---------------
latest# /etc/anacrontab: configuration file for anacron

# See anacron(8) and anacrontab(5) for details.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# These replace cron's entries
1    5    cron.daily     nice run-parts --report /etc/cron.daily
7    10    cron.weekly     nice run-parts --report /etc/cron.weekly
@monthly    15    cron.monthly nice run-parts --report /etc/cron.monthly

1    15    daily_backup    /usr/bin/backintime
-------------------

I then re-started the system, and watched syslog
Entry from syslog:
Code:
------------
Jun 11 10:45:43 john-desktop anacron[872]: Will run job `daily_backup' in 15 min.
...
Jun 11 11:00:43 john-desktop anacron[872]: Job `daily_backup' started
Jun 11 11:00:43 john-desktop anacron[872]: Job `daily_backup' terminated (mailing output)
Jun 11 11:00:43 john-desktop anacron[872]: Can't find sendmail at /usr/sbin/sendmail, not mailing output
Jun 11 11:00:43 john-desktop anacron[872]: Normal exit (1 job run)
-----------------

There was no output to the device (WD Elements 1TB drive mounted on /media/).

So I installed sendmail using Synaptic, edited acrontab to change the delay from 15 mins to 5 mins and re-started again. Syslog does not show the job running again. Is this because it has run once today, though without writing to the output device?
Is there a way to re-run the job, instead of waiting till the next day?

Thanks again   John

---

### Post by arrange on 2010-06-11
First try to make it work in *crontab* (see my previous post), then it should work in *anacron* as well.

To test it you can use```
* * * * * /home/your_username/backmeup.sh
```to launch the script every minute, or ```
*/x * * * * /home/your_username/backmeup.sh
```to launch the script every *x-th* minute.

---

### Post by windyrij on 2010-06-12
Hello again, arrange, and many thanks for your patience.

As suggested, I tried running the command *nice -n 19 /usr/bin/backintime --backup-job* first  from Terminal. This worked OK.

I then created */backmeup.sh *in my Home directory, gave it Execution rights and put it in crontab, as specified.to launch the script every minute.
---------------------
*/x * * * * /home/your_username/backmeup.sh
--------------------
 This worked OK.

I then added a line to anacrontab as follows:
Code:
----------------------
latest# /etc/anacrontab: configuration file for anacron

# See anacron(8) and anacrontab(5) for details.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# These replace cron's entries
1    5    cron.daily     nice run-parts --report /etc/cron.daily
7    10    cron.weekly     nice run-parts --report /etc/cron.weekly
@monthly    15    cron.monthly nice run-parts --report /etc/cron.monthly

1    5       daily backup    /home/john/backmeup.sh
------------------------

This did not work, including today. Have I got the entry in anacrontab wrong?

Thanks again for your help,           John

---

### Post by mike2357 on 2010-06-12
Cron and anacron don't work exactly the same.  Although you can make entries in /etc/anacrontab, the format isn't the same as cron, and there's a way that I find is easier.  So first, I suggest that you remove any entries you added to /etc/anacrontab so it looks like it did before you made any changes.

Anacrontab allows you to add scripts to one of three directories that live in /etc:
cron.daily
cron.weekly
cron.monthly

In your case, since you want your script to run daily, you'd copy it into /etc/cron.daily.  Like any script, make sure it's executable.  All of the scripts in /etc/cron.daily will run as root in alphabetical order, so my scripts begin with "zz_" so that the system's scripts will run before mine.

Incidentally, I use anacron for the exact same purpose:  backups.

---

### Post by arrange on 2010-06-12
It's incorrect, it shouldn't be```
1 5 daily backup /home/john/backmeup.sh
```but```
1 5 backup /home/john/backmeup.sh
```

But the "cron.daily directory" way should work too.

---

### Post by windyrij on 2010-06-14
Hello again:

This is what I have now - still not working.


home/john/backmeup.sh
Code:
------------
#! /bin/sh
nice -n 19 /usr/bin/backintime --backup-job > /tmp/backmeup.log 2>&1
exit 0
----------------


Crontab (john)
Code:
----------------

#*/1 * * * * /home/john/backmeup.sh
@daily nice -n 19 /usr/bin/backintime --backup-job >/dev/null 2>&1

----------------


/etc/anacrontab
Code:
---------------
latest# /etc/anacrontab: configuration file for anacron

# See anacron(8) and anacrontab(5) for details.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin:/home/john

# These replace cron's entries
1    5    cron.daily     nice run-parts --report /etc/cron.daily
7    10    cron.weekly     nice run-parts --report /etc/cron.weekly
@monthly    15    cron.monthly nice run-parts --report /etc/cron.monthly
---------------

/etc/cron.daily
Listing:
---------------
/etc/cron.daily/0anacron
/etc/cron.daily/apport
/etc/cron.daily/apt
/etc/cron.daily/aptitude
/etc/cron.daily/bsdmainutils
/etc/cron.daily/dpkg
/etc/cron.daily/logrotate
/etc/cron.daily/man-db
/etc/cron.daily/mlocate
/etc/cron.daily/popularity-contest
/etc/cron.daily/sendmail
/etc/cron.daily/standard
/etc/cron.daily/zz-backmeup.sh
---------------
zz-backmeup.sh is a re-named copy of /home/john/backmeup.sh


Where have I gone wrong?


Many thanks,   John

---

### Post by afrodeity on 2010-06-26
crontab -e gives me this line:
```

@weekly nice -n 19 /usr/bin/backintime --backup-job >/dev/null 2>&1

```

The damn thing is running on a late Saturday exactly when I want to party with net radio trance streams. Needless to say, the system bus doesn't like the information buzzing around, even though I have plenty of memory, ram and cable.

Now I seriously need to regain control over my cron schedule. How to set the exact time and day??

---

### Post by windyrij on 2010-06-28
Hello afrodeity:

I would hesitate to give advice, being unable to get my system (switched off at night) to do backups), but from reading the Ubuntu documentation and the man page for crontab, i would suggest something like:

This should backup at 04:01 every Monday morning.

01 04 * * 1 nice -n 19 /usr/bin/backintime --backup-job >/dev/null 2>&1

Hope this helps,

windyrij

---

