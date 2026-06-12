---
title: "phpmyadmin log in"
date: 2010-03-02
forum: General Help
---

### Post by ljupcho on 2010-03-02
Hi,
I am trying to reset my mysql password for root user and log in to phpmyadmin.
Apache2 and php5 work fine on ubuntu 9.10 64bit.
First, I tried with stopping the mysql server and disabling network communication with:
#mysqld --skip-grant-tables --skip-networking &  
(here after i execute this command i am not getting anything, it is like processing ... this might be the problem, i don't know).

Then I go into the mysql and update the root's password and restarting mysql server, but that didn't work.
I read that I might need to use the OLD_PASSWORD function and that gives me 16 bit hash passwords. Can't log in that way eighter.
I read I might need to create a database and create users and passwords and grand all privilagies ... which i did, and I don't know how that database can help, how does phpmyadmin looks into that one for logging in?! 

I also tried windows fashion way by gedit the config.default.php under libratry folder for phpmyadmin and set password for the root user, which by default was blank. Unfortinatelly that didn't work eighter.

I tried reisntalling everything, nothing...
And when i install phpmyadmin i have something like this: /var/www/phpmyadmin/phpmyadmin/phpmyadmin/phpmyadmin/phpmyadmin/phpmyadmin/... like shortcuts, can't get rid of it! How can this happen?

Can anyone please give me some more ideas?
Thanks.

---

### Post by J V on 2010-03-02
Root under ubuntu doesn't have a password, your mysql root may...

You need to edit your config.inc.php

---

### Post by ljupcho on 2010-03-02
can you please be more specific.
i have that file under:
/etc/phpmyadmin/config.inc.php
/var/lib/phpmyadmin/config.inc.php
/usr/share/phpmyadmin/config.inc.php
/usr/share/phpmyadmin/setup/frames/config.inc.php

I guess it's the first one. I tried adding something in this secion
   /* Optional: Advanced phpMyAdmin features */
like 
 $cfg['Servers'][$i]['password'] = 'mypassword';

but, that's not it.

---

### Post by ljupcho on 2010-03-04
I need to edit the 
 /var/lib/phpmyadmin/config.inc.php; file, BUT this file is 0 [B], it is empty. How come?
I reinstalled phpmyadmin, but i am not getting this file.
Is it possible that someone could send me this file, please attach it!
Thanks.

---

