---
title: "How do you Limit Log File sizes? Log files are taking up entire harddrive"
date: 2010-03-15
forum: General Help
---

### Post by SundeepG on 2010-03-15
Hey, I just recently reinstalled (clean) Ubuntu 9.10 Karmic Koala last week. In that time, over 40GB of log files were created until the FileSystem was full. I then received a low disk space message and ran disk usage analyzer to find out that almost all of the 44GB I had free were taken up by the /var/log directory. I then preceded to delete the 5 largest files which freed up over 40 GB of space. Basically I believe that I have two problems: 1.) The log files are logging too much information (40 GB in one week). 2.) I need a way to automatically limit the size of the log files. I have tried searching online for this solution and briefly came across logrotate but I don't believe that this will completely solve my problem as it only compresses and backs up older logs. I need something that will remove old log entries altogether. If logrotate is capable of this can someone please walk me through the process? I do not remember all five log files that were in question but they did include: messages, syslog, and daemon.log. I believe kern.log may have been involved too.

---

### Post by ram2500 on 2010-03-15
**40 GB** of log files in a week??? How is that possible? Perhaps a large file or multiple folders were mistakenly put there, or you have a security breach (doubtful, though about the latter). 

I would search for a script that would automatically clear /var/log on shutdown. In the meantime, it is safe to delete the log files in /var/log. 

This simple shell script isn't automatic, but it should work:

[B]#!/bin/bash

rm -r /var/log | mkdir /var/log[/B]

Run it perhaps every couple weeks or so. 

Someone who is a network/system administrator should have a look into better solutions as they can probably post a complete, automatic shell script on here that does it automatically. Or, you can try looking for one on the Internet (but post it on the forums to make sure you're not getting anything malicious, if you don't understand shell scripts.)

This will delete the log folder as well, but no worries, it will be replaced as a new, empty /var/log folder will be made via mkdir /var/log.

---

### Post by dcstar on 2010-03-15
> **SundeepG said:**
> Hey, I just recently reinstalled (clean) Ubuntu 9.10 Karmic Koala last week. In that time, over 40GB of log files were created until the FileSystem was full. I then received a low disk space message and ran disk usage analyzer to find out that almost all of the 44GB I had free were taken up by the /var/log directory. I then preceded to delete the 5 largest files which freed up over 40 GB of space. Basically I believe that I have two problems: 1.) The log files are logging too much information (40 GB in one week). 2.) I need a way to automatically limit the size of the log files. I have tried searching online for this solution and briefly came across logrotate but I don't believe that this will completely solve my problem as it only compresses and backs up older logs. I need something that will remove old log entries altogether. If logrotate is capable of this can someone please walk me through the process? I do not remember all five log files that were in question but they did include: messages, syslog, and daemon.log. I believe kern.log may have been involved too.

Your problem is that something is generating log messages to try and get someone's attention, and if it continues to be ignored it will continue to generate log messages.

Look at the log files and find out what the problem actually is.

---

