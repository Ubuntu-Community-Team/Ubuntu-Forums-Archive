---
title: "mysql"
date: 2010-06-28
forum: General Help
---

### Post by mrgrahamethomson on 2010-06-28
I thought I would set up one of my home computers as a little server to test my website before I uploaded it. All went well when installing XAMPP but when I tried to set the root password I got this error:
The program 'mysql' can be found in the following packages:
*list of packages*

So I installed using this command:
apt-get install mysql-client-5.1

All seemed to go well but when I tried to set the root password I got this error:
can't connect to local mysql server through socket '/var/run/mysqld/mysqld.sock' (2)

Anyone know how to solve this? Would be grateful if you could help. Thanks.

---

### Post by Javich on 2010-06-28
First, make sure you have the server installed.

```
sudo apt-get install mysql-server
```

If it's not, install it, you already have the client, and the error you're seeing is because the server is not started.

Try

```
sudo /etc/init.d/mysql start
```

to start the server, then try again

---

