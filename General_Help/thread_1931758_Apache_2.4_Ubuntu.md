---
title: "Apache 2.4 Ubuntu"
date: 2012-02-26
forum: General Help
---

### Post by mauricessid on 2012-02-26
Hello, quick question: I am using Apache 2.2.20 on Ubuntu and would like to upgrade to 2.4. I how read throught the upgrade notes but am unable to complete this successfully. I downloaded the unix source and when using ./configure it says APR not found...Anyone have an idea?

Thanks

---

### Post by hwttdz on 2012-02-26
You can do "sudo apt-get build-dep apache2" and that should get you everything you need to successfully configure and build.  It should be noted however that apache from source is not quite identical to the ubuntu apache (i.e. no init script, no a2enmod), so look into configuring modules that you might need.  I believe there is a "./configure --help" option.  I'm probably going to just look for a ppa or wait for ubuntu to repackage.

---

### Post by mauricessid on 2012-02-26
Thanks mate! I will try and post an update with the results.

---

### Post by 123fix on 2012-04-12
I found a way to install it in ubuntu

check this

[http://www.discusswire.com/apache-2-4-installation-ubuntu/](http://www.discusswire.com/apache-2-4-installation-ubuntu/)

---

### Post by segian on 2012-06-20
hello im new here, but check this one:
[http://www.thegeekstuff.com/2012/05/install-apache-2-on-centos-6/](http://www.thegeekstuff.com/2012/05/install-apache-2-on-centos-6/)

u can download apr and apr-util from that manual

---

