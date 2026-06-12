---
title: "sarg, File not found"
date: 2010-08-09
forum: General Help
---

### Post by ishokenmei on 2010-08-09
Hi, all.
I installed squid3 and it' running.  When I tried to run sarg, it said it can't find the access log file.  Following is the output of sarg -x
SARG: Init
SARG: Loading configuration from: /usr/local/etc/sarg.conf
SARG: Parameters:
SARG:
SARG:              Hostname or IP address (-a) = 
SARG:                       Useragent log (-b) = 
SARG:                        Exclude file (-c) = 
SARG:                     Date from-until (-d) = 
SARG:       Email address to send reports (-e) = 
SARG:                         Config file (-f) = /usr/local/etc/sarg.conf
SARG:                         Date format (-g) = USA (mm/dd/yyyy)
SARG:                           IP report (-i) = No
SARG:                           Input log (-l) = /var/log/squid3/access.log
SARG:                  Resolve IP Address (-n) = No
SARG:                          Output dir (-o) = /home/ish/squid_report/
SARG:    Use Ip Address instead of userid (-p) = No
SARG:                       Accessed site (-s) = 
SARG:                                Time (-t) = 
SARG:                                User (-u) = 
SARG:                       Temporary dir (-w) = /tmp
SARG:                      Debug messages (-x) = Yes
SARG:                    Process messages (-z) = No
SARG:
SARG: sarg version: 2.2.7.1 Feb-12-2010
SARG: File not found: /var/log/squid3/access.log

The file access.log is in /var/log/squid3.  Thanks in advance.

---

### Post by dino99 on 2010-08-09
[http://www.udiniqgeek.com/sarg_ubuntu.html](http://www.udiniqgeek.com/sarg_ubuntu.html)

---

### Post by ishokenmei on 2010-08-09
> **dino99 said:**
> [http://www.udiniqgeek.com/sarg_ubuntu.html](http://www.udiniqgeek.com/sarg_ubuntu.html)
Thanks for the reply.  But the problem is sarg is unable to find the access.log when I ran it.  It showed the error as in the first post.  And I am pretty sure the path and file name of the log are correct.  Any help?

---

### Post by WorMzy on 2010-08-09
What are the permissions of that file?

```
ls -l /var/log/squid3/access.log
```

It could be that the program needs to be run as root. I've never used it before, so I don't know for sure.

---

### Post by ishokenmei on 2010-08-09
You're right. It's a permission problem.  When I ran it as root, it worked.
Thank you WorMzy.

---

