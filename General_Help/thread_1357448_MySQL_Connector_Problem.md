---
title: "MySQL Connector Problem"
date: 2009-12-17
forum: General Help
---

### Post by zoomiest on 2009-12-17
I just downloaded MySQL Connector/OBDC 5.1, and am trying to establish a connection to a local webserver, with a MySQL database, from Windows.

The error I get is:
Connection Failed: [HY000][ODBC 5.1]Can't connect to MySQL server on '(local IP)' (10061).

The Webserver is running on the same LAN, and is a Ubuntu Server 8.04 box...

Any help would be appreciated!

[You may think its funny posting a MySQL question here, but... people don't answer questions very fast - if at all - on the MySQL Forums]

---

### Post by cj13579 on 2009-12-17
By default MySQL is set to only allow connections from localhost. In order to connect from elsewhere you need to comment out the following line in your /etc/mysql/my.cnf file.


```
bind-address            = 127.0.0.1
```

---

### Post by zoomiest on 2009-12-17
Thanks for your quick reply...

I am trying (remotely - across the city) now, and I get the same error. I will need to try it when I later in the day.

What if I change the IP to my current IP, instead of just commenting it out?

Any other thoughts?

---

### Post by cj13579 on 2009-12-17
You will probably have to set up some port forwarding on your router. Not sure which one's though. Sounds like a job for Google.

I will have look in a while...

---

