---
title: "ServerTokens option not found in apache2.conf"
date: 2011-04-14
forum: General Help
---

### Post by warmnscsi on 2011-04-14
Hello, I am trying to set up a lamp server and I would like to change the ServerTokens option from full to prod but when I open /etc/apache2/apache2.conf it's no where to be found. Has the option been moved somewhere else? Thanks.

Same with setting ServerSignature from on to off. I'm starting to wonder if I even have the right conf file.

---

### Post by matadorx on 2011-08-05
I have the same problem... I was following a guide to setup a web server on this page 

[http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/](http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/) 

and cannot seem to find those entries in apache2.conf. maybe its because this guide is for an older version of ubuntu server...

:guitar: If you figure it out, let me know.

---

### Post by Polskiego on 2011-10-31
Hey, I had the same problem. You can just type it into the apache2.conf file.

Type at the very end of apache2.conf:

[B]ServerTokens Prod
ServerSignature Off[/B]


Then restart Apache:

**service apache2 restart **
or
**sudo service apache2 restart**

It worked for me, hope it works for you.

---

### Post by Dangertux on 2011-10-31
You can find the setting in /etc/apache2/conf.d/security

---

