---
title: "Why am I running a STMP server?"
date: 2011-07-29
forum: General Help
---

### Post by zozza on 2011-07-29
Hello,

I am a client running 10.04.  Not a server of any kind. 

When I run telnet 127.0.0.1 25 the response is:

220 nameofcomputer ESMTP Exim 4.71 Fri, 29 Jul 2011 19:48:19 +0100

Should I be running a SMTP server and if so why is this necessary?

Thanks.

---

### Post by psusi on 2011-07-29
It is handy for local mail, such as those sent by the cron daemon giving you the output of scheduled tasks, or messages from mdadm or smartctl telling you that you have had, or soon will have a drive fail.

---

