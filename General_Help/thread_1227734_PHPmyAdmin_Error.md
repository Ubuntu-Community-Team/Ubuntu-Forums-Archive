---
title: "PHPmyAdmin Error"
date: 2009-07-31
forum: General Help
---

### Post by healee on 2009-07-31
When I run [Http://localhost/phpmyadmin](Http://localhost/phpmyadmin) I got an error saying "This configuration file now needs a secret passphrase (blowfish_secret).  Should I need to look into the config file?  Where is it?  What could be the problem?

---

### Post by nikhilk on 2009-07-31
> **healee said:**
> When I run [Http://localhost/phpmyadmin](Http://localhost/phpmyadmin) I got an error saying "This configuration file now needs a secret passphrase (blowfish_secret).  Should I need to look into the config file?  Where is it?  What could be the problem?

Check [this]("http://ubuntuforums.org/showthread.php?t=621686") thread.

---

### Post by healee on 2009-07-31
> **nikhilk said:**
> Check [this]("http://ubuntuforums.org/showthread.php?t=621686") thread.
Thanks!  I've got it fixed.

---

### Post by raunhar on 2009-08-03
I installed LAMP on Ubuntu 8.10 using:
sudo apt-get install apache2 apache2-mpm-prefork php5-mysql mysql-server php5 libapache2-mod-php5 php5-cgi php5-gd php5-cli phpmyadmin

Evertything went normally.
Installation was successful.
I rebooted the PC. 
Went to [http://localhost](http://localhost)  Got the message It Works!

Then [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/)

OOps, did not find the link.

What could have gone wrong, or is there anything that I need to be installed.

I checked in Synaptec manager, phpmyadmin was shown as installed.

---

### Post by wojox on 2009-08-03
Did you include:

```
sudo gedit /etc/apache2/apache2.conf
```

Include the following line at the bottom of the file, save and quit.

```
Include /etc/phpmyadmin/apache.conf
```

Restart Apache:

```
sudo /etc/init.d/apache2 restart
```

And clear Browser Cache

---

### Post by raunhar on 2009-08-03
:popcorn::D
It worked

---

### Post by healee on 2009-08-06
> **raunhar said:**
> I installed LAMP on Ubuntu 8.10 using:
sudo apt-get install apache2 apache2-mpm-prefork php5-mysql mysql-server php5 libapache2-mod-php5 php5-cgi php5-gd php5-cli phpmyadmin

Evertything went normally.
Installation was successful.
I rebooted the PC. 
Went to [http://localhost](http://localhost)  Got the message It Works!

Then [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/)

OOps, did not find the link.

What could have gone wrong, or is there anything that I need to be installed.

I checked in Synaptec manager, phpmyadmin was shown as installed.
I really can't tell.  I am also pretty new to this system.  My version of ubuntu is 8.04 desktop edition and yous is not.  Hopefully somebody else will give you a hand.  Clear the cache and try again!

---

### Post by healee on 2009-08-06
> **raunhar said:**
> I installed LAMP on Ubuntu 8.10 using:
sudo apt-get install apache2 apache2-mpm-prefork php5-mysql mysql-server php5 libapache2-mod-php5 php5-cgi php5-gd php5-cli phpmyadmin

Evertything went normally.
Installation was successful.
I rebooted the PC. 
Went to [http://localhost](http://localhost)  Got the message It Works!

Then [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/)

OOps, did not find the link.

What could have gone wrong, or is there anything that I need to be installed.

I checked in Synaptec manager, phpmyadmin was shown as installed.
Read this page too!  It might help!
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by longtex on 2009-08-14
I just ran into the same thing. I'm kind of leaning toward the permissions issue, because I am almost 100% certain phpmyadmin was working fairly recently... I had changed some owners from self to www-data in the website directories because of (a) my general ignorance and (b) some weird crap Joomla seems to do. I actually have a virtually identical server at another location, also working with Joomla on that one; both are Ubu 8.04 desktop but being used as WordPress / Joomla web servers temporarily. The "other" one has phpmyadmin working fine; this one gave this BS about blowfish passphrase. I compared the phpmyadmin configs and are identical.

Rather than fart around with file/dir owners, I tried a suggestion from an old thread linked above, and it worked. Here it is:
> didn't solve it for me so instead I went into my /var/lib/phpmyadmin/blowfish_secret.inc.php and copied the
Code:

$cfg['blowfish_secret'] = 'your hash here';

and pasted at the bottom of /etc/phpmyadmin/config.inc.php

Worked for me, hope it helps you!

Thanks - Tex

---

