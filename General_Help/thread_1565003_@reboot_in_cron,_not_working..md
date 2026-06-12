---
title: "@reboot in cron, not working."
date: 2010-08-31
forum: General Help
---

### Post by zeefreak on 2010-08-31
i've got an ubuntu server installation [10.04 lts] and i'm trying to get a virtualbox to start at boot time.

i've been doing some reading on how to achieve this in a simple manner, without the need for init scripts. my research has led me to vixie cron, which is apparently used as the standard ubuntu cron. according to the man page, and various other pages on the web, it should support directives like @reboot instead of the time fields.

the problem is that it simply doesn't work. in my user's crontab, i have

```
@reboot VBoxHeadless --startvm vm_name >> /home/user/vbox.log
```

copying this code [without the @reboot] to the command line works perfectly. it starts a headless virtualbox and logs the output to /home/user/vbox.log in cron however, it does nothing. saving the crontab completes with no errors, but on boot, nothing happens. nothing is logged to /home/user/vbox.log nothing is logged to /var/log/syslog

basically, i cannot understand why there are so many pages saying yay! @reboot is awesome and so easy! when it just doesn't seem to work at all. am i missing something here?

---

### Post by DaithiF on 2010-08-31
Hi, 
2 suggestions:
1. explicit path to VBoxHeadless,
2. capture stderror output: >> /home/user/vbox.log** 2>&1**

---

### Post by zeefreak on 2010-09-04
> **DaithiF said:**
> Hi, 
2 suggestions:
1. explicit path to VBoxHeadless,
2. capture stderror output: >> /home/user/vbox.log** 2>&1**

i tried both of these suggestions, but vbox still doesn't come up, vbox.log still isn't even created . . .

---

