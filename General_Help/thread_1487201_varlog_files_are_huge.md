---
title: "/var/log/ files are huge"
date: 2010-05-18
forum: General Help
---

### Post by gldearman on 2010-05-18
Hi, all,

Out of the blue today, Ubuntu warned me that I was critically short of space on my / drive.

I examined the problem, and determined that a huge amount of disk space is being taken up by files in /var/log/

The following files:
```
/var/log/messages.1
/var/log/kern.log.1
/var/log/daemon.log.1
/var/log/messages
/var/log/kern.log
/var/log/daemon.log
/var/log/syslog

```
are all over 1 GB in size.  The largest is 18 GB.  Together, they total 48.3 GB.

I restarted the system, forcing a fsck.  No luck.

Where do I go from here? What are these files?  Why are they so huge? Can I get rid of them?

Thanks!

---

### Post by gldearman on 2010-05-18
Having looked through these files, it appears to be all error messages from my printer.  These error messages look like they are being generated at the rate of hundreds per second.

---

### Post by jobix on 2010-05-18
You need to figure out what is going on with the printer, but in the meantime, you can use "logrotate" to keep your log files down to a smaller size. 18GB log files is a waste of space.

> man logrotate


The config file is typically in /etc/logrotate.conf.

Also, you could turn off the "cupsd" daemon which might help prevent the printer from writing all that stuff. You can use "sudo rm" if you want to get rid of those log files and that should be okay.

---

### Post by gldearman on 2010-05-18
OK, I forced log rotation with
```
logrotate -f /etc/logrotate.conf
```

Then I went in and manually deleted the gargantuan files, now that they were archived.  Don't know what that was about, and I still have no idea why my printer was spitting out error messages.  But I have the immediate problem solved.  Thanks!

---

