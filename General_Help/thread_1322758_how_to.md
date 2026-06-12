---
title: "how to"
date: 2009-11-11
forum: General Help
---

### Post by malikge on 2009-11-11
Hello...  I am using Ubuntu 8.10, I have just installed Apache and PHP and want to know how to run it??? 
For installation I have followed the following steps in the site below.
              [http://www.howtoforge.com/ubuntu_lamp_for_newbies](http://www.howtoforge.com/ubuntu_lamp_for_newbies)
Now I want to know how run .php files in it...
Thanks.

---

### Post by dvlchd3 on 2009-11-11
Place a php file in the /var/www directory.  Whatever you name the file is what you put in your web browser after [http://localhost/](http://localhost/).

I.e. - filename = test.php
Browse to this file with:
[http://localhost/test.php](http://localhost/test.php)

You can also add directories in the /var/www directory to add directory structure.

I.e. a file located in /var/www/testing/test.php can be browsed to as:
[http://localhost/testing/test.php](http://localhost/testing/test.php)

Does that all make sense?

---

### Post by malikge on 2009-11-11
> **dvlchd3 said:**
> Place a php file in the /var/www directory.  Whatever you name the file is what you put in your web browser after [http://localhost/](http://localhost/).

I.e. - filename = test.php
Browse to this file with:
[http://localhost/test.php](http://localhost/test.php)

You can also add directories in the /var/www directory to add directory structure.

I.e. a file located in /var/www/testing/test.php can be browsed to as:
[http://localhost/testing/test.php](http://localhost/testing/test.php)

Does that all make sense?

Thanks for quick replay...
When I place php file in /var/www directory it gives error message:

    There was an error moving the file into /var/www
     Error moving file: Permission denied.

I have to switch to root and place the file through Terminal in /var/www and then run it through browser.. it then works fine. Do I alway have to move php file in /var/www like this way?

---

### Post by konqueror7 on 2009-11-11
> **malikge said:**
> Thanks for quick replay...
When I place php file in /var/www directory it gives error message:

    There was an error moving the file into /var/www
     Error moving file: Permission denied.

I have to switch to root and place the file through Terminal in /var/www and then run it through browser.. it then works fine. Do I alway have to move php file in /var/www like this way?

change the permission of the folder by,

```
sudo chown -R <username>:<groupname> /var/www
```

say for example,

```
sudo chown -R konqueror7:konqueror7 /var/www
```

the group option is optional...

---

### Post by malikge on 2009-11-11
Thanks man. it helped...

---

