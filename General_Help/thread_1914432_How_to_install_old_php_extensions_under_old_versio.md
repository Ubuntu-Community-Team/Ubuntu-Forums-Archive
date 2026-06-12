---
title: "How to install old php extensions under old versions of lampp?"
date: 2012-01-24
forum: General Help
---

### Post by Luca Borrione on 2012-01-24
Hello,

I'm using lubuntu oneiric.

I need to use different versions of lampp on my developing machine because we have different projects developed and running on differente environments. That means that a "project A" was developed under Apache 2.2.11 with MySQL 5.1.33 and PHP 5.2.9 while a "project B" was developed under Apache 2.2.21 with MySQL 5.5.16 and PHP 5.3.8 and so on .. and now they are online under the same environment on which they were originally developed.

I'm a developer, so it happens to me that when they ask me to modify something I need to recreate quickly the correct environment for the project to modify.
If they ask me to modify the "project A" I will install lampp 1.7.1 for example while I need to install lampp 1.7.7 to modify the "project B" and so on.

I successfully managed how to install and remove different versions of lampp, but the problem comes out for the extensions!

If I need for example to use memcache, if I'm running lampp 1.7.7 I simply do
```
sudo apt-get install php5-memcache
sudo cp -av '/usr/lib/php5/20090626+lfs/memcache.so' '/opt/lampp/lib/php/extensions/o-debug-non-zts-20060613/memcache.so'
```
then I add extension="memcache.so" to php.ini, restart lampp and that's done!

But if I need to use lampp 1.7.1 I cannot do the same because they differ in version!

If I try to copy
```
sudo cp -av '/usr/lib/php5/20090626+lfs/memcache.so' '/opt/lampp/lib/php/extensions/o-debug-non-zts-20060613/memcache.so'
sudo chmod 755 '/opt/lampp/lib/php/extensions/o-debug-non-zts-20060613/memcache.so'
```

I get this error
```
Starting XAMPP for Linux 1.7.1...
PHP Warning:  PHP Startup: memcache: Unable to initialize module
Module compiled with module API=20090626, debug=0, thread-safety=0
PHP    compiled with module API=20060613, debug=0, thread-safety=0
These options need to match
in Unknown on line 0
```

I get a similar problem if I try to install gd. Alway running lampp 1.7.1 if I do:
```
sudo apt-get install php5-gd
sudo cp -av '/usr/include/php5/ext/gd/php_gd.h' '/usr/lib/php5/20090626+lfs/gd.so'
sudo chmod 755 '/opt/lampp/lib/php/extensions/no-debug-non-zts-20060613/gd.so'

```

adding extension="gd.so" to php.ini and restarting lampp, I get this error
```
PHP Warning:  PHP Startup: Unable to load dynamic library '/opt/lampp/lib/php/extensions/no-debug-non-zts-20060613/php_gd.h' - /opt/lampp/lib/php/extensions/no-debug-non-zts-20060613/php_gd.h: invalid ELF header in Unknown on line 0
```

So how can I install old versions of php extensions to old versions of lampp?

---

### Post by dragonfly41 on 2012-01-24
I have not been faced with this problem ..
but one possible approach comes to mind.

Could you pre-install the different lampp environments and then use a switch in a script to pre-select the different sessions for running as lampp1, lampp2, lampp3, lampp4 etc.

Of course the paths to php and mysql in lampp stacks (but not apache2 which seems to be common throughout) would have to be renamed.

/etc/php5-a/apache2/php.ini
/etc/php5-b/apache2/php.ini
/etc/php5-c/apache2/php.ini
/etc/php5-d/apache2/php.ini

You would then have a unique php.ini for each version of lampp and you could set different virtual directories instead of default var/www

Same approach with different mysql configurations to match.

[http://netbeans.org/kb/docs/php/configure-php-environment-ubuntu.html](http://netbeans.org/kb/docs/php/configure-php-environment-ubuntu.html)

In fact your lampp switch could be in a php script. 

This script would need to parse /etc/apache2/apache2.conf   (or perhaps httpd.conf which is included in apache2.conf).

So the question is .. can your paths to different lamp stacks be dynamically switched by **rewriting** httpd.conf for different projects?

Check permissions though of this folder for rewriting.

[http://stackoverflow.com/questions/2567432/ubuntu-apache-httpd-conf-or-apache2-conf](http://stackoverflow.com/questions/2567432/ubuntu-apache-httpd-conf-or-apache2-conf)

Then restart apache2 for after selection of each lampp stack.

...

Admittedly this is a brute force approach.  
But I don't see how you could mix old and new extensions in one lampp configuration.
So some setup script is needed.

Perhaps eclipse might allow different projects.


//==========================================
[COLOR=Navy]
[EDIT] Here is another wild idea .. different to above approach.

Perhaps you could you organise your configuration to manually pre-install lampp versions in a number of portable USB sticks, while keeping rest of Ubuntu and docroot in internal drive?

Then it would be just a simple matter of plugging in and mounting the appropriate lampp stack installed on different USB sticks.  The www files would be in the host Ubuntu configuration.[/COLOR]

---

