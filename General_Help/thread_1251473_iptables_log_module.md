---
title: "iptables log module"
date: 2009-08-27
forum: General Help
---

### Post by lolboxen on 2009-08-27
Trying to setup logging for iptables. Tried a million things and nothing works. Each iteration of a test ive inscreased the scope of the logging config and what iptable does log. Here is my current config

/etc/syslog.conf

```
*.*    -/var/log/test.log
```

assuming it should catch every type of log even and dump it to test.log. also here is my arguement to iptables

```
iptables -A INPUT -j LOG --log-level info
```

test.log still contains no logging data from iptables... what am I doing wrong here :(

---

### Post by blueridgedog on 2009-08-27
Take a look at this:

[http://www.cyberciti.biz/tips/force-iptables-to-log-messages-to-a-different-log-file.html](http://www.cyberciti.biz/tips/force-iptables-to-log-messages-to-a-different-log-file.html)

Some suggestions (assuming you are actually using sudo iptables ... as the command):

Try getting logging working without a custom log, and then move to a custom log.
Try specifying the messages rather than *.* (after getting it to work in /var/log/messages)
Try passing the --log-level argument

---

### Post by lolboxen on 2009-08-28
Yeah that was one of the many websites I came across. I exhausted google resources and dozens of linux discussion board searches.

I am logging into my box as root so sudo shouldnt be necessary. iptables -l does list the record in the chain so I know its getting cached properly. I also did try specific log levels in syslog.conf.

Ill try your suggestion using /var/log/messages instead of a custom one. Thanks!

---

### Post by lolboxen on 2009-08-28
Tried those suggestions and nothing. I did discover however iptables IS logging the data. I discovered dmesg on the interwebs. Everything is in there its just syslogd is not pushing that information to a file. I'm not 100% on how the relationships between those two programs work but now I know my problem lies there.

---

### Post by lolboxen on 2009-08-28
Found some interesting thread: [http://episteme.arstechnica.com/groupee/forums/a/tpc/f/96509133/m/755007637731](http://episteme.arstechnica.com/groupee/forums/a/tpc/f/96509133/m/755007637731)
That is probably my issue. Hope this thread helps other who ran into this issue.

---

### Post by blueridgedog on 2009-08-28
Is anything getting logged to /var/log/messages?

---

