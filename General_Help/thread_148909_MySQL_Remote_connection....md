---
title: "MySQL Remote connection..."
date: 2006-03-22
forum: General Help
---

### Post by Master Jedi on 2006-03-22
I can connect to and query MySQL if I connect to 127.0.0.1 or localhost, but I want other computers on the network to be able to connect to the database and it doesn't seem to work.

From the MySQL administrator on the MySQL server I can not connect to 192.168.1.100 (which is the server's IP address), but I can connect to localhost. How do I set it up to run on 192.168.1.100 instead of 127.0.0.1?

---

### Post by saaz on 2006-03-29
First, you need to edit /etc/mysql/my.cnf and comment out the "bind-address" line so it looks like this:

#bind-address              = 127.0.0.1

This will allow connections from hosts other than 'localhost' including the server's regular IP.

---

