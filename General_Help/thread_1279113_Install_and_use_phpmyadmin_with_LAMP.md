---
title: "Install and use phpmyadmin with LAMP"
date: 2009-09-30
forum: General Help
---

### Post by pedrosorio on 2009-09-30
I'm using ubuntu 9.04 and I've recently installed lamp (sudo tasksel install lamp-server). After that I've installed phpmyadmin (sudo apt-get install phpmyadmin).

I expected that, after starting the apache server (sudo /usr/sbin/apache2ctl start), I would find the usual phpmyadmin at [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/) however I get a 404 Not Found, error...

If anyone can lead to me to a possible solution, I'd be grateful.

---

### Post by wojox on 2009-09-30
Try:

```
sudo /etc/init.d/apache2 restart
```

---

### Post by pedrosorio on 2009-09-30
It shows the same. I forgot to say, that I have already tried to stop, start, restart, and it stays the same.

---

### Post by wojox on 2009-09-30
Okay then 

```
sudo gedit /etc/apache2/apache2.conf
```

Include the following line at the bottom of the file, save and quit. 

```
Include /etc/phpmyadmin/apache.conf
```

```
sudo /etc/init.d/apache2 restart
```

[https://help.ubuntu.com/community/ApacheMySQLPHP#Phpmyadmin%20and%20mysql-admin](https://help.ubuntu.com/community/ApacheMySQLPHP#Phpmyadmin%20and%20mysql-admin)

---

### Post by pedrosorio on 2009-09-30
Thanks! It did work!

Now I have another problem. It asks me for a username and password. I remember being asked to choose a password during the installation process, but not the username...

EDIT: The username is root, ok. Problem solved =)

---

