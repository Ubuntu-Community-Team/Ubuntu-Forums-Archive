---
title: "PHP does not display warnings"
date: 2010-09-01
forum: General Help
---

### Post by Autodidact on 2010-09-01
Recently I upgraded to Ubuntu 10.0.4.1. 
Everything works perfect.
Then I installed LAMP with:
```
sudo apt-get install libapache2-mod-auth-mysql php5-mysql apache2 php5 libapache2-mod-php5 mysql-server
```

PHP renders all files perfectly. 
But when an error occurs, noting happens. 
PHP just dies without showing any warnings and returns an blank page.

php.ini has been set to:
```
display_errors = On
```

I also tried to add these lines to my PHP files:
```
ini_set('display_errors', 1); 
ini_set('log_errors', 1); 
ini_set('error_log', dirname(__FILE__) . '/error_log.txt'); 
error_reporting(E_ALL);
```

But still no warnings show up.

For example, this page renders perfectly:
```
<? echo 'Hello'; ?>
```
And this returns an empty page:
```
<? ech 'Hello'; ?>
```
While it should return something like:
```
Parse error: syntax error, unexpected T_CONSTANT_ENCAPSED_STRING in /var/www/sample.php on line 1
```

Please help! As far I know, the warnings should show up now...

---

