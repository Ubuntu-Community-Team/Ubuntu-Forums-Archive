---
title: "Strange behaviour: CRON requires having logged in to do sudo commands"
date: 2009-07-17
forum: General Help
---

### Post by HotForLinux on 2009-07-17
This is sort of a ramification of my previous thread:

[COLOR=DimGray][**Can sudoers sudo in their crontabs? - How?  **]("http://ubuntuforums.org/showthread.php?t=1212910")[/COLOR]

[COLOR=Red](edit): [/COLOR]But it points out other problems I'm facing using crontabs with sudo commands.  


(A)
As soon as the system boots, CRON starts executing the jobs that users have in their crontabs at their due time, even if the users have not yet logged in **_EXCEPT_** those that include a sudo-command and the user can execute without the need of password identification.

The moment the user loggs in (and even out) CRON is able to execute the jobs that include sudo commands too.


```

**cat /home/user/cron/CRON.LOG**
16 Jul 23:35:03 ntpdate[20020]: adjust time server 91.189.94.4 offset -0.013027 sec
Thu Jul 16 23:35:03 CEST 2009 - ~/cron/ntpdate.sh
17 Jul 00:35:03 ntpdate[21011]: adjust time server 62.93.230.13 offset -0.007102 sec
Fri Jul 17 00:35:03 CEST 2009 - ~/cron/ntpdate.sh
[COLOR=Gray]          <---- System Shutdown ---->[/COLOR]

[COLOR=Gray]         <---- System Reboot   ---->[/COLOR]
[COLOR=Gray](CRON is not doing all commands in user's crontab s cript:)[/COLOR]
Fri Jul 17 11:35:01 CEST 2009 - ~/cron/ntpdate.sh
Fri Jul 17 12:35:01 CEST 2009 - ~/cron/ntpdate.sh
Fri Jul 17 13:35:01 CEST 2009 - ~/cron/ntpdate.sh

[COLOR=Gray]          <---- user, owner of the crontab, logged in AND OUT at 14:30 ---->[/COLOR]
[COLOR=Gray](CRON starts doing ALL commands in user's crontab script, including sudo commands:)[/COLOR]
17 Jul 14:35:02 ntpdate[8503]: adjust time server 192.33.96.102 offset 0.079122 sec
Fri Jul 17 14:35:02 CEST 2009 - ~/cron/ntpdate.sh

```As you can see, one part of the job in the crontab is not being done even if it is in the same script.


Is this how it should be?
I don't see any reason why.
Is there any way to avoid this?

According to what I have been observing around a user can never be sure if his jobs are going to be done or not until he has done all kinds of unimaginable tests.
------

(B)
A script whose filename includes a dot (file.name) placed in /etc/cron.hourly is not being done.
The same script with an underscore (file_name) in the name is done perfectly.

Is this normal?

---

### Post by LightningCrash on 2009-07-17
If you don't already have it, you probably need a nopasswd line in your /etc/sudoers for ntpdate.

---

### Post by HotForLinux on 2009-07-17
Thanks but I'm talking about a completely different thing here.

(In the previous thread that I mentioned above I talked about that issue. Not only the line you say is needed in the sudoers file, but attention should be paid to the position it occupies in that file)

---

### Post by LightningCrash on 2009-07-17
> **HotForLinux said:**
> Thanks but I'm talking about a completely different thing here.

(In the previous thread that I mentioned above I talked about that issue. Not only the line you say is needed in the sudoers file, but attention should be paid to the position it occupies in that file)

If I have time I'll play around with it. Probably end up stracing the cron jobs while I'm logged in and logged out.

I just put in a nopasswd line today after the %admin line and it worked just fine with nopasswd, didn't prompt. So we'll see.

---

### Post by HotForLinux on 2009-07-18
The problem is not that cron doesn't do your sudo commands in your crontab scripts when you are logged out but that it doesn't do them _BEFORE YOU LOG IN_ for the first time _after a reboot_.

---

