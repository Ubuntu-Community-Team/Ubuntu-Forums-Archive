---
title: "Php doesn't show error messages"
date: 2010-03-28
forum: General Help
---

### Post by manoelcampos on 2010-03-28
I'm using Ubuntu Desktop 9.10, Apache 2.2.12 and PHP 5.2.10, installed by apt-get. The problem is that PHP doesn't show error messages. Warnings is showed. I found php.ini file at:

/usr/share/php5/php.ini
/etc/php5/apache2/php.ini
/etc/php5/cli/php.ini

And I changed the variables below (at all php.ini files):

error_reporting = E_ALL & E_NOTICE
display_errors = On
display_startup_errors = On
ignore_repeated_errors = Off
ignore_repeated_source = Off

I restarted apache after changes, but only warning is showed.

---

### Post by manoelcampos on 2010-05-04
I solved the problem setting log_errors = Off at php.ini file.
The default value is setted to On

---

