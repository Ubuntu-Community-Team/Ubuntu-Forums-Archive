---
title: "How to list machine startup times"
date: 2012-10-09
forum: General Help
---

### Post by arcull on 2012-10-09
Hi everyone.

I wonder if it is possible to list let's say last 10 machine startup dates and times somehow, are there any kernel logs which I could parse to get them? Any advice welcome, thanks

---

### Post by pbrane on 2012-10-09
the command 'last' will show you a list of last logged in users,
'last reboot' will give you the reboot times. I only get two when I use that command. I don't know how to get any more than that.

'last' parses the file /var/log/wtmp. There may be a /var/log/wtmp.1 which should be older and may have more boot times in it.

Aha! 'last reboot -f /var/log/wtmp.1' on my system shows the last 15 reboots!

---

### Post by Frogs Hair on 2012-10-09
Here are some related "last" commands. [http://www.cyberciti.biz/tips/linux-shutdown-command-and-logfile.html](http://www.cyberciti.biz/tips/linux-shutdown-command-and-logfile.html)

---

### Post by arcull on 2012-10-10
it is not actually about startups, but is still very useful, thanks :)

---

### Post by dcstar on 2012-10-10
> **arcull said:**
> Hi everyone.

I wonder if it is possible to list let's say last 10 machine startup dates and times somehow, are there any kernel logs which I could parse to get them? Any advice welcome, thanks

The syslog file has all startups in the file before it is rotated, or you can simply write a script that runs in /etc/rc.local to record each startup.

---

