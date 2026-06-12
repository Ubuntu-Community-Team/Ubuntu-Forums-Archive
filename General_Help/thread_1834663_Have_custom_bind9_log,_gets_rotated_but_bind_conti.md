---
title: "Have custom bind9 log, gets rotated but bind continues to log to old log"
date: 2011-08-27
forum: General Help
---

### Post by MechaMechanism on 2011-08-27
I have a custom log for bind9 called  bind9-query.log located in /var/log.  Bind9 also writes to the regular  logs as well, like daemon, syslog etc.  I created a logrotate config in  /etc/logrotate.d/ that rotates the bind9-query.log log and it works but  bind9 continues to write to first log now called bind9-query.log.1.  How do I set this up so that the log is rotated and bind9 writes to  the new log.  I know it's possible because bind9 by default writes to  daemon and syslog with no problem.

 My logrotate.d config.

 /var/log/bind9-query.log {
       daily
       rotate 5
       delaycompress
       compress
       notifempty
       missingok
}


Will these options work.
 postrotate
      /etc/init.d/bind9 reload > /dev/null
    endscript


 I took this from elsewhere on the Internet.  What is the postrotate  thing and what does it do and is it necessary (man page not very clear).  Finally is the reload  command right, I thought you used service instead of init.d these days, I  want to use the correct command.  Also what is the end script thing.   Also the /dev/null/ thing, what is it's purpose.

---

### Post by galvatron408 on 2011-08-27
I hope I can help you understand this...

when logrotate rotates a log file, it renames the log file to something.log.1 like how you described it. 

this action of course, does not affect the process that already has a file handle on the log file. 

So, the postrotate is the part where you tell the process that already has a file handle on it, to let go. When you do this, the process should let go and start writing to the original (something.log).

This guy explains it quite well:
[http://lambie.org/2008/09/03/rotating-logs-with-logrotate/](http://lambie.org/2008/09/03/rotating-logs-with-logrotate/)

---

### Post by MechaMechanism on 2011-08-27
> **galvatron408 said:**
> I hope I can help you understand this...

when logrotate rotates a log file, it renames the log file to something.log.1 like how you described it. 

this action of course, does not affect the process that already has a file handle on the log file. 

So, the postrotate is the part where you tell the process that already has a file handle on it, to let go. When you do this, the process should let go and start writing to the original (something.log).

This guy explains it quite well:
[http://lambie.org/2008/09/03/rotating-logs-with-logrotate/](http://lambie.org/2008/09/03/rotating-logs-with-logrotate/)
Great, thanks a lot.  That guy really explains it well.  Now it works great.

---

