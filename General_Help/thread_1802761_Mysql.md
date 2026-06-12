---
title: "Mysql"
date: 2011-07-12
forum: General Help
---

### Post by Linux_buddy on 2011-07-12
Hi, 
   I have installed Mysql 5.1 client server version in my computer.
 But I dont know how to start it. When i tried with something like below :


```
name@name:~$ mysql hi
Warning: World-writable config file '/etc/mysql/my.cnf' is ignored
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2).

```

 What is the problem here and what should i do here to start the program.
  Thnx

---

### Post by WorMzy on 2011-07-12
[https://help.ubuntu.com/10.04/serverguide/C/mysql.html](https://help.ubuntu.com/10.04/serverguide/C/mysql.html)

---

### Post by lykwydchykyn on 2011-07-12
For security reasons, some services will not start if their configuration files are world-writable or don't meet certain permissions requirements.

These are typically set correctly by default, so it looks as thought the permissions were changed on the configuration file and need to be changed back.

Try this:
```

sudo chmod 644 /etc/mysql/*
sudo service mysql restart

```

Then try again.  If that doesn't fix it, post the output of:
```

sudo tail /var/log/mysql.err

```

---

### Post by Linux_buddy on 2011-07-12
Hi, 
  Thaks for the quick reply.
  The code:
```
  sudo chmod 644 /etc/mysql/*
```
 worked. It saying mysql start/running.
   Now, how can i access the mysql window where i can write the commands?
 
   thnx

---

### Post by ~!geek!~ on 2011-07-12
If you want to work on command line, you may do:
> mysql -u <username> -p <password>
It will give you mysql prompt. Now you may start working.

If you want a gui for mysql, you should install phpmyadmin using command:
> sudo apt-get install phpmyadmin
If you have any webserver installed, you may run [http://localhost/phpmyadmin](http://localhost/phpmyadmin) to start this phpmyadmin window: Now after entering username and  password you may start using mysql prompt.

---

### Post by Linux_buddy on 2011-07-12
Hi, 
     when i write the code mentioned above i get the below given error:
```
[CODE]  ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

```[/CODE]
  what now?

 
  Thnx

---

