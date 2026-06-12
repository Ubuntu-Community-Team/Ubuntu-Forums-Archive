---
title: "Another Cron Not Working Post Damn Noob. :)"
date: 2010-03-16
forum: General Help
---

### Post by lvleph on 2010-03-16
For some reason my cron jobs are not running and I can't seem to figure out why.
Here is **crontab -l**
```
SHELL=/bin/sh
PATH=/sbin:/bin:/usr/sbin:/usr/bin
# m h  dom mon dow   command
*/30 * * * * flexget --cron
```
And here is the output of **ps -eaf | grep cron**
```

media     6804  6693  0 12:05 pts/0    00:00:00 grep --colour=auto cron
root     27831     1  0 Mar14 ?        00:00:00 cron
```
I have run the command outside of cron and it works fine. I am unsure what is going on.

---

### Post by CharlesA on 2010-03-16
Are you running a script or trying to run a program in cron?

---

### Post by lvleph on 2010-03-16
That is a program that is located in /usr/local/bin/
lol, I think I found my problem. I will try to add that to the path.

---

### Post by CharlesA on 2010-03-16
> **lvleph said:**
> That is a program that is located in /usr/local/bin/
lol, I think I found my problem. I will try to add that to the path.

Ah ok. For stuff I run in cron, I throw the commands in a script then tell cron to run the script. It seems to work for almost everything.

---

### Post by lvleph on 2010-03-16
Yep, I didn't have the PATH variable set correctly. It works now.

---

### Post by CharlesA on 2010-03-16
Awesome. :D

---

### Post by dcstar on 2010-03-17
> **lvleph said:**
> Yep, I didn't have the PATH variable set correctly. It works now.

The cron environment is not the same as a user environment.

It is always good practice to use full path definitions in all cron jobs and never assume that because something works in a user shell it will work via cron.

This sort of thing catches 99% of people who start using cron jobs.

---

### Post by lvleph on 2010-03-17
My problem was that originally I thought flexget was in /usr/bin.

---

