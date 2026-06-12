---
title: "Natty Lockups - Recorded in a Log File?"
date: 2011-06-02
forum: General Help
---

### Post by jdholman on 2011-06-02
Hello:

I am on 64-bit Natty and for the first time since my install a month ago, I have had a system hang requiring a power-off restart.  It happened yesterday and a few moments ago.

My question is that I want to troubleshoot this myself and wonder if the activities that my system were running just prior to crashing are recorded in a log file somewhere.

I used to look int /var/log.messages or /var/log/boot, but this was in the Maverick days.

Any thoughts on where to start?

Thanks,

Jim

---

### Post by Rubi1200 on 2011-06-02
In general, you should find information in messages, syslog, and dmesg:

```
dmesg | less

cat /var/log/messages | less

cat /var/log/syslog | less
```If you suspect a specific device or other factor is causing the problem, use grep (it will be less time consuming).

For example,

```
egrep -e fail /var/log/messages
```Replace fail with any other search term.

---

### Post by jdholman on 2011-06-02
Thanks Rubi.

dmesg has some good information starting at my last boot. /var/log/messages is empty and /var/log/sysinfo has some nice stuff in there but nothing that I could see that seemed to be when I crashed.

Would syslog be where Ubuntu writes info on crashes, kernel panics, and other issues or am I looking in the wrong place?  I was hoping to see what it did at 0913 local time that made it crash.  Perhaps it's not that easy.

Thanks,

Jim

---

