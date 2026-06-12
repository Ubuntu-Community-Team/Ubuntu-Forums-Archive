---
title: "web server?"
date: 2009-06-26
forum: General Help
---

### Post by ELFMAN69 on 2009-06-26
Ok, so now my Ubuntu 9.04 is installed and now I want to use it as a web server.
is there a list of apps I will need to do this?

I want to publish my own web sites on my server.

---

### Post by Celauran on 2009-06-26
```
sudo aptitude install apache2 php5 mysql-server
```

Should give you everything you need.

---

### Post by mcduck on 2009-06-26
the correct way to do this would be:
```

sudo tasksel install lamp-server
```

(or, in Synaptic Package Manager, Edit->Mark Packages by Task->LAMP Server).

You may also want to install phpmyadmin to get a graphical interface for MySQL.

---

### Post by Celauran on 2009-06-26
I'm not sure how it's more "correct" but every time I have tried that, tasksel just hangs part way through and I end up having to finish the job with aptitude anyways. I learned to cut out the middleman.

---

### Post by ELFMAN69 on 2009-06-26
thanks guys! looks like I may already have everything needed.
I did a lamp install so I guess it's just a matter of checking.

---

### Post by cybergalvez on 2009-06-26
> **Celauran said:**
> ```
sudo aptitude install apache2 php5 mysql-server
```

Should give you everything you need.

note, installing apache and php this way will install the apache-mpm-prefork, the non threaded version which is needed to use mod_php.  If you want to use the threaded apache apache2-mpm-worker then you have to install php-cli and mod_fastcgi and set up apache to use fastcig to interact with php rather then mod_php.

---

### Post by credobyte on 2009-06-26
Install Apache, PHP, MySQL and phpMyAdmin :
```
sudo apt-get install apache2 php5 libapache2-mod-php5 mysql-server phpmyadmin
```
Open Apache configuration file :
```
sudo gedit /etc/apache2/apache2.conf
```
Add the following line : 
```
Include /etc/phpmyadmin/apache.conf
```
Restart your web server : 
```
sudo /etc/init.d/apache2 restart
```

---

### Post by bodhi.zazen on 2009-06-26
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by maheshasolkar on 2009-06-26
Not being an Apache expert, I've found 'rapache' very useful when managing the apache server.

```
  sudo aptitude install rapache
```

More info at:

  [https://launchpad.net/rapache](https://launchpad.net/rapache)

---

