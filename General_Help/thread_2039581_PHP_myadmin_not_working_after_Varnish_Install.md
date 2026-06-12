---
title: "PHP myadmin not working after Varnish Install"
date: 2012-08-09
forum: General Help
---

### Post by iqbalmp on 2012-08-09
:)Hi,
I have installed Varnish accelerator for PHP; ports were changed during the installation.
After the successful installation I can access all sites in my document root. But 'phpmyadmin' does not work..
It automatically redirects to the port:8008 and page left blank.
[http://localhost:8008/phpmyadmin/](http://localhost:8008/phpmyadmin/)

Any help appreciated.

---

### Post by Kalanac on 2012-08-09
If you're running apache, make sure that phpmyadmin is still in the includes in the configuration file.  You could also try uninstalling and re-installing phpmyadmin

---

### Post by iqbalmp on 2012-08-09
Hi Kalanac,

Yes, I am running in Apache; I didn't change anything other than the port in virtual host:
/etc/apache2/sites-available/default
<VirtualHost *:8008>
Also I can see:
/etc/apache2/conf.d/phpmyadmin.conf
which starts:
"Alias /phpmyadmin /usr/share/phpmyadmin ........"

---

### Post by Kalanac on 2012-08-09
Is there a:

```
Include /etc/phpmyadmin/apache.conf
```

line in /etc/apache2/apache2.conf ?

Other than that I can only suggest purging your phpmyadmin package and re-installing it.  That'll clear all the configuration files so that the re-install will start from scratch

```
sudo apt-get purge phpmyadmin
```

This isn't something I've done myself and I'm not very well versed in the behaviour of phpmyadmin so I don't know what might happen as a result of doing this.  Loosing settings is certainly likely.

---

### Post by iqbalmp on 2012-08-09
Kalanac,

I have reinstalled the PhpMyadmin but no success:
When I am trying:
[http://localhost/phpmyadmin/](http://localhost/phpmyadmin/)
It automatically redirects to:
[http://localhost:8008/phpmyadmin/](http://localhost:8008/phpmyadmin/)

In '/etc/apache2/apache2.conf' I can see:
Include conf.d/

---

