---
title: "No httpd executable with apache2 install?"
date: 2011-01-25
forum: General Help
---

### Post by bigspoon on 2011-01-25
Hey y'all,
I'm trying to build a C++ library with apache2 support on 10.10. The ./config file wants me to link to the httpd executable but there is none to be found in /usr/sbin. I don't know apache that well on Linux. Is this set up right? Is something wrong?

$ sudo find / -name httpd*
/etc/apache2/httpd.conf
$

---

### Post by bigspoon on 2011-01-26
httpd is an old executable and the new one for apache2 resides here /usr/sbin/apache2

---

