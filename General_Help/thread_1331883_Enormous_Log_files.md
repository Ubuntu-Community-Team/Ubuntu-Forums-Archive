---
title: "Enormous Log files"
date: 2009-11-19
forum: General Help
---

### Post by Strongbad on 2009-11-19
I just recently overhauled my system, doing a clean dual boot with windoze 7 and ubuntu 9.10, and for some reason my primary hard drive is being consumed by log files! 

Specifically, syslog, syslog.1 and user.log are taking up 309GB of space altogether.

in user.log, I have the repeating error: ```
pulseaudio[1976]: ratelimit.c: 70 events suppressed
```

in syslog, I have: ```
pulseaudio[1646]: socket-server.c: accept(): Too many open files
```

in syslog.1 I have: ```
wpa_supplicant[1217]: CTRL-EVENT-SCAN-RESULTS
``` and```
avahi-daemon[1076]: Invalid query packet.
``` mixed in there most frequently with some other stuff.

Seems like there's something going on with pulse audio, but I don't really have any idea what it's doing...

Any help would be much appreciated. Thanks!

p.s. I have both a SB X-FI PCI sound card, and an integrated one from Realtech I think.

---

### Post by juancarlospaco on 2009-11-19
how to solve: use bleachbit as root, wipe logs
why: i dont know

---

### Post by TheCowGod on 2009-11-19
I toow would like to know what the deal with the ratelimit.c messages are. I have a TON of them in my log files. Pulse Audio and sound in general seem to work fine, but the gazillions of messages are really annoying. I have spent some real time on google and here trying to figure out what they mean, but no one seems to know.

---

### Post by Strongbad on 2009-11-21
I've thought of wiping the log files, but this seems like it would be a temporary fix, seeing as how it filled my hard drive in a matter of a couple days of uptime, I have a feeling that It'll probably just do it again. I'd like to fix whatever it is that is causing this, not just the symptoms. 

This seems like a fairly common issue from what I've seen googling around, but I haven't found much in the way of a solution yet.

---

### Post by brainyron on 2009-11-27
Anyone found anything helpful with regards to this yet?  I just came back from the Thanksgiving holiday to find my desktop's disk completely full due to these errors...

---

### Post by blueridgedog on 2009-11-27
I would start with a bug report, using the command line tool ubuntu-bug.  Try:

```
ubuntu-bug pulseaudio
```

I have seen lots of thread talking about the issue, but no solution:

[http://ubuntuforums.org/showthread.php?p=8263459](http://ubuntuforums.org/showthread.php?p=8263459)

---

### Post by brainyron on 2009-11-27
I already found a bug report that covers it...the only thing any ubuntu dev has commented on it was "doesn't seem to be a security issue"

---

### Post by Strongbad on 2009-11-27
Apparently, from what I and a friend have dug up, some bad packages have crept into the repos which cause this. They don't seem to be advertising the fact too much (probably cause they screwed up big time), but apparently they'll have fixed them all come mid December. :-/

---

### Post by SlugSlug on 2009-11-27
> **Strongbad said:**
> 

Specifically, syslog, syslog.1 and user.log are taking up 309GB of space altogether.





309 gig thats mental

---

### Post by mbadola on 2009-12-29
got same problem, and my m/c's syslog contains these lines ::
Dec 29 13:07:56 localhost pulseaudio[1634]: socket-server.c: accept(): Too many open files
Dec 29 13:07:56 localhost pulseaudio[1634]: socket-server.c: accept(): Too many open files
----------
found one workaround, (although its a temporary one but will serve you atleast till next boot)
just **kill the process "*usr/bin/pulseaudio --start*"** via pid, search it from ps -eaf|grep pulse command. 
and then check df -h output you will see now disk consumption stopped immediately.
It worked for me hope it will solve yours too.

Thanks

---

### Post by Belizeian on 2010-01-04
Bump Same problem here

---

### Post by Belizeian on 2010-01-20
Does anyone have any ideal.  Sound works great no issue it's just all these ratelimt entries in the log file.  How do you get rid of them.

---

