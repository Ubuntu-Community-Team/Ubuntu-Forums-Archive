---
title: "Php isnt working"
date: 2009-09-15
forum: General Help
---

### Post by xZachtmx on 2009-09-15
Ok i have the php5 package installed but when i try to use php in html it dosent do anything and .php files dont do anything in my browser but it only tells me i can download the code.  Is there something ineed to do to enable php?

---

### Post by durand on 2009-09-15
How did you install php? Try this: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by durand on 2009-09-15
And this: [https://help.ubuntu.com/9.04/serverguide/C/web-servers.html](https://help.ubuntu.com/9.04/serverguide/C/web-servers.html)

---

### Post by slakkie on 2009-09-15
```

sudo a2enmod php

```

---

### Post by xZachtmx on 2009-09-15
Yes i did all that and apache is working... but when i goto my test php file on the server (which has the code < ?php phpinfo(); ?> ) it only displays the code  and dosent do anything else... its just a blank page that says




< ?php phpinfo(); ?> 




Apache lists php5 as one of its modules... so i wonder whats happening :confused:

---

### Post by durand on 2009-09-15
Hmm, not sure. If you're desperate to get it working, you can use xampp as a temporary solution: xampp.org It's basically a ready to go lampp install.

---

### Post by uylug on 2009-09-15
Yes. Had the same issue. I never really got it to work by installing packages manually. Are you using Ubuntu with graphical interface? Then open Synaptic:

```
sudo synaptic
```

Then go into Edit -> Select Packages By Task -> LAMP Server.

---

### Post by conehead77 on 2009-09-15
try to remove the space:
```

<?php phpinfo(); ?> 

```

instead of < ?php...

---

### Post by uylug on 2009-09-15
> **conehead77 said:**
> try to remove the space:
```

<?php phpinfo(); ?> 

```

instead of < ?php...

That won't do it. The problem is Apache not 'interpreting' php files, which is why he gets a download window where he can see the php code he wrote.

If Apache was processing .php files, he would have got a php syntax error, which is not what he is getting right now.

---

### Post by durand on 2009-09-15
> **conehead77 said:**
> try to remove the space:
```

<?php phpinfo(); ?> 

```

instead of < ?php...

I kinda thought that was intentional. I don't know much about php but would the space actually matter?

---

### Post by uylug on 2009-09-15
> **durand said:**
> I kinda thought that was intentional. I don't know much about php but would the space actually matter?

I guess it won't work with that space. I am currently writing a page with php but I always write it like <?php.

However, the problem he is having right now is Apache not using the PHP module to process php files.

---

### Post by conehead77 on 2009-09-15
> **uylug said:**
> That won't do it. The problem is Apache not 'interpreting' php files, which is why he gets a download window where he can see the php code he wrote.

If Apache was processing .php files, he would have got a php syntax error, which is not what he is getting right now.

I just tried it on my localhost and it is just like the OP described. With space: just the text. Without space: phpinfo output. I say it is worth a try.

---

### Post by uylug on 2009-09-15
> **conehead77 said:**
> I just tried it on my localhost and it is just like the OP described. With space: just the text. Without space: phpinfo output. I say it is worth a try.

It sure is worth a try!

I just re read my post and it seemed quite rude! Sorry about that!

---

### Post by conehead77 on 2009-09-15
> **uylug said:**
> 
I just re read my post and it seemed quite rude! Sorry about that!

No worries, i dont inteprete short and concise answers as rude :)

---

### Post by fragos on 2009-09-16
For PHP to work you'll need to enable it in httpd.conf. I placed the following 3 lines in mine:

LoadModule php5_module /usr/lib/apache2/modules/libphp5.so
AddType application/x-httpd-php .php .phtml
AddType application/x-httpd-php-source .phps

---

### Post by fragos on 2009-09-16
For PHP to work you'll need to enable it in httpd.conf. I placed the following 3 lines in mine:

LoadModule php5_module /usr/lib/apache2/modules/libphp5.so
AddType application/x-httpd-php .php .phtml
AddType application/x-httpd-php-source .phps

---

### Post by freackout on 2009-09-16
> **durand said:**
> And this: [https://help.ubuntu.com/9.04/serverguide/C/web-servers.html](https://help.ubuntu.com/9.04/serverguide/C/web-servers.html)

slampp2.0.1 is out its nice and easy. running virtual for time being may help.

---

