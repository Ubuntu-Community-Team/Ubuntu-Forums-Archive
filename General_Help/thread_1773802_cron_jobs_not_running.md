---
title: "cron jobs not running"
date: 2011-06-02
forum: General Help
---

### Post by 1juanpa1 on 2011-06-02
Hello,

I have a cron job that executes fine in opensuse 11.4. It is located in

/etc/cron.d/publish.cron:

-----------------------
* * * * * jpablo /srv/django-apps/smcommand/scripts/publish.sh
-----------------------


It is correct, I want it to execute every minute.


Now, I copied the same script to ubuntu maverick, and it doesn't run.

Perhaps there's some ubuntu peculiarity that I'm not aware of?

Regards,

  Juan Pablo

---

### Post by ruffEdgz on 2011-06-02
Have you checked the /var/log/messages to see what it says about it? If you changed your rsyslog for cron messages to to another file, just change the code suggestion below to that path:
```

sudo grep -i "cronname" /var/log/messages

```

Also, if I want a job to execute every minute, I just do:
```

*/1 * * * * /path/to/cron/job.sh

```
But your way could work as well. That is what I have been told works for every minute.

---

### Post by 1juanpa1 on 2011-06-02
The problem is that cron seems to be ignoring the file altogether. 

In opensuse whenever I modify the file there's a confirmation message in /var/log/messages:

/usr/sbin/cron[2529]: (*system*) RELOAD (/etc/cron.d/publish.cron)

But on ubuntu there isn't such message.

---

### Post by seawolf167 on 2011-06-02
Couple things.

Enable logging of cron messages to /var/log/cron.log

```
sudo gedit /etc/rsyslog.d/50-default.con
```then uncomment the line

```
cron.*         /var/log/cron.log
```restart the cron service, now you can see your logs a little easier in /var/log/cron.log

```
sudo service cron restart
```does the bash script work in a terminal like it should outside of cron?

is the file executable?

```
chmod u+x /srv/django-apps/smcommand/scripts/publish.sh
```does the user "jpablo" have access/execute permission on that file?

you may also need to add

```
SHELL=/bin/sh:/bin/bash
```to the top of the /etc/crontab file, then save and restart cron

```
sudo service cron restart
```

---

### Post by 1juanpa1 on 2011-06-02
It's solved!

The problem was that the cron filename had a dot in it, and cron doesn't like that, so it was ignoring the file.

Thanks!

  Juan Pablo

---

### Post by seawolf167 on 2011-06-02
That was easy - glad its fixed!

---

