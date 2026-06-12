---
title: "MySQL Remote Connection"
date: 2012-03-29
forum: General Help
---

### Post by scambro on 2012-03-29
Not sure exactly where to post this question because it's a combination of MySQL, networking and a lack of knowledge on my part.  I just setup synchronization between two MySQL servers on different IPs.  I got synchronization working, but I had to create user access in MySQL with the specific IP address of my slave server (not the host name).

My MySQL database is setup with the following privileges for this user:

```

Host: slave.master-MySQL-server-addresscom
user: replicate

```

Here's what happens when I try to connect to my master server from being SSH'd to the slave:

```

mysql -u replicate -h www.master-MySQL-server-address.com --port=3306 -p

ERROR 1045 (28000): Access denied for user 'replicate'@'xxx.xxx.xxx.xxx' (using password: YES)

```

The IP address that shows is the IP of the slave server (slave.master-MySQL-server-address.com).  When I added the host of the IP address to my master MySQL user table, I can then connect remotely and the synch works.  The IP address on my slave server changes on occassion, so I'd rather have the A DNS record referenced.

Any ideas?  Thanks!

---

