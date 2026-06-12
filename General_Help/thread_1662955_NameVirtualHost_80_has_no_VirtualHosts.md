---
title: "NameVirtualHost *:80 has no VirtualHosts"
date: 2011-01-08
forum: General Help
---

### Post by micha8l on 2011-01-08
Hey,

As title suggests, I'm trying to set up a virtual host using the Apache web server, however I can't get the thing to work. The only steps I've taken to set up the virtual host was to create a text file named "square.localhost" and saved it in /etc/apache2/site-available and /etc/apache2/sites-enabled.

square.localhost.txt
> 
NameVirtualHost *:80
<VirtualHost *:80>
    DocumentRoot "/var/www/square/public"
    ServerName square.localhost
</VirtualHost>


I then restarted apache:

```

sudo apachectl restart

```

And it gives the error:
 > apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Sun Jan 09 04:26:11 2011] [warn] NameVirtualHost *:80 has no VirtualHosts


I try [http://square.localhost/](http://square.localhost/) in my browser but it doesn't work.

---

