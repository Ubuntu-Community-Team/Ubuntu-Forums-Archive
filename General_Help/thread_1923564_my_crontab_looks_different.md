---
title: "my crontab looks different"
date: 2012-02-10
forum: General Help
---

### Post by nslegacy163 on 2012-02-10
Hi gang, 

 I want to create a cron job for my rsync. I have it all figured out thanks to [_[COLOR="Blue"]this[/COLOR]_]("http://linuxbasement.com/content/backups-using-rsync-bash-cron") link but here is the weird part. I also have a Back in Time program snap-shot program running via the cron, but it's crontab looks like this: 
```
drew@drew-ubuntu-PC:~/Desktop$ crontab -l
@weekly nice -n 19 /usr/bin/backintime --backup-job >/dev/null 2>&1

```

 From anything I've read, the crontab should look something more like ```
 * * * * 0 /root/rsync-shell.sh 
``` (this is actually what I want, to run the rsync every week on Monday) but it doesn't look like that. I added that latter line to the crontab using crontab -e, saved it, then looked at the crontab again and it only lists the ```
@weekly
``` one. 

 What's the deal? How do I get this rsync added to the crontab?

 Thanks in advanced!

---

### Post by llamabr on 2012-02-10
That's ubuntu being user friendly.

[http://en.wikipedia.org/wiki/Cron#Predefined_scheduling_definitions](http://en.wikipedia.org/wiki/Cron#Predefined_scheduling_definitions)

---

### Post by nslegacy163 on 2012-02-10
> **llamabr said:**
> That's ubuntu being user friendly.

[http://en.wikipedia.org/wiki/Cron#Predefined_scheduling_definitions](http://en.wikipedia.org/wiki/Cron#Predefined_scheduling_definitions)

So, my crontab line should be, @weekly...? Then just the standard stuff?

---

