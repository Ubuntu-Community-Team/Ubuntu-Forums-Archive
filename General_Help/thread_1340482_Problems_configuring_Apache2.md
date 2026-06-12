---
title: "Problems configuring Apache2"
date: 2009-11-28
forum: General Help
---

### Post by dgohn on 2009-11-28
Ok so I have the apache2 webserver installed and running.  When you hit my domain it goes right to my var/www/ and looks for index. whatever right.  No problems there.  The problem is lying that when you hit mydomain.com/usernamehere or mydomain.com/~usernamehere it isn't going to the /home/usernamehere/public_html/index.whatever

However,  the weird thing is I have another user account on the server for myself other then my administrative account and for some reason that one is the only one that works.  I have looked and looked and can't find a difference between anything else, if you goto mydomain.com/myotherusernamehere it succesfully connects to /home/myotherusernamehere/public_html/index.html but all other users such as mydomain.com/anotherrandomuserontheserver doesn't goto their /home/anotherrandomuserontheserver/public_html/index.html

This is probably way more information or way more complicated then I needed to explain it but I just wanted to make sure I get the jist of the problem acrossed the first time.  Any and all help is greatly appreciated.

Thanks in advance,

Dan

---

### Post by Virtual Liberty on 2009-11-28
```
sudo a2enmod userdir
```httpd.conf
```
<IfModule mod_userdir.c>
    UserDir public_html
</IfModule>
``````
sudo /etc/init.d/apache2 restart
```Am I shooting in the wrong direction ( you know this stuff but it still doesn't work ) ?

---

### Post by dgohn on 2009-11-28
Thanks a ton.

---

