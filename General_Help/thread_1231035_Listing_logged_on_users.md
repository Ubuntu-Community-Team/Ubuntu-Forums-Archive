---
title: "Listing logged on users"
date: 2009-08-04
forum: General Help
---

### Post by kg84 on 2009-08-04
Curious to see how long the machine here had been on for, I ran uptime and got the normal output. It shows 2 users logged on.

I ran the users command to see who/ what else was logged on here. I expected to see myself ('m') and root. But what i saw was m, twice.

Why is this?

:)

Screenie attached.

---

### Post by nikhilk on 2009-08-04
> **kg84 said:**
> Curious to see how long the machine here had been on for, I ran uptime and got the normal output. It shows 2 users logged on.

I ran the users command to see who/ what else was logged on here. I expected to see myself ('m') and root. But what i saw was m, twice.

Why is this?

Better information can be obtained about the logged on users from the output of command
```
w
```
Yes, it is the single letter 'w'

---

### Post by kpkeerthi on 2009-08-04
Run the **who -H** command and you'll find out why :)

---

### Post by kg84 on 2009-08-04
```
m@m-laptop:~$ w
 17:59:58 up 1 day, 30 min,  2 users,  load average: 0.07, 0.12, 0.14
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
m        tty7     :0               Mon17   14:30m  1:11m  0.65s x-session-manag
m        pts/0    :0.0             17:59    0.00s  0.10s  0.01s w
m@m-laptop:~$ who -H
NAME     LINE         TIME             COMMENT
m        tty7         2009-08-03 17:30 (:0)
m        pts/0        2009-08-04 17:59 (:0.0)
m@m-laptop:~$ 

```Thanks for the replies guys, but straight up, I am still none the wiser :)

'Mon17' is especially perplexing.

---

### Post by slakkie on 2009-08-04
man w
man who
man last

---

### Post by kg84 on 2009-08-04
> **slakkie said:**
> man w
man who
man last

Thanks slakkie - I can now see why I was seeing the two 'm' login's.

I also understand what the IDLE: 14:30m is telling me.

Still not certain what Mon17 is saying.

---

### Post by lisati on 2009-08-04
> **kg84 said:**
> Still not certain what Mon17 is saying.
My first guess is it's an abbreviation for "Monday, 17th". There is one this month but it hasn't happened yet:confused: There was one in November 2008 but that doesn't tally with the idle time :confused:

---

### Post by kg84 on 2009-08-04
> **lisati said:**
> My first guess is it's an abbreviation for "Monday, 17th". There is one this month but it hasn't happened yet:confused: There was one in November 2008 but that doesn't tally with the idle time :confused:

This was the first thing that sprang to my mind as well.

Time to put a second thinking cap on :)

---

### Post by Spiritof76 on 2009-11-21
> **kg84 said:**
> ```
m@m-laptop:~$ w
 17:59:58 up 1 day, 30 min,  2 users,  load average: 0.07, 0.12, 0.14
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
m        tty7     :0               Mon17   14:30m  1:11m  0.65s x-session-manag
m        pts/0    :0.0             17:59    0.00s  0.10s  0.01s w
m@m-laptop:~$ who -H
NAME     LINE         TIME             COMMENT
m        tty7         2009-08-03 17:30 (:0)
m        pts/0        2009-08-04 17:59 (:0.0)
m@m-laptop:~$ 

```Thanks for the replies guys, but straight up, I am still none the wiser :)

'Mon17' is especially perplexing.
I think it might the hour of the login. 17:00

---

