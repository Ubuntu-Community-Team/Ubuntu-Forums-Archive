---
title: "Installing Nginx"
date: 2011-09-11
forum: General Help
---

### Post by lakshmen on 2011-09-11
I am facing problem installing nginx in ubuntu. Most of the websites are asking to install it together with PHP. But i just want to install nginx alone. Is there any good websites that i can follow?

---

### Post by Lars Noodén on 2011-09-11
nginx should work out of the box after you used the package manager to install it.  What kind of things do you plan to use it for that would warrant extra info?

---

### Post by lakshmen on 2011-09-11
i am going to use it for cloud computing. I intend to do high availabilty or failover management and need nginx to be installed in my computer.. And facing problems in installing it...

---

### Post by Lars Noodén on 2011-09-11
So you want to use nginx as a load balancer?

---

### Post by lakshmen on 2011-09-11
in the package manager, i installed nginx but how do i run it to know it is working... not sure abt it..

---

### Post by lakshmen on 2011-09-11
that is run... Load balancing and failover management. I need to install heartbeat as well...

---

### Post by lakshmen on 2011-09-11
when i type, sudo apt-get install nginx, i get this msg,

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

what shld i do?

---

### Post by coldraven on 2011-09-11
Any use?
[http://www.howtoforge.com/installing-nginx-with-php5-and-php-fpm-and-mysql-support-on-ubuntu-11.04](http://www.howtoforge.com/installing-nginx-with-php5-and-php-fpm-and-mysql-support-on-ubuntu-11.04)

Surely you can skip the PHP part of the process?

---

