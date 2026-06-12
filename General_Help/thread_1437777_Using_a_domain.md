---
title: "Using a domain"
date: 2010-03-24
forum: General Help
---

### Post by Inf3rnal on 2010-03-24
Okay I have a Ubuntu Server that is correctly set up and has been working for awhile.

It currently has a domain (Registered by GoDaddy) and it is used as the main.

I just bought another domain (From GoDaddy) and I want it to connect to the same server but a different section to host a second site completely separate from the first. 

So this is how I want it to be setup:

Domain1 = /var/www/
Domain2 = /var/www/website2

When I put Domain1 in the url like [www.domain1.com]("http://www.domain1.com") it will connect to /var/www/
When I put Domain2 in the url like [www.domain2.com]("http://www.domain2.com") it will connect to /var/www/website2

Is there a way to do that or a better way to do it?

---

### Post by rudy.b on 2010-03-26
It sounds like you might want to use virtual hosting in Apache.  Virtual hosting allows you to host multiple sites with one server by creating a separate configuration file for each site.

Check out the [Ubuntu server documentation]("https://help.ubuntu.com/community/ApacheMySQLPHP#Virtual%20Hosts") and the [Apache docs]("http://httpd.apache.org/docs/2.2/vhosts/") on virtual hosting for more info.

---

### Post by Ryan Dwyer on 2010-03-26
Basically, you just copy /etc/apache2/sites-available/default (ie. copy default and call it something like domain2), then edit the file and change the DocumentRoot and so on.

Then run a2ensite default2 (or whatever you called it) to enable that host, then /etc/init.d/apache2 reload so Apache starts serving the new host.

---

