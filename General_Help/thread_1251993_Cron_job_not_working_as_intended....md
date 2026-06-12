---
title: "Cron job not working as intended..."
date: 2009-08-28
forum: General Help
---

### Post by Vunutus on 2009-08-28
I am attempting to set up my backup script to run every hour. I'm using the SpiderOak backup service, along with their client. Once configured, you can run a command to have it catalog new changes and upload as necessary. This seems like a very simple thing to automate.

I made a file called "spideroak" in /etc/cron.hourly and made it executable. The contents are as follows:

```

#!/bin/bash

SpiderOak --batchmode 
date >> /home/danny/cronspider

```

Unfortunately, it doesn't work. It RUNS, but it doesn't work. The line "SpiderOak --batchmode" works perfectly fine if I just execute it from a terminal. It takes a couple minutes to process new changes, uploads them to the offsite backup location, and exits. When it's executed by cron, nothing appears to happen and my files aren't uploaded. I know that the event is firing correctly because the date line executes and I have a file in my home folder with the date and time of every time it's run thus far (about 30 or so times).

What could cause this command to work in a normal terminal but not as a cron script? Is there something I'm overlooking?

---

### Post by pholden on 2009-08-28
Have you tried the script with the full path to SpiderOak?

You can run *which SpiderOak* at your terminal to find the full path.

---

### Post by Vunutus on 2009-08-28
> **pholden said:**
> Have you tried the script with the full path to SpiderOak?

You can run *which SpiderOak* at your terminal to find the full path.

Nope, I changed it to that and it still failed in the same way. This is frustrating.

One thing I thought of is the fact that although SpiderOak is installed for all users (in /usr/bin/SpiderOak), it's configuration files are in my own home directory. Is it possible that the program is actually running as root and just exiting with nothing to do because the configuration files are in my home directory?

How can I run a cron job as root and have it take my own configuration files? As far as I know, the program does not allow a config file to be passed to it on the command line.

---

### Post by dannyboy79 on 2009-08-28
> **Vunutus said:**
> Nope, I changed it to that and it still failed in the same way. This is frustrating.

One thing I thought of is the fact that although SpiderOak is installed for all users (in /usr/bin/SpiderOak), it's configuration files are in my own home directory. Is it possible that the program is actually running as root and just exiting with nothing to do because the configuration files are in my home directory?

How can I run a cron job as root and have it take my own configuration files? As far as I know, the program does not allow a config file to be passed to it on the command line.
just put SpiderOak config file in the same place that it is nn your home directory (example: /home/user/.spideroak/config) into root home directory (example: /root/.spideroak/config) good luck. also, there is a way to have commands run as a certain user within a batch script but you'll have to goggle that as I am not sure how to do that.

---

### Post by DaithiF on 2009-08-28
Hi, I would you suggest you run it from your own crontab, rather than from the system-wide one.  Otherwise it is running as root, and not only possible problems finding the config files, but maybe also changing the ownership of backed up files to root rather than you.

```
crontab -e
```
to edit your own crontab.
enter something like
```
10 * * * * /path/to/yourscript
```
to run hourly at 10 past the hour.

while verifying that it runs ok the first time or two you may want to capture output as it is run, to check for errors, etc.  In which case add something like:
```
10 * * * * /path/to/yourscript >> /home/you/somefile.log 2>&1

```
good luck

---

### Post by wojox on 2009-08-28
Is it called spideroak or spideroak.sh?

If spideroak.sh rename it spideroak

---

### Post by DaithiF on 2009-08-28
As wojox indicates, scripts ending in .sh (and more generally any script with a 'dot' in its filename) will NOT be run by the runparts mechanism which handles the entries in cron.hourly, .daily, .weekly, .monthly)

Individual users crontabs, and root's crontab don't suffer from this restriction though, so you can name your script whatever you want if you follow the suggestion to use your own user's crontab.

---

### Post by Vunutus on 2009-09-10
Thanks, I got the script working as intended by copying my SpiderOak config file to /root. 

I have two more questions, though.

First, would it be possible to make a symlink of /root/.SpiderOak that points to my user's SpiderOak config directory (/home/danny/.SpiderOak) so I don't have to always make sure I have the latest config in /root? I mean, I know it's POSSIBLE, but will it work in terms of the program finding the intended config directory?

Second, is there any legitimate reason that cron will not execute scripts with a dot in the filename? That seems like it could be #1 on a large list of "gotchas".

---

### Post by bulamab on 2009-10-05
Hi Vuntus,

I tried you solution, but it seems to be still not working for me. Did you copy thw whole .SpiderOak directory into the root directory, or just the config.txt?

Thanks!

Bulamab

---

### Post by Vunutus on 2009-10-05
> **bulamab said:**
> Hi Vuntus,

I tried you solution, but it seems to be still not working for me. Did you copy thw whole .SpiderOak directory into the root directory, or just the config.txt?

Thanks!

Bulamab

I copied the entire .SpiderOak directory to /root, then made sure my script in cron.hourly didn't have a . in it

---

