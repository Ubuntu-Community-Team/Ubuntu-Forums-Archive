---
title: "MYSQL : Remote Connection"
date: 2010-02-07
forum: General Help
---

### Post by hwgmis on 2010-02-07
Hi Guys,

I am having a problem with mysql server which installed on my Ubuntu 8.04 Hardy.

I cannot do any remote connection to the server from windows client as i need to run some program which using mysql.

I have commenting the bind-address option in the my.cnf and grant all privileges to user root and my windows ip address, but still connect to server, if i use the navicat to connect to server, it give an error saying "Can't connect to mysql server on '192.168.103.2' where **192.168.103.2** is my mysql server ip address.

I have open port 3306 on server to accept the incoming connection, but when i do the telnet 3306 from my windows box, it say couldn't connect to the server.

Any ideas guys where i should go to set the mysql server? 

Thanks

---

### Post by gmargo on 2010-02-08
You could try setting the bind-address to 0.0.0.0.  I saw some mention of that while googling around.

---

### Post by The Cog on 2010-02-08
Why doesn't telnet connect - it normally gives a reason - timeout or connection refused are the common reasons.

What is the output of **netstat -lnt** ? We want to see where mysql is listening on.

Do you have a firewall that might be blocking the connection?

---

