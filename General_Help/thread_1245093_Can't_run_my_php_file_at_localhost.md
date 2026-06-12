---
title: "Can't run my php file at localhost"
date: 2009-08-20
forum: General Help
---

### Post by masoud23 on 2009-08-20
Hello!

I run ubuntu 9.04 and apach2 which workes: when i open: [http://localhost/](http://localhost/) i get: "It works!" but when I create a new map at /var/www and put my php file in it "test1.php", it just refuse to open it a box apaeres which ask what program i will open it with!! shouldn't that be clear!! i think ubuntu works well in general but geting localhost to work it is like hell!
code in my tets1.php file:
<html>
<body>
<h1>Test</h1>

<?php
echo ”php_test”;
?>
</body>
</html>

---

### Post by mcduck on 2009-08-20
Are you sure you have PHP correctly installed? How did you install LAMP?

---

### Post by credobyte on 2009-08-20
Try:
```
sudo apt-get install php5 libapache2-mod-php5 && sudo /etc/init.d/apache2 restart

```

---

### Post by kellemes on 2009-08-20
As asked by mcduck.. Have you setup PHP?
[Instructions here..]("https://help.ubuntu.com/community/ApacheMySQLPHP")

---

### Post by masoud23 on 2009-08-20
> **mcduck said:**
> Are you sure you have PHP correctly installed? How did you install LAMP?
how do i install php?

---

### Post by mcduck on 2009-08-20
The best way to install the complete LAMP is to use the following command:
```
sudo tasksel install lamp-server
```
This will download, install and configure Apache2, PHP5 and MySQL for you.

If you don't want mySQL support, the command credobyte posted should do the trick since you already have Apache installed.

---

### Post by masoud23 on 2009-08-20
> **credobyte said:**
> Try:
```
sudo apt-get install php5 libapache2-mod-php5 && sudo /etc/init.d/apache2 restart

```

I installed PHP5 but it still till don works i get this message:
```
masoud@masoud-desktop:~$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
 ... waiting apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName

```

---

### Post by Copernicus1234 on 2009-08-20
Dony worry about that message, its just for information. Apache still works as it should.

You cant tell from restarting apache if php is working however, so you need to try to run a test .php page.

---

### Post by credobyte on 2009-08-20
> **masoud23 said:**
> I installed PHP5 but it still till don works i get this message:
```
masoud@masoud-desktop:~$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
 ... waiting apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName

```

Thats just a warning. To remove it, open /etc/apache2/apache2.conf and add the following line:
```
ServerName webserver
```

---

### Post by masoud23 on 2009-08-20
I can run some php file but for som other it askes what program they should be opened with!!

---

### Post by credobyte on 2009-08-20
> **masoud23 said:**
> I can run some php file but for som other it askes what program they should be opened with!!

Show us the output of:
```
cd /var/www && ls -al
```

---

