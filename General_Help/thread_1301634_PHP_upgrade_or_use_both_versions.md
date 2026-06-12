---
title: "PHP upgrade or use both versions?"
date: 2009-10-26
forum: General Help
---

### Post by milindras on 2009-10-26
Hi All,
Have a live Web server (Ubuntu 4.1.2-13ubuntu2). Which is running Apache2, Mysql 5 & php 4.4. The websites running on the server were created using php4.4.
 
If I upgrade php4.4 to php5 will it effect any existing websites?
 
Or Should I need to run Both versions of PHP?
 
Thanks
Milindra

---

### Post by martrn on 2009-10-26
No you don't need to run both versions of php.

There was a change from php4.2 and up, that effected a lot of websites but was changed for security reasons from the web server site. There are not many sites written in php4.4 will stop working if upgrading to php5.

We are now at php version 5.3.0.

You have to upgrade some time, and no longer need to run php 4.

---

### Post by milindras on 2009-10-26
Ok Thanks Mate.

---

### Post by dgoosens on 2009-10-26
as PHP 4 is no longer supported and worked on by the PHP-people...
you should try to make the switch asap...

have a look at this:
[http://be2.php.net/manual/en/migration5.php](http://be2.php.net/manual/en/migration5.php)

---

### Post by milindras on 2009-10-27
I already have more than 50 websites on the server which runs on php4. I can't test these all with php5. Our future development sites will be run on php5. So I would like to keep both versions working on my server. Can you help me where can I find good guide lines to do that? (run php4 & php5 at the same time).
 
Many thanks

---

### Post by martrn on 2009-10-27
> **milindras said:**
> I already have more than 50 websites on the server which runs on php4. I can't test these all with php5. Our future development sites will be run on php5. So I would like to keep both versions working on my server. Can you help me where can I find good guide lines to do that? (run php4 & php5 at the same time).Many thanks

To 'keep' both versions you have to configure apache2 properly.

[URL="http://www.gentoo.org/proj/en/php/php4-php5-configuration.xml"]
http://www.gentoo.org/proj/en/php/php4-php5-configuration.xml[/URL]

Which method you follow will depend which php version is installed as a apache cgi module either one or the other or both or if you have two version of apache running and both php4 and php5 are configured as apache modules.

The debian (and ubuntu) installation of apache2 running with PHP5 and PHP4 at the same time is at [http://www.howtoforge.com/apache2_with_php5_and_php4]("http://www.howtoforge.com/apache2_with_php5_and_php4").

---

### Post by milindras on 2009-11-05
Ok I decided to upgrade to PHP5 rather than keeping both versions. Just in case if I need to revert back to php4 again(after the upgrade), which files should I backup on php4 before I do the upgrade?
 
Thanks
milindra

---

