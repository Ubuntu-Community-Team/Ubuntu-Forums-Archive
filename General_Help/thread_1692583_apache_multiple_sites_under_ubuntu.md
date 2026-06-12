---
title: "apache multiple sites under ubuntu"
date: 2011-02-21
forum: General Help
---

### Post by supasoaker on 2011-02-21
hi all - I am tyring to configure apache and finding it difficult.........
 
It is my first time with apache so please be gentle :P
 
I have read many walk throughs but still can't get my head around it, I am trying to configure apache 2 so that it recognises an IP address as being x and then loads the index.html from the DocumentRoot that I enter but still can't get it working.........
 
anyone able to offer any help? Much obliged!

---

### Post by supasoaker on 2011-02-23
As far as I am aware all I need to do is edit my httpd.conf file to get everything working........This is what my httpd.conf currently looks like:
 
**NameVirtualHost 10.1.2.3**
 
**<VirtualHost 10.1.2.3>**
**ServerAdmin [EMAIL="contact@xxxx.com"]contact@xxxx.com[/EMAIL]**
**DocumentRoot /home/dan/html**
**ServerName xxxx.com**
**</VirtualHost>**
 
I know for sure that my domain xxxx.com (I have not written it on this forum as I am borrowing it from someone) is not being used. It still is not working! When I restart apache I get this in my terminal:
 
**dan@dan-desktop:~$ sudo /etc/init.d/apache2 restart**
*** Restarting web server apache2 apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName**
**... waiting apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName**
**[ OK ]**
 
Any clues as to what I am missing?

---

