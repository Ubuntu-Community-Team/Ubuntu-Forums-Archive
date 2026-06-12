---
title: "PHP LAMP Installation"
date: 2012-03-13
forum: General Help
---

### Post by LinuXofArabiA on 2012-03-13
Hello everyone,

I want to install a complete server-based suite on my local computer for local web development and testing. I want to used PHP for server side scripting. I saw the following command for installing the full LAMP suite:

sudo apt-get install lamp-server^

I was wondering if this the right way to go, or if there is an already available package somewhere.

Thanks in advance for your help.

---

### Post by ubudog on 2012-03-13
That works, or you could do:
```
sudo tasksel install lamp-server
```

---

### Post by fragos on 2012-03-13
That's all you need to install but PHP won't execute until /etc/apache2/httpd.conf has the following three lines in it to enable PHP.

LoadModule php5_module /usr/lib/apache2/modules/libphp5.so
AddType application/x-httpd-php .php .phtml
AddType application/x-httpd-php-source .phps

---

