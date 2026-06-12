---
title: "Multiple SSL Certificates on Apache"
date: 2011-08-16
forum: General Help
---

### Post by ondemanddesign on 2011-08-16
How can I allow multiple SSL certificates in the default-ssl file in /etc/apache2/sites-available/ folder? I tried

```
NameVirtualHost *:443
```

And


```
<VirtualHost *:443>
```

but I get the error

```
[error] VirtualHost *:443 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
```

Is it possible to have 2 or more SSL certificates with a single IP?

---

### Post by Habitual on 2011-08-16
don't think so, usually it's 
1 domain = 1 IP = 1 Certificate.

Self-signed certs ***may*** be the exception.

---

### Post by ondemanddesign on 2011-08-16
What about if I use a non-standard SSL port instead of 443 for the second certificate?

Edit: To the nay sayers, this is completely doable. Below is the basic structure I used.

```

<IfModule mod_ssl.c>
NameVirtualHost ww.xx.yy.zz:443
SSLStrictSNIVHostCheck on
<VirtualHost ww.xx.yy.zz:443>
   ServerAdmin admin@examplesite.com
   ServerName examplesite.com
   DocumentRoot /var/www/site

</VirtualHost>
<VirtualHost ww.xx.yy.zz:443>
   ServerAdmin admin@examplesite2.com
   ServerName examplesite2.com
   DocumentRoot /var/www/site2
</VirtualHost>

```

---

