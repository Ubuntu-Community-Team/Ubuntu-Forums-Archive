---
title: "Open Window on Specified Display"
date: 2009-09-18
forum: General Help
---

### Post by UndeniablyRexer on 2009-09-18
Forgive me if this has been answered previously, but I could not find anything through my searches.

I have a mythbuntu running on my television with no peripherals attached, except the television.  Is there a way to ssh into it from my laptop and open mythtv remotely?

---

### Post by UndeniablyRexer on 2009-09-18
For anyone who cares, I did this by checking the display (using the 'w' command and using the value under 'FROM'), and exporting it as the DISPLAY variable.

```

user@server:~$ w
 17:07:15 up  1:06,  4 users,  load average: 0.22, 0.27, 0.21
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
user     tty7       :0                     16:01    8:06m  2:08   0.02s /bin/sh /etc/xd
user     pts/0    :0.0                  16:02    1:05m  0.11s  0.11s bash
user     pts/1    fe80::21e:c2ff:f 16:04    0.00s  0.14s  0.00s w
user     pts/2    fe80::21e:c2ff:f 17:02    3:55   0.14s  0.14s -bash
user@server:~$ DISPLAY=:0
user@server:~$ export DISPLAY
user@server:~$ firefox &

```

---

