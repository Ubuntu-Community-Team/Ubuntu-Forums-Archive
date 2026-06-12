---
title: "Apache PHP and MySql questions"
date: 2006-05-23
forum: General Help
---

### Post by Stochastic on 2006-05-23
Hey, I've poured over a few howtos and posts on here including server setup things and I'm trying to get the following setup working: a standalone webserver that I'd like to run a couple different pages from, which is currently running Ubuntu Breezy, and a "production server" (I think that's what it's called) that's not open to public access on my laptop that's currently running Ubuntu Dapper.  It looks like I've got everything installed and running but I have no idea as to configuration to make this setup work.

When I go to [http://192.168.0.101](http://192.168.0.101) (my standalone box) I get a listing of files and when I click on apache2-default folder I get the apache setup webpage.  when I click back (to /var/www/) and then click on info.php firefox asks me how to handle the file instead of running it.  The phpmyadmin website comes up (when I go to that folder) but I don't know what username/password to log in with.

When I go to [http://192.168.0.100](http://192.168.0.100) (my laptop) I get the same behaviour except that info.php returns the info on php.

My questions then include 1)how do I get my standalone box to run info.php 2)what's the best way to configure multiple websites on a single standalone 3)how do I log into phpmyadmin 4)how do I configure apache on my laptop to be secure from everyone except the local user?

thanks.

---

### Post by FDupont on 2006-05-23
Go there:

[https://wiki.ubuntu.com/ApacheMySQLPHP]("https://wiki.ubuntu.com/ApacheMySQLPHP")

Cheers!

---

### Post by Stochastic on 2006-05-23
I've already read over that document and still can't get php to work on my standalone server.  I've tried uninstalling everything in the lamp stack and reinstalling it but phpmyadmin returns an error when I 'sudo apt-get remove phpmyadmin' and thus apt-get won't let me uninstall php or mysql because of phpmyadmin dependencies.  Do I need to reinstall ubuntu?

And that document really doesn't answer much of any of my other questions.

---

### Post by adamkane on 2006-05-23
Here are the error-free methods to install. If something doesn't work, it's a PITA to troubleshoot.

Apache2/PHP4/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php4 mysql-client mysql-server phpmyadmin libapache2-mod-php4 libapache2-mod-auth-mysql php4-mysql

``` 
Apache2/PHP5/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php5 mysql-client mysql-server phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

``` 
Apache2/PHP5/MySQL5 (dapper):
```

sudo apt-get install apache2 php5 mysql-client-5.0 mysql-server-5.0 phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

``` 
You create multiple websites by creating folders under /var/www, and having your DNS provider direct various addresses to the folders under your IP. You'll need to check your DNS provider's support pages to learn their procedure for creating multiple web addresses to the same machine. I think you have to port forward with your firewall/router.

---

### Post by Stochastic on 2006-05-23
Well I've got these packages installed fine on the laptop but I can't seem to get php working on my standalone (still the same phpmyadmin dependency issue I stated before).  But still, can anyone answer my questions 1, 3, or 4?

---

### Post by adamkane on 2006-05-23
1:
LAMP is truly difficult to troubleshoot. I try to keep my LAMP installation on a separate server, back up my database and web pages with cron, and re-install the server, whenever LAMP gets hosed.

3:
[http://localhost/phpmyadmin]("http://localhost/phpmyadmin")

4:
You need a firewall/router to limit access. Hardware firewall is best. Software firewall is most effective on a machine that is used specifically as a network firewall.

---

### Post by Isoss on 2006-05-24
Sorry, this was posted by mistake

---

### Post by ifokkema on 2006-05-25
[QUOTE=Stochastic]My questions then include 1)how do I get my standalone box to run info.php 2)what's the best way to configure multiple websites on a single standalone 3)how do I log into phpmyadmin 4)how do I configure apache on my laptop to be secure from everyone except the local user?[/QUOTE]

Hi,

1) Are you sure the mod-php4 is enabled? You need to run
```
sudo a2enmod php4
sudo /etc/init.d/apache2 restart
```
for it to work.

2) You need to be using virtual hosts for that. If you want those websites to be available from within the network, you need to configure your router to point these hostnames to your machine. Then create new virtual hosts. They're configured in /etc/apache2/sites-available/, and you can enable them by running
```
sudo a2ensite <name>

4) The simpliest thing to do is to make sure Aaache listens only to the 127.0.0.1 IP address, then it's not listening for connections from elsewhere and you don't need to worry about a firewall or so. There's a listen directive in the config file:
[CODE]Listen 127.0.0.1:80
```

Hope this helps you along,

Ivo

---

