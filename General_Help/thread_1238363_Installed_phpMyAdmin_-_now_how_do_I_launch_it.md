---
title: "Installed phpMyAdmin - now how do I launch it?"
date: 2009-08-12
forum: General Help
---

### Post by traductionbiz on 2009-08-12
Hi,

I just installed phpMyAdmin via Synaptic... How do I actually launch phpMyAdmin in my Web browser?

Thanks in advance for any help. :)

---

### Post by credobyte on 2009-08-12
Haven't tried to install it from Synaptic, but here's what you should do ( in most cases ) ..

Add this line to your Apache configuration file ( [COLOR=Gray]/etc/apache2/apache2.conf[/COLOR] ):
```
Include /etc/phpmyadmin/apache.conf
```

Restart Apache ( [COLOR=Gray]sudo /etc/init.d/apache2 restart[/COLOR] ) and go to [http://localhost/phpmyadmin](http://localhost/phpmyadmin) ;)

---

### Post by traductionbiz on 2009-08-12
credobyte, thanks very much for the help :) Worked perfectly.

---

### Post by teddersion on 2010-06-30
This is exactly what I was looking for as well, thank you!

---

### Post by viczsaurav on 2011-07-12
worked great..Thanks.

Saurav Verma
Reason can Answer Questions But Imagination has to Ask Them..!!!

---

### Post by Goldpin on 2011-07-29
I've done what was suggested in the posts above, but when I try to launch the browser I get:  UNABLE TO CONNECT  Firefox cannot find a connection the server at localhost.  What do I do now???

DISREGARD:  Fixed the problem.  Had put wrong syntax in the .conf file (apache2.conf vs apache.conf

---

