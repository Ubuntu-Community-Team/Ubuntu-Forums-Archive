---
title: "Cron-apt not working"
date: 2010-04-28
forum: General Help
---

### Post by IceReaper88 on 2010-04-28
Hello, i just got a big problem with using corn-apt:
i installed ubuntu lucid minimal on a server called "kvm1".
Not i installed the package ubuntu-virt-server and created 3 vm's "vm1-3".
Now i wanted all to send me emails on changes via cron-apt, so i did on every machine a "aptitude install cron-apt". i edited the config file and set the right mail destination. Then i copied the config from that server to the other 3.
So they are exactly identical, (except "kvm1" is a host, and the others guests).
all 3 vm's are working without a problem, but my host machine does not mail me my changes.
When executing "cron-apt -s" i see the right output on every machine.
Secondly i tested "echo foobar | mail my@email" and that worked on all 4 machines...
So the mailing part does work very well. I couldn't find out any way to trace the error on that machine, cron-apt reads the config file without a problem and completes without a problem. but i have no idea how it actualy mails so i couldn't figure out why this machine does not mail the result..?
If some1 could help or has ideas how to trace this problem in cron-apt it would be very nice :)

---

