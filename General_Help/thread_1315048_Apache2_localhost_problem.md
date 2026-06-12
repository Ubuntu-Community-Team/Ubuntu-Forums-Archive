---
title: "Apache2 localhost problem"
date: 2009-11-04
forum: General Help
---

### Post by washlee on 2009-11-04
I'm getting frustrated with my apache setup here. Very. 

 I installed and everything seems to work great on the "localhost" but not anywhere else - on the network or elsewhere.  The trouble is that when I go to the IP, whether local or from another network (I have port forwarding set up, correctly, I believe), the url changes from xx.yy.zz:80 to localhost/index.php.  When I manually change  "localhost" back to the ip in the url, then the text from the pages load but not the images, presumably because its looking for them at localhost/images..etc, and  the links suffer the same problem.

  I've tried everything - adding ServerName to apache2.conf and specificying my local ip, network ip, "localhost."  I've tried adding ServerName to /sites-available/default and specifying those also.  I also tried changing ports.conf to Listen xx.yy.zz:80 rather than just 80, because someone else on here seemed to have the exact same problem.  

Heres the begining of my /sites-avilable/default (I think I have it back to its default)

```
NameVirtualHost *
<VirtualHost *>
    ServerAdmin webmaster@localhost

    DocumentRoot /var/www/
```The only thing I've changed in  apache2.confis to add 
```
"ServerName localhost"
```And my ports.conf just says Listen 80

I also just tried the instructions on [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP) to add ServerName localhost to /etc/apache2/conf.d/fqdn

still nothing.  everytime the url changes to localhost/whatever.   please help.  i've been at this for longer than I'm willing to admit.  

Thank you in advance.

---

### Post by washlee on 2009-11-06
Should anyone come across this, it turned out not to be an apache issue at all.  I was trying to set up Project Pier and apparently at some point during the configuration I put "localhost" rather than my ip.  There was a config file (config/config.php) that had a "root_url" line I needed to change.

---

