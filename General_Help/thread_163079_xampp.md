---
title: "xampp"
date: 2006-04-20
forum: General Help
---

### Post by tension9000 on 2006-04-20
hi to all, 
i would try to create a website with phpmyadmin wordpress and so on .........
first i tried to install apache2-mysql-php4,5-phpmyadmin.... but no way to start phpmyadmin, i have always window with the chance to save or open a phtml (?) file......... i have removed all software i installed and tried with xampp 1.5.1 but it's the same! same window when i want to start phpmyadmin.
anybody could help me?

---

### Post by dermotti on 2006-04-20
Been awhile since i used apache, cuz lighttpd owns it. (howto in my signature, but you need dapper :-))

But anyways, did you add:

[B]AddType application/x-httpd-phtml .phtml
AddType application/x-httpd-php .php[/B]

to your httpd.conf?

---

### Post by tension9000 on 2006-04-20
now i'll read your howto

> But anyways, did you add:

AddType application/x-httpd-phtml .phtml
AddType application/x-httpd-php .php

to your httpd.conf?

i did it on first installation from synaptic.... no way
if i do with xampp i obtain errors when starting it.......

---

### Post by dermotti on 2006-04-20
One thing to note, i had this issue before and even tho i had fixed it, i kept getting the "download file" box. The browser caches that, so you may never know you when you fix it. 

Easiest way around it is to create a file called php.php and put <? phpinfo(); ?> in it.

everytime you make a change trying ot fix the issue, rename the php.php somehting like php1.php.

This way you always get a fresh copy and not a cached copy.

---

