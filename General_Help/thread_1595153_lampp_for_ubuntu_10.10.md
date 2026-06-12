---
title: "lampp for ubuntu 10.10"
date: 2010-10-12
forum: General Help
---

### Post by tech7 on 2010-10-12
It's been a short while since I had to put lampp on ubuntu 10.04.  But, nevertheless I got it running eventually.
I cannot seem to get it working on 10.10.
Has anybody had experience with this yet?
If so, what did you do to get it to work?
Also, what differences does anybody know of that is preventing it from installing on 10.10 via the routes it would install on 10.04?

---

### Post by crichard on 2010-10-13
Could you please explain more about what is going on? How did you install it? Did you get any errors while installing? 
Looking for more details. I'm running LAMP-server without any issues in 10.04 & 10.10.. 

[Installing LAMP ( Linux &#8211; Apache &#8211; MySQL &#8211; PHP ) Server in Ubuntu.]("http://surferzworld.com/2010/10/installing-lamp-linux-apache-mysql-php-server-ubuntu/")

Please go through the above tutorial & let me know the outcome. 

**sudo tasksel install lamp-server** command will not work under 10.10., but it works under 10.04.

Instead of you can use the following command,
 **sudo apt-get install lamp-server^**

---

### Post by tech7 on 2010-10-13
great.  phpmyadmin is up and running now.  As far as the tutorial is concerned, i get 404'd when I use the url's they provide, like [http://localhost/~user/phpinfo.php]("http://localhost/%7Euser/phpinfo.php") and [http://localhost/~user/]("http://localhost/%7Euser/").  I can access phpmyadmin by standard url [http://localhost/phpmyadmin](http://localhost/phpmyadmin) (which is a great improvement)

[http://localhost/phpinfo.php](http://localhost/phpinfo.php) also gets 404'd in addition to the tutorial's urls that are mentioned above.

I have to split and head to work.  I'm going to throw some files in /var/www and maybe some other places to see where lampp has set the server to.  

I'll report back as soon as I have had a chance to do that.

Thanks a lot for your help, crichard!!

---

### Post by crichard on 2010-10-13
[http://localhost/~user/](http://localhost/~user/) This one is an example to you. You've to use your username instead of the word user, For example, My url will look like as [http://localhost/~charles/](http://localhost/~charles/) because my username is charles. 

If you don't know who is the user of the computer, just try the following command in the terminal,

```
whoami
```

Please keep in mind, to place your files in /var/www , you need root access.

---

