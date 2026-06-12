---
title: "Need Apache and MySQL GUI tools"
date: 2012-07-31
forum: General Help
---

### Post by tripower on 2012-07-31
I need to run Apache w/Mono and MySQL with Ubuntu 12.04 desktop to start off with then moving over to Ubuntu server. Are there any GUI tools for Apache and is there a way for me to get Rapache even though they are no longer supporting this? Also I need a good GUI management tool for MySQL as well. Thanks.

---

### Post by beboylips on 2012-08-01
Phpmyadmin is an excellent browser php-based MySQL GUI. Also Mysql Workbench.

---

### Post by tripower on 2012-08-01
> **beboylips said:**
> Phpmyadmin is an excellent browser php-based MySQL GUI. Also Mysql Workbench.

What about Apache?

---

### Post by greenpeace on 2012-08-01
The mysql workbench GUI tool in the repositories works well and allows server administration as well.  


Also, phpmyadmin is simple, browser based, and available in the repositories

---

### Post by LinuxBill on 2012-08-01
> **tripower said:**
> I need to run Apache w/Mono and MySQL with Ubuntu 12.04 desktop to start off with then moving over to Ubuntu server. Are there any GUI tools for Apache and is there a way for me to get Rapache even though they are no longer supporting this? Also I need a good GUI management tool for MySQL as well. Thanks.

Webmin is a great tool also for all your admin needs. its a web server that runs on your machine and lets you admin all your services from the web GUI. Think its runs on port 10000 or something an you just go to your localhost:10000 in browser. Quite powerful.

I used it on alot of my openBSD machines in previous job. 

Linky to the site is [here]("http://www.webmin.com/") if you want a look.

Bill

---

### Post by tripower on 2012-08-01
> **greenpeace said:**
> The mysql workbench GUI tool in the repositories works well and allows server administration as well.  


Also, phpmyadmin is simple, browser based, and available in the repositories

Ok, thanks what about an admin tool for APACHE?

---

### Post by lisati on 2012-08-01
> **tripower said:**
> Ok, thanks what about an admin tool for APACHE?

Webmin can be used to administer apache.

---

### Post by anuvnu387 on 2012-08-01
I second Webmin as well. It can manage Apache, MySQL and a lot more. It is one of the first things I install on my ubuntu server.

---

