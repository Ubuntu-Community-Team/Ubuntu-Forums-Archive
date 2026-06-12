---
title: "Run command every sunday at 8pm using at?"
date: 2011-08-08
forum: General Help
---

### Post by thegoonden on 2011-08-08
The at manual is not much help for this, it's quite poor in general.

All I want to do is set the machine to run a certain command (or a few) at 8 o'clock on a Sunday evening. The manual is no help, google (google keeps telling me how to do it with different cron demins rather than at) is no help, I'm at my wits' end.

Surely somebody somewhere on earth has needed to do this before??????


Thanks for reading:D

---

### Post by tweakmy on 2011-08-08
you check out cron

---

### Post by thegoonden on 2011-08-08
So I have to ditch at and use something else?

OK, thanks.

---

### Post by thegoonden on 2011-08-08
That seems to be the way, thanks again :D

---

### Post by thegoonden on 2011-08-08
OOOOPS not actually solved at all.......


service cron start
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.102" (uid=1000 pid=4732 comm="start cron ") interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init"))


What?

LOL.....would HELP if I ran it with sudo really wouldn't it.

Except now I don't know why it didn't run my test command (I had thought cron wasn't running)

THIS is why I like "at" it works :D

---

### Post by fdrake on 2011-08-08
> **thegoonden said:**
> OOOOPS not actually solved at all.......


service cron start
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.102" (uid=1000 pid=4732 comm="start cron ") interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init"))


What?

LOL.....would HELP if I ran it with sudo really wouldn't it.

Except now I don't know why it didn't run my test command (I had thought cron wasn't running)

THIS is why I like "at" it works :D

modify this file
```
gedit /etc/crontab
or  EDIT:suggested by yetiman64
crontab -e
> 0 8 ? * 0 * command

```

---

### Post by yetiman64 on 2011-08-08
> **fdrake said:**
> modify this file
```
gedit /etc/crontab
```

@ fdrake /etc/crontab is owned by root and gedit is a graphical app. A better command for that would be ```
gksudo gedit /etc/crontab
```**OR** the OP can directly edit his/her or root's crontabs (probably a better idea than doing system wide with /etc/crontab) with the command ```
sudo crontab -e
``` for root or ```
crontab -e
``` for user.

---

### Post by thegoonden on 2011-08-08
I got it sorted, crontab doesn't much care for the use of && or backticks

---

