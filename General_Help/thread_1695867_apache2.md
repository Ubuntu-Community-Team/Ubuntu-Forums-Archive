---
title: "apache2"
date: 2011-02-26
forum: General Help
---

### Post by dcool76 on 2011-02-26
I notice when my website slows down I look in the memory and I have about 200+ 
 
3772 www-data 184524 kB /usr/sbin/apache2 -k start 
 
What does this mean and sometimes it will go away and the website will load quickly?
 
It also shows on users alot of them to
 
3621 0.1 % 14:15 /usr/sbin/apache2 -k start

---

### Post by dcool76 on 2011-02-26
I changed this in apache2.conf
 
MaxClients 850 instead of 100
 
KeepAliveTimeout 2 instead of 15
 
I host many sites and my biggest is a script site users can host on there site I get alot of requests my server load is at .10 and site seems to load quickly now.
 
I still see alot of 0.0 %  14:48  /usr/sbin/apache2 -k start i would like some info about this thanks.

---

