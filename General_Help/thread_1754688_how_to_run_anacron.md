---
title: "how to run anacron"
date: 2011-05-10
forum: General Help
---

### Post by kaykav on 2011-05-10
Good morning
              Well I'm totally frustrated. I have been trying to figure out how to use anacron (schedule tasks). I Googled,Binged,Yahooed, and manpaged.I cannot find how to, at least, start anacron. To use 'cron' I use  crontab -e. What do i use to start anacron?.   Thank you

---

### Post by Dave_L on 2011-05-10
As far as I know, anacron (if installed) runs automatically.  By default, it runs the system cron scripts in /etc/cron.daily, /etc/cron.weekly and /etc/cron.monthly, as configured in /etc/anacrontab.

It doesn't run the user cron tasks in /var/spool/cron/crontabs, which are specified with crontab -e.

---

### Post by Cheesehead on 2011-05-11
At is for one-time, scheduled tasks.  (At 4:30, make me a sandwich)
Cron is for recurring, scheduled tasks. (Every weekday at 4:30, make me a sandwich, and archive the old sandwich)
Anacron is for systems that are not turned on 24/7. It simply tries to figure out what cron should have run during the off period, eliminates the duplicates and the moot, and does it for cron. (Don't make sandwiches for the three days the system was off)

So you probably should not be trying to do 'anacron tasks'. Instead, recurring jobs are simply 'cron jobs', and one-time tasks are simply 'at jobs'.

If you tell us what kind of job you want to run, we can probably help guide you.

---

### Post by Rytron on 2012-04-18
Can all cron tasks be put in anacron instead?

Can someone post a few anacron examples?

---

### Post by dcstar on 2012-04-18
> **Rytron said:**
> Can all cron tasks be put in anacron instead?

Can someone post a few anacron examples?

Your system is already full of Anacron tasks, go look for them.

---

### Post by Rytron on 2012-04-18
> **dcstar said:**
> Your system is already full of Anacron tasks, go look for them.

I refer to the file, **/etc/anacrontab**. What would be an example entry for it?

---

### Post by Dave_L on 2012-04-18
I don't understand your question.

The scripts in /etc/cron.daily, /etc/cron.weekly and /etc/cron.monthly are automatically run by anacron.

My /etc/anacrontab looks like this:

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

You don't need to change /etc/anacrontab, unless you want to alter the default behaviour.

If you do need to change it, the man page for anacrontab explains its format: [http://manpages.ubuntu.com/manpages/lucid/en/man5/anacrontab.5.html](http://manpages.ubuntu.com/manpages/lucid/en/man5/anacrontab.5.html)

---

### Post by Rytron on 2012-04-19
Sorry, I am new to anacron and am trying to figure it out.

I ran ```
gksudo gedit /etc/crontab
``` and had these (both worked fine):
[COLOR="Indigo"]42 *	* * *	root	updatedb
05 9	* * *	rytron	recollindex[/COLOR]

I removed them and added like so to /etc/anacrontab (to test them out):

[COLOR="Indigo"]1       5      rytron	recollindex
1       15      root	updatedb[/COLOR]

[COLOR="Red"]1       15      root	updatedb[/COLOR] seems to work but not recollindex.

Should I leave everything in gksudo gedit /etc/crontab? How would I make it so that these would be updated (via anacron) even if missed in cron due to turning PC on at lets say 10am?
[COLOR="Indigo"]42 *	* * *	root	updatedb
05 9	* * *	rytron	recollindex[/COLOR]

---

### Post by Rytron on 2012-04-20
I will ditch anacron and go back to crontab.

---

### Post by Paqman on 2012-04-20
> **Cheesehead said:**
> At is for one-time, scheduled tasks.  (At 4:30, make me a sandwich)
Cron is for recurring, scheduled tasks.


There's no reason anacron can't be used for recurring tasks. That's what it's designed for. The actual difference is this:

> 
Anacron is for systems that are not turned on 24/7.


I much prefer anacron because it's so much simpler to use. To schedule a job in anacron you just drop the script into the right folder. Too easy! Cron is only really necessary if you need fine-grained control, such as requiring the job to run at a *specific* time of day, instead of just once a day.

---

### Post by Rytron on 2012-04-20
> **Paqman said:**
> ...To schedule a job in anacron you just drop the script into the right folder...

Hi Paqman.

So anacron only deals with scripts? What folder(s)?

For things like **1       15      root	updatedb** - i'd be better off stick with crontab?

---

### Post by Paqman on 2012-04-20
> **Rytron said:**
> 
So anacron only deals with scripts? What folder(s)?


Yes, but a script can be a single command. The folders are at /etc/cron.daily, /etc/cron.weekly and so on. Drop it in the one you want and it's all done.

> 
For things like **1       15      root	updatedb** - i'd be better off stick with crontab?

If it had to be run at exactly that time of day, yes. If there was a chance the machine would be powered down at that time, and/or if it doesn't matter what time of day it ran then use anacron.

---

### Post by Rytron on 2012-04-20
> **Paqman said:**
> Yes, but a script can be a single command. The folders are at /etc/cron.daily, /etc/cron.weekly and so on. Drop it in the one you want and it's all done.

If it had to be run at exactly that time of day, yes. If there was a chance the machine would be powered down at that time, and/or if it doesn't matter what time of day it ran then use anacron.

Cheers Paqman.

---

### Post by Rytron on 2012-04-21
Can I have a few commands in 1 text file and drop them there (/etc/cron.daily, /etc/cron.weekly)?
Do the files have to be executable?
Do they need to end in .sh? Do they need to be in the usual format of [COLOR="DarkOrange"]**#!/bin/sh ...**[/COLOR]?

I want **root updatedb** to run hourly and **rytron recollindex** to run daily.

---

### Post by Paqman on 2012-04-21
> **Rytron said:**
> Can I have a few commands in 1 text file and drop them there (/etc/cron.daily, /etc/cron.weekly)?
Do the files have to be executable?
Do they need to end in .sh? Do they need to be in the usual format of [COLOR="DarkOrange"]**#!/bin/sh ...**[/COLOR]?

I want **root updatedb** to run hourly and **rytron recollindex** to run daily.

Create two text files, put #!/bin/bash on the first line, then your command(s), save the file with any name you want (file extensions are not needed), mark as executable and drop them into the appropriate folder. So the one with root updatedb would go in /etc/cron.hourly and the other one in /etc/cron.daily

---

### Post by Rytron on 2012-04-21
> **Paqman said:**
> Create two text files, put #!/bin/bash on the first line, then your command(s), save the file with any name you want (file extensions are not needed), mark as executable and drop them into the appropriate folder. So the one with root updatedb would go in /etc/cron.hourly and the other one in /etc/cron.daily

Ok.
So in /cron.daily I have the file **recollindex** with:
```
#!/bin/bash
1       5      rytron	recollindex
```

and in /cron.hourly I have the file **updatedb** with:
```
#!/bin/bash
1       15      root	updatedb
```

All ok?

---

### Post by Paqman on 2012-04-21
> **Rytron said:**
> Ok.
So in /cron.daily I have the file **recollindex** with:
```
#!/bin/bash
1       5      rytron	recollindex
```

and in /cron.hourly I have the file **updatedb** with:
```
#!/bin/bash
1       15      root	updatedb
```

All ok?

Close, try:
```
#!/bin/bash
recollindex > /location/where/you/want/your/output
```
and:
```
#!/bin/bash
updatedb
```

However, the updatedb one may be a bit superfluous, as one of the default jobs in anacron runs it daily anyway.

---

### Post by Rytron on 2012-04-21
> **Paqman said:**
> Close, try:
```
#!/bin/bash
recollindex > /location/where/you/want/your/output
```


Please elaborate on the part "***/location/where/you/want/your/output***". I only used ***recollindex*** to update **recoll**.

---

### Post by Paqman on 2012-04-21
> **Rytron said:**
> Please elaborate on the part "***/location/where/you/want/your/output***". I only used ***recollindex*** to update **recoll**.

Ok, skip that bit then.

---

### Post by Rytron on 2012-04-21
> **Paqman said:**
> Ok, skip that bit then.

Ok, so recollindex file and command is setup in cron.daily. Will it run today immediately or begin running tomorrow?

---

### Post by Paqman on 2012-04-21
Depends what time of day it is. IIRC the default time for anacron to run is 07:30, so if it's after that I wouldn't expect it to run until tomorrow. You can of course run it manually if you want to:
```
./etc/cron.daily/recollindex
```

---

### Post by Rytron on 2012-04-22
> **Paqman said:**
> Depends what time of day it is. IIRC the default time for anacron to run is 07:30, so if it's after that I wouldn't expect it to run until tomorrow. You can of course run it manually if you want to:
```
./etc/cron.daily/recollindex
```

I booted my computer today at around 10am and recoll has **not** been updated.

---

### Post by Dave_L on 2012-04-22
Please post the output from these:

```
cat /etc/anacrontab
```

```
ll -h /var/spool/anacron/
```

---

### Post by Rytron on 2012-04-22
> **Dave_L said:**
> Please post the output from these:

```
cat /etc/anacrontab
```

# /etc/anacrontab: configuration file for anacron

# See anacron(8) and anacrontab(5) for details.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# These replace cron's entries
1       5       cron.daily       nice run-parts --report /etc/cron.daily
7       10      cron.weekly      nice run-parts --report /etc/cron.weekly
@monthly        15      cron.monthly nice run-parts --report /etc/cron.monthly



> **Dave_L said:**
> 
```
ll -h /var/spool/anacron/
```

ll: command not found

$ **[COLOR="Red"]l[/COLOR]** -h /var/spool/anacron/
total 28K
drwxr-xr-x  2 root root 4.0K 2012-04-18 13:59 .
drwxr-xr-x 13 root root 4.0K 2012-02-26 20:50 ..
-rw-------  1 root root    9 2012-04-22 10:22 cron.daily
-rw-------  1 root root    9 2012-04-08 09:34 cron.monthly
-rw-------  1 root root    9 2012-04-18 08:34 cron.weekly
-rw-------  1 root root    9 2012-04-20 09:18 rytron
-rw-------  1 root root    9 2012-04-20 09:18 root

---

### Post by Dave_L on 2012-04-22
> **Rytron said:**
> -rw-------  1 root root    9 2012-04-22 10:22 cron.daily

That tells you that anacron last ran the /etc/cron.daily scripts at 10:22 on 2012-04-22.

---

### Post by Rytron on 2012-04-22
> **Dave_L said:**
> That tells you that anacron last ran the /etc/cron.daily scripts at 10:22 on 2012-04-22.

I'm curious as to why it did not run the script 'recollindex' containing:
```
#!/bin/bash
recollindex
```

---

### Post by Rytron on 2012-04-22
For arguments sake - could I run multiple commands in a single file titled 'daily_tasks' within cron.daily like this example:

```
#!/bin/bash
rytron recollindex
root updatedb
```

---

### Post by Dave_L on 2012-04-22
You can have multiple commands, but those are not valid bash commands.

I would direct the output to a file. For example:

```
#!/bin/bash
date >>/home/rytron/recollindex.log
recollindex >>/home/rytron/recollindex.log 2>&1
date >>/home/rytron/updatedb.log
updatedb >>/home/rytron/updatedb.log 2>&1
```

You could also check the system logs for diagnostics. I don't recall offhand which ones to look at it, but there aren't that many.

I don't know anything about recollindex or updatedb. Are they bash scripts, or executables?

---

### Post by Rytron on 2012-04-22
> **Dave_L said:**
> You can have multiple commands, but those are not valid bash commands.

I would direct the output to a file. For example:

```
#!/bin/bash
date >>/home/rytron/recollindex.log
recollindex >>/home/rytron/recollindex.log 2>&1
date >>/home/rytron/updatedb.log
updatedb >>/home/rytron/updatedb.log 2>&1
```

You could also check the system logs for diagnostics. I don't recall offhand which ones to look at it, but there aren't that many.

I don't know anything about recollindex. Is it a bash script, or an executable?

Thank you Dave_L for the info.
I don't know if recollindex is a bash script or an executable either.
I will go back to crontab but I will keep these notes if I choose to try anacron again in the future.
Cheers.

---

