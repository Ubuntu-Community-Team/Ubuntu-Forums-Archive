---
title: "apache2 wont serve PHP"
date: 2009-12-30
forum: General Help
---

### Post by rugbert on 2009-12-30
I just installed ubuntu 8.04 server as lamp and for whatever reason apache2 wont serve PHP. Ive reinstalled php5 but still no go.

Its been a long while since Ive set up a server and I think that maybe Im forgetting something, did I have to configure apache to serve php? Was there more than just installing php5?

---

### Post by fragos on 2009-12-30
Add the following 3 lines to /etc/apache2/httpd.conf and create file if it dosen't exist.

LoadModule php5_module /usr/lib/apache2/modules/libphp5.so
AddType application/x-httpd-php .php .phtml
AddType application/x-httpd-php-source .phps

By default PHP isn't configured in Apache.

---

### Post by rugbert on 2010-01-01
> **fragos said:**
> Add the following 3 lines to /etc/apache2/httpd.conf and create file if it dosen't exist.

LoadModule php5_module /usr/lib/apache2/modules/libphp5.so
AddType application/x-httpd-php .php .phtml
AddType application/x-httpd-php-source .phps

By default PHP isn't configured in Apache.

That did it. Thanks a bunch!

---

