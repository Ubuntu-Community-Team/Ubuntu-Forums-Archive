---
title: "Apache port numbers"
date: 2010-06-25
forum: General Help
---

### Post by goodvikings on 2010-06-25
Hi all
 
I have an installation of Apache2 running on a Ubuntu 8.04 server, for both normal web hosting as well as forward proxying. 
 
What I'd like to know is if it is at all possible to have these two purposes use different ports. Ie, I want the web to still use the default port 80, but I want the proxy to be something user defined.
 
Cheers

---

### Post by goodvikings on 2010-06-25
If needed, here is the section in httpd.conf regarding the proxy module
```

<IfModule mod_proxy.c>
ProxyRequests On
<Proxy *>
Order deny,allow
Allow from all
AuthType Basic
AuthName "Password Required Bro"
AuthUserFile /usr/local/apache2/conf/.htpasswd
Require valid-user
</Proxy>
</IfModule>

```

---

### Post by goodvikings on 2010-06-25
bumpin

---

### Post by gmargo on 2010-06-25
You can use "VirtualHost" directives to create multiple independent web sites listening on different ports. (I run an 2 internal-facing sites on ports 80 & 81 and an external-facing site on another port. Each is specified in separate files under sites-avalable/.)

Instead of httpd.conf, those directives belong in files under sites-available/ (and linked to sites-enabled/ with a2ensite.)

---

