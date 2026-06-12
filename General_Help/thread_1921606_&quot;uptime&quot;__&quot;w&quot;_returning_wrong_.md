---
title: "&quot;uptime&quot; / &quot;w&quot; returning wrong number of logged on users"
date: 2012-02-07
forum: General Help
---

### Post by gewone on 2012-02-07
**Hi!**


[I]```
gewone@LOSANGELES:~$ w
 09:12:22 up 164 days, 41 min,  6 users,  load average: 0,01, 0,05, 0,12
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
gewone     pts/0    11-11-11-111.cus 09:10    0.00s  0.53s  0.01s w

gewone@LOSANGELES:~$ uptime
 09:12:23 up 164 days, 41 min,  6 users,  load average: 0.01, 0.05, 0.12

gewone@LOSANGELES:~$
```[/I]Why may it say that 6 users are logged on, when it's actually just me?
I know for a fact rebooting fixes the issue (I've had it before), but I don't want to.
What daemon/service should I restart to "get a clean slate", so to speak?

**Cheers!**

---

### Post by HiImTye on 2012-02-07
try to list them all
```
sudo who -u -d
```

---

### Post by gewone on 2012-02-07
```
gewone@LOSANGELES:~$ who -u -d
gewone   pts/0        2012-02-07 13:56   .         24416 (cust123.localty.isp.co.uk)
         pts/1        2011-12-08 20:34             21305 id=ts/1  term=0 exit=0
         pts/2        2012-02-07 13:56             22931 id=ts/2  term=0 exit=0
         pts/3        2011-11-11 22:47             31405 id=ts/3  term=0 exit=0
         pts/4        2011-11-07 20:36             11839 id=/4    term=0 exit=0
         pts/4        2011-11-09 20:00             23958 id=ts/4  term=0 exit=0
         pts/5        2011-11-09 20:00             24126 id=/5    term=0 exit=0
         pts/7        2011-11-09 19:30             24267 id=ts/7  term=0 exit=0
         pts/5        2011-12-15 22:59             18877 id=ts/5  term=0 exit=0
         pts/11       2011-11-09 20:00             24679 id=s/11  term=0 exit=0
         tty8         2011-12-13 11:55             27982 id=:1    term=0 exit=0
         pts/1        2011-12-11 17:14             28379 id=p1    term=0 exit=2

gewone@LOSANGELES:~$ who -u
gewone   pts/0        2012-02-07 13:56   .         24416 (cust123.localty.isp.co.uk)

gewone@LOSANGELES:~$ w
 13:57:47 up 164 days,  5:27,  6 users,  load average: 0,04, 0,08, 0,02
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
gewone   pts/0    cust123.localty.isp.co.uk  13:56    0.00s  0.69s  0.01s w

```

Really weird.

**Ideas?**

---

### Post by gewone on 2012-02-19
**Bump.**

Ideas?

---

### Post by dcstar on 2012-02-20
> **gewone said:**
> **Bump.**

Ideas?

You have the Process IDs of the sessions, see what they are doing.

---

### Post by Khayyam on 2012-02-20
utmp (which "w" and "uptime" query) isn't very reliable, and can become corrupted. The following should clear the log

```
sudo tee /var/run/utmp </dev/null
```HTH ... khay

---

### Post by gewone on 2012-02-20
> **Khayyam said:**
> utmp (which "w" and "uptime" query) isn't very reliable, and can become corrupted. The following should clear the log

```
sudo tee /var/run/utmp </dev/null
```HTH ... khay

**Oh my gosh.**

I was just about to give up. Your trick there was amazing.
Now it seems "reset", it shows correct no. of users logged on.
[B]
Big thanks Khayyam. You are amazing![/B]

---

### Post by Khayyam on 2012-02-20
Your welcome ...

There is a reason, or particular combination of factors, that can cause this, but I can't for the life of me remember what exactly. If it comes to me I'll be sure and let you know, 'til then /dev/null is your BFF.

best ... khay

---

