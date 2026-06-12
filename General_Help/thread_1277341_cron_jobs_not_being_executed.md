---
title: "cron jobs not being executed"
date: 2009-09-28
forum: General Help
---

### Post by badger_fruit on 2009-09-28
Ubuntu 9.04

Hello, I wonder if someone can help me diagnose a problem with a simple cronjob I have scheduled ...

```
sudo crontab -e
```

then added the line

```
00 04 * * * reboot
```

The idea being to reboot my machine at 4am every day.

Now, in order to test the job I moved the time to now+2 minutes (at the time of writing this would be 13:02) but it didn't run.

I've checked and there is no /etc/cron.allow or cron.deny files so according to the guides online, this means only root jobs will be done.

I've tailed /var/log/messages and there's nothing in there relating to cron, no errors, warnings, nothing.

If anyone's got any ideas on what I've done wrong (as it WILL be user error lol!) please can they advise; many thanks to all for reading

badger

---

### Post by DaithiF on 2009-09-28
Hi, the default PATH under cron is /usr/bin:/bin, whereas reboot is located in /sbin
so use the full path in your crontab, ie.:
```
/sbin/reboot 
```

---

### Post by badger_fruit on 2009-09-28
> **DaithiF said:**
> Hi, the default PATH under cron is /usr/bin:/bin, whereas reboot is located in /sbin
so use the full path in your crontab, ie.:
```
/sbin/reboot 
```


Hello, thanks for the help, yup, that worked!
Haha, silly me ... told you it would be USER ERROR!!!

Cheers

---

