---
title: "Apache won't pick up port 8080"
date: 2010-01-15
forum: General Help
---

### Post by Zanahade on 2010-01-15
I am trying to get Apache to pick up on port 8080 because my isp blocks incoming on port 80. For some reason Apache is not connecting to it. In the ports.conf file I added:
```
Listen 80
Listen 8080
```
and ran
```
sudo /etc/init.d/apache2 restart
```
at terminal. Apache restarted without error. In fire fox I entered
```
http://localhost:8080/
```
and firefox returned:
> Not Found

The requested URL / was not found on this server.
Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.5 with Suhosin-Patch Server at localhost Port 8080

Ok I am at a loss but I am still very much a noob so any help in resolving this would be epic.

---

### Post by Zanahade on 2010-01-16
Also, I do get a proper connection when not specifying a port. I understand that is default 80. How do I get apache to respond to port 8080? Am I missing something?

---

### Post by pirateghost on 2010-01-16
do you actually have a named virtualhost listening on port 8080?

```
NameVirtualHost *:8080
<VirtualHost *:8080>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>
</VirtualHost>

```by default this file is located:
/etc/apache2/sites-available/default

---

### Post by Zanahade on 2010-01-16
I don't remember having to do that back in 8.04 but you are right, that did it! Thanks for the help! Cheers!

---

