---
title: "Help remove/uninstall LAMP server in Ubuntu 10.10"
date: 2010-11-03
forum: General Help
---

### Post by jhaykage on 2010-11-03
Hi everyone,

I'm using Ubuntu 10.10 and I just recently installed a LAMP server for some minor local web development. 

Used the sudo tasksel command to install lamp but I can't get phpmyadmin to work nor can I access mysql.

I need help in removing the LAMP and starting all over again.

How do I go about this?

Many thanks!

---

### Post by TheAnachron on 2010-11-03
LAMPP just compies the files into /opt/lampp mostly.
Just delete that folder.

Btw, you need to run LAMPP as root to be able to use it.
(& you need to start it yourself: sudo /opt/lampp/lampp start)

---

### Post by rvause on 2010-11-03
For PhpMyAdmin admin you will need to add the Apache configuration:

```
sudo cp /etc/phpmyadmin/apache.conf /etc/apache2/sites-available/phpmyadmin.conf
sudo a2ensite phpmyadmin
sudo /etc/init.d/apache2 restart
```

If you want to remove the LAMP server you can do so with tasksel by running `sudo tasksel` again and unchecking "LAMP SERVER" and hitting "OK". The LAMP server should then be removed.

Then follow the relevant web server guidesif you want to set up manually: [https://help.ubuntu.com/10.10/serverguide/C/web-servers.html]("https://help.ubuntu.com/10.10/serverguide/C/web-servers.html")

---

### Post by jhaykage on 2010-11-03
That's weird. The /etc/opt folder is empty.

---

### Post by jhaykage on 2010-11-03
> **rvause said:**
> For PhpMyAdmin admin you will need to add the Apache configuration:

```
sudo cp /etc/phpmyadmin/apache.conf /etc/apache2/sites-available/phpmyadmin.conf
sudo a2ensite phpmyadmin
sudo /etc/init.d/apache2 restart
```

If you want to remove the LAMP server you can do so with tasksel by running `sudo tasksel` again and unchecking "LAMP SERVER" and hitting "OK". The LAMP server should then be removed.


I tried to run 'sudo tasksel' and unchecked "LAMP SERVER" but I get this error message after hitting OK:

tasksel: aptitude failed (100)

---

### Post by rvause on 2010-11-03
You can try and make sure all configuration is ok with 

```
sudo dpkg --configure -a
```

and packages are up to date with

```
sudo apt-get update
```

then return to tasksel and try removing LAMP again

---

### Post by jhaykage on 2010-11-03
> **rvause said:**
> You can try and make sure all configuration is ok with 

```
sudo dpkg --configure -a
```

and packages are up to date with

```
sudo apt-get update
```

then return to tasksel and try removing LAMP again

No luck, after updating the packages, I tried to run tasksel to remove LAMP but the same 'aptitude failed (100)' message appeared.

Did some troubleshooting and found a way to know what command tasksel was trying to run and found this:


> debconf-apt-progress -- apt-get -q -y install mysql-client-core-5.1- apache2- php5-cli- libaprutil1-dbd-sqlite3- apache2.2-common- libapache2-mod-php5- apache2-utils- libaprutil1- libaprutil1-ldap- php5-common- php5-mysql- libdbi-perl- mysql-server-core-5.1- mysql-server- libplrpc-perl- apache2.2-bin- libdbd-mysql-perl- libhtml-template-perl- libnet-daemon-perl- libapr1- mysql-server-5.1- libmysqlclient16- apache2-mpm-prefork- mysql-client-5.1- mysql-common-

I read somewhere that running the command above manually via Terminal solved the problem. Tried it but it didn't work.

---

### Post by rvause on 2010-11-03
Have you tried to install the above packages manually using apt-get without using tasksel? Perhaps this would be better for you?

---

### Post by jhaykage on 2010-11-03
> **rvause said:**
> Have you tried to install the above packages manually using apt-get without using tasksel? Perhaps this would be better for you?

I did, but the LAMP stack had problems while running so I wanted to do a clean install again.

---

