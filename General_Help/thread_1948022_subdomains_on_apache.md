---
title: "subdomains on apache"
date: 2012-03-27
forum: General Help
---

### Post by yawnmoth on 2012-03-27
I SSH into my Ubuntu machine and edit /etc/apache2/apache2.conf to add the following:

```
<VirtualHost *:80>
  ServerName subdomain.domain.com:80
  Redirect 301 / https://www.google.com/</VirtualHost>
```
I then do sudo apachectl restart and...  nothing.

The DNS server hasn't been updated but my hosts file has been:

```
x.x.x.x  subdomain.domain.com
```

---

