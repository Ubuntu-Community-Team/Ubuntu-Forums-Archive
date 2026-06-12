---
title: "Using Desktp Install and Using LAMP?"
date: 2006-06-01
forum: General Help
---

### Post by Avicus on 2006-06-01
Can I install the Desktop ISO and apt-get the LAMP software stack for use on this install? Or is that a special package that is available only on the Server ISO?

---

### Post by Ramses de Norre on 2006-06-01
Yes you can ;)

---

### Post by Avicus on 2006-06-01
OK, so whats the package called, or are you gonna make me install and search??? :P

---

### Post by armeck on 2006-06-01
You could also go the other way around.  Install as a server first, then 'apt-get ubuntu-desktop'

---

### Post by ubnoobie on 2006-06-01
[QUOTE=Avicus]Can I install the Desktop ISO and apt-get the LAMP software stack for use on this install? Or is that a special package that is available only on the Server ISO?[/QUOTE]
the "lamp" packages the server iso installs are:

apache2 php5-mysql libapache2-mod-php5 mysql-server

(source: ubuntu-server-lamp.seed off the server iso)

those (and their depends) are installed on top of the ubuntu-standard meta package and the server-optimised kernel (if supported by the hardware).

so

sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server

on an existing dapper install will net the same 'lamp' setup as the server iso.

note you may also want to get libapache2-mod-perl2 and a few other things, depending upon your specific requirements.

---

### Post by az on 2006-06-01
[QUOTE=ubnoobie]the "lamp" packages the server iso installs are:

apache2 php5-mysql libapache2-mod-php5 mysql-server

(source: ubuntu-server-lamp.seed off the server iso)

those (and their depends) are installed on top of the ubuntu-standard meta package and the server-optimised kernel (if supported by the hardware).
[/QUOTE]

Just to be clear, you don't need to use a special server kernel to run the LAMP stack.  You can use an old 486 box and run the default dektop 386 kernel)

---

### Post by Avicus on 2006-06-01
Yes, that's all fine I guess... but the LAMP setup on the server description page  also says no need for extra configuration and working in minutes rather than an hour to set up all LAMP components... I'm looking to save time!

Is there an automated package install rather than installing all LAMP components separately?

Or is the LAMP thing (I havent even tried the server disc yet) just a script that runs all that during the server install? And therefore might be unavailable to a desktop installed user?

---

### Post by jonibo on 2006-06-01
Just run:

sudo apt-get apache2 php5-mysql libapache2-mod-php5 mysql-server

Then open firefox and check [http://localhost](http://localhost)
Put you web page under /var/www/

---

### Post by chrisfay on 2006-07-16
I have written a basic yet hopefully helpful tutorial on how to setup the LAMP configuration for Linux beginners. It includes resources on setting up Apache2, MySQl5,PhP5 and FTP as well as WebMin in an informal semi how-to. [Check it out]("http://www.cjfay.com/lamp.html").

---

### Post by ayoli on 2006-07-16
if i renember well, i've just apt-get phpmyadmin which depends on apache, php and mysql.
regards.

---

