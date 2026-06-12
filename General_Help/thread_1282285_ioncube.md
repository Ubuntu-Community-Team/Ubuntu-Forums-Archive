---
title: "ioncube?"
date: 2009-10-04
forum: General Help
---

### Post by Bluesplayer on 2009-10-04
Hi

I can't seem to get ioncube to run.  I have the following:

ioncube directory located in usr/local/bin

php.ini file with:

zend_extension = /usr/local/bin/ioncube/ioncube_loader_ioncube_loader_lin_5.2.so

Still won't run though?  What am I missing?

Regards

PS: latest version of ubuntu server

---

### Post by devon34 on 2009-10-04
Is php.ini located in the admin folder?
[[IMG]http://cash1000.org/images/th.png[/IMG]](http://groups.adobe.com/people/838ec6d24c/profile)

---

### Post by Bluesplayer on 2009-10-04
php.ini is in:

/etc/php5/apache2

---

### Post by Bluesplayer on 2009-10-04
I think I need Zend Optimizer for this to work?

---

### Post by Bluesplayer on 2009-10-04
Sorted this now.  Read the apache log and there was a Elfclass32 error.  I must have downloaded the wrong ioncube file.  Redid it and it is now working :).

---

