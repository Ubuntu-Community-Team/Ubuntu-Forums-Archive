---
title: "wamp / lamp required"
date: 2010-03-25
forum: General Help
---

### Post by gurmeet on 2010-03-25
hi
where i can download and install WAMP / LAMP or ( may b something else to run PHP ) on UBUNTU... 


plz give me link where i can download ?
 and i also need step by step to configure it on ubuntu environment...



1 more thing i want to know that can i store a PHP site on UBUNTU( web server) and access it from clients (XP), how may i configure this environment?

---

### Post by captain_171 on 2010-03-25
You dont have to go anywhere do download anything.
You need to go into the terminal and type
```

sudo apt-get install apache2
sudo apt-get install php5 libapache2-mod-php5
sudo apt-get install mysql-server
sudo apt-get install libapache2-mod-auth-mysql php5-mysql phpmyadmin

```This will get you everything you need

---

### Post by mcduck on 2010-03-25
or even easier way to install the whole LAMP stack:

```
sudo tasksel install lamp-server
```

..and here's some configuration instructions to get you started: [https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP")

---

### Post by owenll on 2010-03-25
> **gurmeet said:**
> hi
where i can download and install WAMP / LAMP or ( may b something else to run PHP ) on UBUNTU... 

Xampp is really easy to install if you want a testing sever:

[http://www.apachefriends.org/en/xampp-linux.html](http://www.apachefriends.org/en/xampp-linux.html)

---

### Post by ruslyislam on 2011-07-05
tasksel : command not found

> **mcduck said:**
> or even easier way to install the whole LAMP stack:

```
sudo tasksel install lamp-server
```..and here's some configuration instructions to get you started: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by Dangertux on 2011-07-05
> **ruslyislam said:**
> tasksel : command not found

Try 
```

sudo apt-get install lamp-server

```

---

