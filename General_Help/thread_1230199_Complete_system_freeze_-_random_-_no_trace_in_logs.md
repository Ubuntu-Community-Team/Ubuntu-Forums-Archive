---
title: "Complete system freeze - random - no trace in logs - not hardware - help please!"
date: 2009-08-03
forum: General Help
---

### Post by musther on 2009-08-03
My system keeps randomly freezing (complete freeze, forcing hard reset) - doesn't happen in other operating systems etc, so not hardware, hardware thoroughly tested.  No entries in logs at the time of freeze, they just stop:

Core 2 Quad 2.33Ghz
4Gb RAM
Gigabyte GA-EG31MF-S2
500GB SATA Drive
EXT4 partitions
Ubuntu 9.04 64bit

Any further information, please request it.  Any suggestions? Comments?

---

### Post by robert shearer on 2009-08-03
when it freezes are you able to reboot using RSEIUB rather than a hard reset ?

RSEIUB info here...
[http://techpatterns.com/forums/about911.html](http://techpatterns.com/forums/about911.html)

[http://www.brunolinux.com/01-First_Things_To_Know/Run-Away_Processes.html](http://www.brunolinux.com/01-First_Things_To_Know/Run-Away_Processes.html)

[http://www.brunolinux.com/01-First_Things_To_Know/Skinny_Elephants.html](http://www.brunolinux.com/01-First_Things_To_Know/Skinny_Elephants.html)

---

### Post by musther on 2009-08-03
Never heard of it before, will let you know at next crash.  Cheers

---

### Post by Koobi on 2009-08-03
if you are using the 2.6.28-11 kernel, this is probably the problem:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/346691?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/346691?comments=all)

you can view the kernel version using:
```

uname -a

```

I had the same problem, now I can't even access my other hard disk:
[http://ubuntuforums.org/showthread.php?p=7721887](http://ubuntuforums.org/showthread.php?p=7721887)

---

### Post by musther on 2009-08-03
I looked at that bug with interest, but I'm running kernel 2.6.28-15.

I've been ploughing through my logs, and there's nothing happening even close to the crash time, but eventually I found my way to auth.log and found this:

```
Aug  3 20:20:01 dominus CRON[7576]: pam_unix(cron:session): session closed for user root
Aug  3 20:30:01 dominus CRON[8198]: pam_unix(cron:session): session opened for user root by (uid=0)
Aug  3 20:30:01 dominus CRON[8198]: pam_unix(cron:session): session closed for user root
Aug  3 20:39:01 dominus CRON[8754]: pam_unix(cron:session): session opened for user root by (uid=0)
Aug  3 20:39:01 dominus CRON[8754]: pam_unix(cron:session): session closed for user root
Aug  3 20:40:01 dominus CRON[8876]: pam_unix(cron:session): session opened for user root by (uid=0)
Aug  3 20:40:01 dominus CRON[8876]: pam_unix(cron:session): session closed for user root
Aug  3 20:50:01 dominus CRON[9477]: pam_unix(cron:session): session opened for user root by (uid=0)
Aug  3 20:50:01 dominus CRON[9477]: pam_unix(cron:session): session closed for user root
Aug  3 21:00:01 dominus CRON[10121]: pam_unix(cron:session): session opened for user root by (uid=0)
Aug  3 21:00:01 dominus CRON[10122]: pam_unix(cron:session): session opened for user root by (uid=0)
Aug  3 21:00:01 dominus CRON[10122]: pam_unix(cron:session): session closed for user root
Aug  3 21:00:01 dominus CRON[10121]: pam_unix(cron:session): session closed for user root
Aug  3 21:09:01 dominus CRON[10629]: pam_unix(cron:session): session opened for user root by (uid=0)
Aug  3 21:09:01 dominus CRON[10629]: pam_unix(cron:session): session closed for user root
Aug  3 21:10:01 dominus CRON[10751]: pam_unix(cron:session): session opened for user root by (uid=0)
Aug  3 21:10:01 dominus CRON[10751]: pam_unix(cron:session): session closed for user root
Aug  3 21:17:01 dominus CRON[11215]: pam_unix(cron:session): session opened for user root by (uid=0)
Aug  3 21:17:01 dominus CRON[11215]: pam_unix(cron:session): session closed for user root
Aug  3 21:20:01 dominus CRON[11423]: pam_unix(cron:session): session opened for user root by (uid=0)
Aug  3 21:20:01 dominus CRON[11423]: pam_unix(cron:session): session closed for user root
Aug  3 21:30:01 dominus CRON[12024]: pam_unix(cron:session): session opened for user root by (uid=0)
Aug  3 21:30:01 dominus CRON[12024]: pam_unix(cron:session): session closed for user root
```

21:30, according to the frozen desktop clock, is exactly when this particular crash occured - and I find these root cron sessions opening at the time of crashes in general.  I'm guessing it's just a coincidence though - seems to be something to do with cron.hourly, but I don't understand why it's happening every few minutes, with seemingly random intervals.

---

