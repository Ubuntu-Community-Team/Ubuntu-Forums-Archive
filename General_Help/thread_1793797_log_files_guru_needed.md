---
title: "log files guru needed"
date: 2011-06-30
forum: General Help
---

### Post by pikamoku on 2011-06-30
hi m8s
my first problem is I've no idea where in this forum I should post my problem. I need some kind of log files reader to help me to identify what causes a load freeze with normal kernels but picking "recovery mode" mode kernel on grub the system works fine after log and startx manually.

I tried to read the /var/log/dmesg to find out whats happening but I dont understand it. It's likely that the answer is there :confused:

So please, where should I make my question? Once there I'll be more specific about my system and possible problem's source

regards and thank you for helping me

---

### Post by Rubi1200 on 2011-07-01
Hi,
please post the specifications for the computer, which version of Ubuntu you are using, as well as any other information such as when the problem started etc.

You can also use egrep to search the logs for information. 

For example,

```
egrep -e root /var/log/messages | more
```

This would look for a pattern with root as the word you are searching for. Obviously, change "root" and use other keywords.

By the way, Ubuntu comes with a log file reader called Log File Viewer which you can access via System > Administration.

---

