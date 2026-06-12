---
title: "how can i install ioncube loader on ubuntu 9.10 ?"
date: 2009-12-11
forum: General Help
---

### Post by Gladiator-prog4me on 2009-12-11
Hello 

i faces a problem when i try to use ioncube !

now i have install ( php5 , apache2 , mysql , phpmyadmin ) and it's working fine . 

and i have install ioncube , and edit php.ini

and this my result :

root@Mohamed-Laptop:/# php -v
PHP 5.2.10-2ubuntu6.3 with Suhosin-Patch 0.9.7 (cli) (built: Nov 26 2009 14:42:49) 
Copyright (c) 1997-2009 The PHP Group
Zend Engine v2.2.0, Copyright (c) 1998-2009 Zend Technologies
    with the ionCube PHP Loader v3.3.7, Copyright (c) 2002-2009, by ionCube Ltd., and
    with Zend Extension Manager v1.2.2, Copyright (c) 2003-2007, by Zend Technologies
    with Zend Optimizer v3.3.3, Copyright (c) 1998-2007, by Zend Technologies

and this is my php.ini file : 

zend_extension=/usr/local/ioncube/ioncube_loader_lin_5.2.so
zend_extension_ts=/usr/local/ioncube/ioncube_loader_lin_5.2_ts.so
zend_extension_manager.optimizer=/usr/local/Zend/lib/Optimizer-3.3.3
zend_extension_manager.optimizer_ts=/usr/local/Zend/lib/Optimizer_TS-3.3.3
zend_optimizer.version=3.3.3
zend_extension=/usr/local/Zend/lib/ZendExtensionManager.so
zend_extension_ts=/usr/local/Zend/lib/ZendExtensionManager_TS.so

and i'am sure the /usr/local/ioncube  >> it's true 

but when i try to use script " whmcs "  in /var/www 

i got this error : 

Site error: the file /var/www/whmcs/index.php requires the ionCube PHP Loader ioncube_loader_lin_5.2.so to be installed by the site administrator.

please can you help me ?

---

### Post by Gladiator-prog4me on 2009-12-11
thank you ,

the problem , has been fixed

---

### Post by nemo6910 on 2009-12-13
Please, can you explain how did you fix it?
I have the same mistake...

PS: Sorry for my english, i'm french.

---

### Post by fand on 2010-01-15
> **nemo6910 said:**
> 

PS: Sorry for my english, i'm french.

Check Your SELinux settings in my logs is notte about this bug but I don check it jet... 


PS: Sorry for my english, i'm Polish. :);)

---

### Post by ikillbill on 2010-01-19
Hello

I have EXACT issue

could you please tell us more how to fix this issue?

ubuntu 9.10
PHP 5.2.10
apache 2

---

### Post by kopyphany on 2010-04-05
I have the same problem can you tell me how to fix?

---

### Post by PA28 on 2010-08-11
If anyone else is having trouble with this, check out this guide. It worked great for me (Ubuntu 10.04 Lucid, PHP 5.3).

[http://www.aionsolution.com/blog/linux/install-ioncube-in-ubuntu/](http://www.aionsolution.com/blog/linux/install-ioncube-in-ubuntu/)

Lucid ships with PHP 5.3 by default, so make sure you download the latest version on ionCube (3.3.20+) and change the extension inclusion line from the guide to:

```
zend_extension = /usr/local/ioncube/ioncube_loader_lin_5.3.so
```

Just remember that this will get ionCube up and running for PHP in Apache. For PHP on the command line you'll need to include the above extension line in the CLI version of the php.ini as well (/etc/php5/cli/php.ini).

Hopefully this helps someone else in the future. ;)

---

