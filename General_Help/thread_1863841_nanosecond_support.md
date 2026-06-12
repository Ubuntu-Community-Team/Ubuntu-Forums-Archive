---
title: "nanosecond support"
date: 2011-10-18
forum: General Help
---

### Post by docdailey on 2011-10-18
what do i need to get time resolution less than a us (nanoseconds)

I have looked around and i cant figure it out.

i need much better precision for NTP.  here is what i am referring to:

willy@shuttle:~$ tail /var/log/ntpstats/loopstats
55852 43301.494 0.000016000 -29.477 0.000019928 0.004705 4
55852 43317.494 0.000016000 -29.473 0.000018644 0.004613 4
55852 43333.494 0.000015000 -29.469 0.000017443 0.004505 4
55852 43349.494 0.000015000 -29.466 0.000016320 0.004408 4
55852 43365.494 0.000014000 -29.462 0.000015273 0.004297 4
55852 43381.494 0.000014000 -29.459 0.000014291 0.004197 4
55852 43397.494 0.000015000 -29.455 0.000013376 0.004134 4
55852 43413.494 0.000013000 -29.452 0.000012534 0.004027 4
55852 43429.494 0.000013000 -29.449 0.000011729 0.003930 4
55852 43445.494 0.000012000 -29.446 0.000010983 0.003819 4 

I need the last 3 digits in the offset column  0.000012000

My bet is I need a different kernel or need to enable nanosecond in the kernel.. or my hardware doesnt support?

willy@shuttle:~$ ntpd --version 
ntpd - NTP daemon program - Ver. 4.2.6p2
willy@shuttle:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
willy@shuttle:~$ echo `uname -r` 
3.0.0-12-generic

Intel P4

---

### Post by hwttdz on 2011-10-18
I'm confused, 
1) a us ('mu' s) is a microsecond
2) you're worried your clock is off by some tiny fraction of a second?  Honestly, it seems unlikely to me that you're going to get better time resolution than that due to network overhead.

---

### Post by docdailey on 2011-10-18
> **hwttdz said:**
> I'm confused, 
1) a us ('mu' s) is a microsecond
2) you're worried your clock is off by some tiny fraction of a second?  Honestly, it seems unlikely to me that you're going to get better time resolution than that due to network overhead.

True, for distributing the time... but for timestamping and for proof of concept I want better if it is available in ubuntu.  I may have to go to freebsd.  I am fairly certain ubuntu can do better.  

For a little background.. i am feeding it with a GPSDO (jackson labs fury)that should get me in close to 100 ns (maybe lower if the OS and hardware can handle it) using the PPS from the oscillator (smoothed from raw gps pps).  My next step if ubuntu can't do nanoseconds is to move to freebsd.  Then I have a soekris net4501 that I will replace the stock crystal with a disciplined oscillator.  The journey is the goal.  I want to compare Ubuntu time performance to FreeBSD on stock hardware then on modified hardware.

I am creating a precision appliance for time keeping.

---

