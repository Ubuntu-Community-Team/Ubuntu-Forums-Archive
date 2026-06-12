---
title: "Can't get cron to work..."
date: 2010-01-06
forum: General Help
---

### Post by jeff[0] on 2010-01-06
Hey guys, I've been trying to accomplish this on my own, but I can't seem to figure it out... but I've been off researching and learning on my own, I promise!

All I'm trying to do (for learning purposes) is to get a message to print out to a log file every 5 minutes.

This is on Ubuntu Server 6.06.

Logged in as root ( I know, I know, should have sudo'd, oh well...;) )

Created a new file with this in it:
```
echo "This is teh win: $(date)" >> /tmp/thisistestlog.log
```

Saved this file as "baktest" in /usr/bin/

At prompt, typed in: crontab -e

Added this line:
```
0-59/5 * * * * /usr/bin/baktest
```
( I wasn't sure the proper command to try every 5 minutes, but this is my latest iteration. I also started with just */5, and that didn't seem to work either. )

Saved and exited crontab.

Console reports: 
> crontab: installing new crontab

Using command: ps -ef | grep cron
> root@mail:/tmp# ps -ef | grep cron
root     23444     1  0 Jan05 ?        00:00:00 /usr/sbin/cron
root     26149 18771  0 12:19 pts/1    00:00:00 grep cron


So I waited 10 minutes to be safe.... and saw no log file appear.

I checked this page here: [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

I wasn't sure what it meant by the PATH= variable they wanted me to set, my /etc/crontab file states:
```
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
```

But I didn't know if it meant there, or in my crontab -e location, so after the first failed attempt, I added the line from that webpage as well to crontab -e:
```
PATH=/usr/sbin:/usr/bin:/sbin:/bin
```

Waited another 10 minutes to be safe, still nothing.

What can I be doing wrong? I'm sure it's super obvious to you guys. :)

---

### Post by iponeverything on 2010-01-06
you could just add it to /etc/crontab

---

### Post by jeff[0] on 2010-01-06
> **iponeverything said:**
> you could just add it to /etc/crontab

Well, according to [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto), it says I really shouldn't... ;p

---

### Post by z0n on 2010-01-06
Is your script is executable?

Try this:
sudo chmod 755 /usr/bin/baktest

For good measure, execute your script from your shell:
/usr/bin/baktest

..and check that log-file of yours to confirm.

---

### Post by jeff[0] on 2010-01-06
> **z0n said:**
> Is your script is executable?

Try this:
sudo chmod 755 /usr/bin/baktest

For good measure, execute your script from your shell:
/usr/bin/baktest

..and check that log-file of yours to confirm.

Oh snap, I think it was the chmod that did it... Ran the script manually and it worked, waited for some time and it appears another message was added to the log file on it's own from the 5 minute timer.

Thanks so much man.

---

