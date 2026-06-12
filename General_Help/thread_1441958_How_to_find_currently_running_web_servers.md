---
title: "How to find currently running web servers?"
date: 2010-03-29
forum: General Help
---

### Post by thanuja on 2010-03-29
Hi,

I installed lamp in kubuntu 8.1. When i started the server, mysql started but for apache and FTP, it says that someother servers are already running.[didnt mention any name..]

How do i stop them and setup apache as the default localserver.??

Thank You

---

### Post by gmargo on 2010-03-29
To find a process from the port it has opened, you can use **lsof**.  Apache wants port 80 and ftp wants port 21.  So try these to discover who's using those ports:

```

sudo lsof -i :80

sudo lsof -i :21

```On my system, I get:
```

$ sudo lsof -i :80
COMMAND   PID     USER   FD   TYPE  DEVICE SIZE NODE NAME
apache2 20156     root    4u  IPv4 3874623       TCP *:www (LISTEN)
apache2 20160 www-data    4u  IPv4 3874623       TCP *:www (LISTEN)
apache2 20161 www-data    4u  IPv4 3874623       TCP *:www (LISTEN)
apache2 20162 www-data    4u  IPv4 3874623       TCP *:www (LISTEN)
apache2 20163 www-data    4u  IPv4 3874623       TCP *:www (LISTEN)

$ sudo lsof -i :21
COMMAND   PID USER   FD   TYPE DEVICE SIZE NODE NAME
inetd   10931 root    9u  IPv4  20058       TCP *:ftp (LISTEN)

```In my case **apache2** is using port 80, and I expect you'll see this too (it's a different copy of apache2 from your lamp stuff.)  And the ftp port is used by **ftpd**, which is invoked by the inetd daemon.

---

### Post by thanuja on 2010-03-30
Hi again,

In my case i think i have tomcat server running since i installed java and netbeans. Can u tell me how to stop tomcat server??

Thanks

---

### Post by falconindy on 2010-03-30
To show all services, use `netstat -planut`.

---

