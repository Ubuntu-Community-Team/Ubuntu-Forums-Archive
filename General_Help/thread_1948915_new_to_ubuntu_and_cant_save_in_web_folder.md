---
title: "new to ubuntu and cant save in web folder"
date: 2012-03-29
forum: General Help
---

### Post by mrhankey on 2012-03-29
hi
i decided to install ubuntu as a dual boot on my pc, installation went fine and i can go onto ubuntu no problems.
 
it asked for a password when installing which i entered and when i have ran in the terminal to isntall lighttpd it asked me for password and installed with no errors.
 
the issue i have is i am trying to save a document a phpinfo page in var/www/ however it says i have no permissions for this. this is the same for apache on the machine also.
 
i wanted to play around and get comfortable with web server on ubuntu before i decided to go with it for a vps. however i do not know how i can resolve this?
 
why cant i save onto this location if i am the only user account i setup at install?
 
hope someone can help.
thanks

---

### Post by dragonfly41 on 2012-03-29
I've just gone through this in using Komodo Edit 7.0 to write into DocumentRoot

it's a permissions issue .. you will have take ownership such as this

sudo chown -R yourusername:yourusername /var/www

or

sudo chown -R root:root /var/www

try **[COLOR=black]man chown[/COLOR]** in terminal to see the options

---

### Post by amauk on 2012-03-29
> **dragonfly41 said:**
> I've just gone through this in using Komodo Edit 7.0 to write into DocumentRoot

it's a permissions issue .. you will have take ownership such as this

sudo chown -R yourusername:yourusername /var/www

or

sudo chown -R root:root /var/www try **[COLOR=black]man chown[/COLOR]** in terminal to see the options

Probably cleaner to add your user to the www-data group, but either should do

---

### Post by mrhankey on 2012-03-29
thanks this allowed me to save my phpinfo file to the lcation.
 
however when i launch firefox and type localhost in it says:
 
you dont have permission to access / on this server
 
apache 2.2.20 (ubuntu) server at localhost port 80
 
i installed apache, mysql and php from terminal with commands on ubuntu site.
 
also install lighttpd but cannot get access to the web server.
 
should i only have either apache or lighttpd installed?
 
thanks again

---

### Post by mrhankey on 2012-03-29
i tried following this:
 
[http://www.ubuntugeek.com/lighttpd-webserver-setup-with-php5-and-mysql-support.html](http://www.ubuntugeek.com/lighttpd-webserver-setup-with-php5-and-mysql-support.html)
 
to sort php on lighttpd however it says i cannot modify the php.ini file in this location.
 
/etc/php/cgi
 
i tried chown command to take ownership and it said operation not permitted.
 
finding it all very frustrating to setup a web server on ubuntu so far. hope someone can help.
 
thanks

---

### Post by dragonfly41 on 2012-03-29
I installed (latest) apache, PHP, MySQL manually .. no lighttpd

try reading this ..

[http://maketecheasier.com/install-and-configure-apache-in-ubuntu/2011/03/09](http://maketecheasier.com/install-and-configure-apache-in-ubuntu/2011/03/09)

[http://netbeans.org/kb/docs/php/configure-php-environment-ubuntu.html](http://netbeans.org/kb/docs/php/configure-php-environment-ubuntu.html)

---

### Post by mrhankey on 2012-03-29
thanks i really want to use lighttpd as it is much faster web server aparently.
 
anyway it says apache is already running but not having much joy getting php/mysql going even though they are installed
 
think i might have to use a cpanel then i guess to make it easier as this is a nightmare.
 
thanks

---

### Post by dragonfly41 on 2012-03-29
> /etc/php/cgi

my php5 is in /etc/php**5**/cgi

is that  just a typo error?

---

### Post by mrhankey on 2012-03-29
yeah sorry just a typo.

---

### Post by mrhankey on 2012-03-29
wierd thing is i am getting an error going to localhost.
 
yet if i go to [file:///var/www/index.html](file:///var/www/index.html)
i get the it works page but i am not sure if this is the lighttpd that is showing this as apache is still erroring?
 
i cannot restart service
 
thanks

---

### Post by dragonfly41 on 2012-03-29
Don't forget to clear firefox cache .. Ctrl + F5 forces a browser reload

I've been caught on that one.

---

