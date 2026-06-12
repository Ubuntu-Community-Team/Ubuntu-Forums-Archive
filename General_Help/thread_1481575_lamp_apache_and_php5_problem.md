---
title: "lamp apache and php5 problem"
date: 2010-05-12
forum: General Help
---

### Post by jbaltrus on 2010-05-12
I can't seem php5 work with apache2. I am getting the text openning instead of php. I think this is infamous problem, found many suggestions adding AddType application/x-httpd-php .php, did that in /etc/apache2/apache2.conf and /etc/apache2/httpd.confwith no luck, it's still opening text

any suggestion would be helpful

Jonas

---

### Post by Ryan Dwyer on 2010-05-12
Do you mean you see the <?php tag(s) in the HTML source through the browser? I'm sure you're aware you need to browse via localhost and not open the file directly.

Post the output of the following:

sudo apt-get install libapache2-mod-php5
sudo /etc/init.d/apache2 restart
ls /etc/apache2/mods-enabled/php*

Check if it works after that.

---

### Post by bodhi.zazen on 2010-05-12
```
sudo a2enmod php5
sudo service apache restart
```

Then clear you (browser) cache and reload the (php) page.

---

### Post by jbaltrus on 2010-05-12
> **Ryan Dwyer said:**
> Do you mean you see the <?php tag(s) in the HTML source through the browser? I'm sure you're aware you need to browse via localhost and not open the file directly.

Post the output of the following:

sudo apt-get install libapache2-mod-php5
sudo /etc/init.d/apache2 restart
ls /etc/apache2/mods-enabled/php*

Check if it works after that.

I don't get it, I tried all of them, it just wouldn;t work:

cmrfocf@schedule-cmrf:~$ sudo apt-get install libapache2-mod-php5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libapache2-mod-php5 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 62 not upgraded.
cmrfocf@schedule-cmrf:~$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
 ... waiting apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
   ...done.
cmrfocf@schedule-cmrf:~$ ls /etc/apache2/mods-enabled/php*
/etc/apache2/mods-enabled/php5.conf  /etc/apache2/mods-enabled/php5.load
cmrfocf@schedule-cmrf:~$

---

### Post by jbaltrus on 2010-05-12
> **bodhi.zazen said:**
> ```
sudo a2enmod php5
sudo service apache restart
```Then clear you (browser) cache and reload the (php) page.

same here, does not help:

cmrfocf@schedule-cmrf:~$ sudo a2enmod php5
[sudo] password for cmrfocf: 
Sorry, try again.
[sudo] password for cmrfocf: 
Module php5 already enabled
cmrfocf@schedule-cmrf:~$ sudo a2enmod php5
Module php5 already enabled
cmrfocf@schedule-cmrf:~$ sudo service apache restart
apache: unrecognized service
cmrfocf@schedule-cmrf:~$ sudo service apache2 restart
 * Restarting web server apache2
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
 ... waiting apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
   ...done.

---

### Post by bodhi.zazen on 2010-05-12
Did you clear your cache ?

---

### Post by jbaltrus on 2010-05-12
> **bodhi.zazen said:**
> Did you clear your cache ?

I did. One of these things I did made it work. I have absolutely no idea which or why

thanks though

---

