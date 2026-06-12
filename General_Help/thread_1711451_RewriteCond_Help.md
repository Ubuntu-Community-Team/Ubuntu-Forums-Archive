---
title: "RewriteCond Help"
date: 2011-03-21
forum: General Help
---

### Post by ondemanddesign on 2011-03-21
I am trying to do a simple redirect, any views to the page myHost.com/events/anythingHere.html should go to events.myHost.com/anythingHere.html. What am I doing wrong?

The following is being inserted into /etc/apache2/apache2.conf inside the VirtualHost for myHost.com
```
RewriteEngine on
RewriteCond %{HTTP_HOST} ^myHost\.com/events/(.*)
RewriteRule ^http://events.myHost.com/$1 [R=permanent,L]
```

---

### Post by kidders on 2011-03-22
Hi there,

The problem is with the use of %{HTTP_HOST} in your RewriteCond directive. The regular expression you're testing for will never match a hostname. In any case, since the rule appears inside the VirtualHost block for myhost.com, testing the value of %{HTTP_HOST} is redundant anyway. You should test the value of %{REQUEST_URI} instead. For example ...```
RewriteCond %{REQUEST_URI} ^/events/(.*)
```

I hope that helps.

---

