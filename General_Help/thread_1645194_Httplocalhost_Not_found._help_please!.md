---
title: "Http://localhost/ Not found. help please!"
date: 2010-12-14
forum: General Help
---

### Post by kukker32 on 2010-12-14
Hi there.

I'm currently learning how to program in PHP i have recently installed LAMP server and apache2 and MySQL, i have run a bunch of commands, so i can really remember them all..
the ones i can remember is:

```
apache2 php5-mysql libapache2-mod-php5 mysql-server
sudo tasksel install lamp-server
sudo apt-get install apache2
```

and when i entered [Http://localhost](Http://localhost) in my browser bar i got a screen saying it worked but no content has been added.
I tried put my test file (called index.php) into /var/www/ still not worked renamed it to index.html still not worked.
tried [http://localhost/index.php](http://localhost/index.php) and with index.html wasn't working.

___


i woke up today to try find out what was wrong. 
BUT NOW I CAN'T ENTER [Http://localhost](Http://localhost) nor [http://127.0.0.1](http://127.0.0.1)
I got a "server not found" screen like when you enter an incorrect adress


i tried to restart apache using:
```

sudo /etc/init.d/apache2 restart
```

but get's

>   * Restarting web server apache2                                                apache2: Syntax error on line 233 of /etc/apache2/apache2.conf: Syntax error on line 12 of /etc/apache2/conf.d/index.php: Expected </?php> but saw </div>
                                                                         [fail]


and i'm lost! what do i do, PLEASE HELP ME.

---

### Post by CharlesA on 2010-12-14
index.php shouldn't be in /etc/apache2/conf.d/

---

### Post by kukker32 on 2010-12-14
> **CharlesA said:**
> index.php shouldn't be in /etc/apache2/conf.d/

it's not the index.php i made.
either i don't know what you mean by that post :/

---

### Post by CharlesA on 2010-12-14
Post the output of this please:

```
ls -l /etc/apache2/conf.d/
```

---

### Post by kukker32 on 2010-12-14
> **CharlesA said:**
> Post the output of this please:

```
ls -l /etc/apache2/conf.d/
```

i got this output

> 
totalt 20
-rw-r--r-- 1 root  root   269 2010-11-18 22:16 charset
-rw-r--r-- 1 root  root    21 2010-12-14 14:46 fqdn
-rw-r--r-- 1 allan allan  208 2010-12-13 18:28 index.php
lrwxrwxrwx 1 root  root    45 2010-12-13 21:55 javascript-common.conf -> /etc/javascript-common/javascript-common.conf
-rw-r--r-- 1 root  root  3296 2010-11-18 22:16 localized-error-pages
lrwxrwxrwx 1 root  root    28 2010-12-13 21:56 phpmyadmin.conf -> ../../phpmyadmin/apache.conf
-rw-r--r-- 1 root  root  1481 2010-11-18 22:16 security

---

### Post by CharlesA on 2010-12-14
Yep. Somehow index.php got moved there, and shouldn't be there.

Move it somewhere else for the time being - maybe yer home directory and then try to restart apache2.

---

### Post by kukker32 on 2010-12-14
> **CharlesA said:**
> Yep. Somehow index.php got moved there, and shouldn't be there.

Move it somewhere else for the time being - maybe yer home directory and then try to restart apache2.


WOAH IT WORKED!! thanks for that ;)

now time for the next problem xD one problem rarely comes alone..

do you know where i should put that index.php file i made.. so that i can see it in [http://localhost](http://localhost) ?

as said above i currently have it in var/www/ so i have tried enter [http://localhost/index.php](http://localhost/index.php)

but i only get a white blank screen :(

---

### Post by kukker32 on 2010-12-14
i don't know if it's a mistake i done in the PHP file so i post the code of it here

<html>

  <body>
    <?php
     //this is for testing PHP
     echo "welcome to the first PHP script"
     echo "<br>"
     echo "AND welcome to PHP"
    ?>
  </body>
</html>

---

### Post by CharlesA on 2010-12-14
If you get a blank page, can you view the source and see php code?

EDIT: Try creating a file with this:

```
<html>
<head>
<title>PHP Test</title>
</head>
<body>
<?php phpinfo(); ?>
</body>
</html>
```

Save it as phpinfo.php

Then open it the browser.

See [here]("http://www.htmlgoodies.com/beyond/php/article.php/3472431/PHP-Tutorial-First-Page.htm").

---

### Post by kukker32 on 2010-12-14
> **CharlesA said:**
> If you get a blank page, can you view the source and see php code?

nope also just a blank screen :(

---

### Post by CharlesA on 2010-12-14
Check out my edit ^.

Try that and see if anything is shown.

---

### Post by kukker32 on 2010-12-14
> **CharlesA said:**
> If you get a blank page, can you view the source and see php code?

EDIT: Try creating a file with this:

```
<html>
<head>
<title>PHP Test</title>
</head>
<body>
<?php phpinfo(); ?>
</body>
</html>
```Save it as phpinfo.php

Then open it the browser.

See [here]("http://www.htmlgoodies.com/beyond/php/article.php/3472431/PHP-Tutorial-First-Page.htm").


i got a php page now when i enter [http://localhost/phpinfo.php](http://localhost/phpinfo.php) 

but my index.php (now called test.php) is still not working :/ i think i should try program further on now to see if it's working then..

thanks for saving my day :D

---

### Post by kukker32 on 2010-12-14
ouh and also i see the deafult index.html document is locked to something (according to the little lcok in the corner of the file) in var/www/

is it possible to lock the deafult page to another ?

---

### Post by CharlesA on 2010-12-14
index.html is probably owned by root, which is why it has a lock on it.

You'd have to move it using sudo.

---

### Post by kukker32 on 2010-12-14
> **CharlesA said:**
> index.html is probably owned by root, which is why it has a lock on it.

You'd have to move it using sudo.

i'd run sudo nautilus, moved the file to the desktop, moved the phpinfo.php to var/www/ 
but i still got the default page :( tried rename it to index.php index.html but! it still showing the default screen :(
i want it to show my file or just the phpinfo.php as default.

---

### Post by CharlesA on 2010-12-14
Use gksudo nautilus to start with with root permissions.

Can you post the output of this please:

```
ls -l /var/www
```

---

### Post by kukker32 on 2010-12-14
> totalt 8
-rw-r--r-- 1 root  root  177 2010-12-13 16:19 index.html
-rw-r--r-- 1 allan allan 208 2010-12-13 18:28 index.php


to help make it less frustrating. I will post the codings of each file below.



***index.php***
```

<!doctype html> 
<html> 
    <head> 
     
    </head> 
    <body> 
        <div id="wrap" style="width: 900px; margin: 0px auto;"> 
            <?php 
                echo "<h1>It's works</h1>"; 
                $php_info; 
            ?> 
        </div> 
    </body> 
</html>

```

yea i know it's another index.php but i edited the old index.php so this one works when i enter [http://localhost/index.php](http://localhost/index.php)
[U][I][B]
index.html[/B][/I][/U]

```
<html><body><h1>It works!</h1>
<p>This is the default web page for this server.</p>
<p>The web server software is running but no content has been added, yet.</p>
</body></html>
```

to summerize (spelling) it's the index.php i want as the default page.

---

### Post by CharlesA on 2010-12-14
Remove index.html, and index.php should be the the default page.

---

### Post by kukker32 on 2010-12-14
i have moved the files to thrash bin now,
still get's the default IT WORKS! screen from index.html

---

### Post by CharlesA on 2010-12-14
So index.html isn't there any more?

---

### Post by kukker32 on 2010-12-14
> **CharlesA said:**
> So index.html isn't there any more?

thats correct. but i can get it back if necessary

---

### Post by CharlesA on 2010-12-14
That's strange. Try clearing your browser cache and reloading the page.

---

### Post by kukker32 on 2010-12-14
> **CharlesA said:**
> That's strange. Try clearing your browser cache and reloading the page.

you are indeed a god at this stuff.. :D

/solved.

---

### Post by CharlesA on 2010-12-14
Glad you got it working. :)

Don't forget to mark the thread as solved from thread tools.

---

### Post by kukker32 on 2010-12-14
done :D

---

