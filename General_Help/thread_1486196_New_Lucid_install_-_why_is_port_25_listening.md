---
title: "New Lucid install - why is port 25 listening?"
date: 2010-05-17
forum: General Help
---

### Post by yeleek on 2010-05-17
Hi,

Just wiped 9.10 and installed Lucid.

Carry out a netstat -nl and get this

Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN 

Why is port 25 (SMTP) open?

Thx

---

### Post by jerome1232 on 2010-05-17
It's not, it's listening on the loopback address, meaning your machine is only accepting connections to port 25 from itself.

I'm assuming it's for system mail. I Just checked on my system, the process that is listening is called master, if you look at the man page for master you'll find it's a daemon for postfix for delivering mail, the system mail in this case.

---

### Post by anomie on 2010-05-17
[QUOTE=yeleek]```
Proto Recv-Q Send-Q Local Address           Foreign 
..     
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN
``` 

Why is port 25 (SMTP) open?[/QUOTE]

Note that it's listening only on localhost; it's accessible only by you. One reason to run an MTA (and glom onto localhost in this way) is to ensure that you receive system email.

---

### Post by yeleek on 2010-05-18
Fair enough - Thank you.

---

