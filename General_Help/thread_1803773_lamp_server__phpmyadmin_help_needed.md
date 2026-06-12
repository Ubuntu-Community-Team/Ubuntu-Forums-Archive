---
title: "lamp server / phpmyadmin help needed"
date: 2011-07-13
forum: General Help
---

### Post by 9antreas9 on 2011-07-13
I am kind of new to ubuntu, I use 11.04 Natty.

I installed lamp server (sudo tasksel install lamp server) and the server and php work fine.

Then i installed phpmyadmin (sudo apt-get install phpmyadmin)

and restarted apache ( sudo /etc/init.d/apache2 restart).

When i browsed [http://localhost/phpmyadmin](http://localhost/phpmyadmin), i got a 404, so after some searches i found out that i had to include  "Include /etc/phpmyadmin/apache.conf" in my apache2.conf flie.

After restarting apache, i went to [http://localhost/phpmyadmin](http://localhost/phpmyadmin) and i am getting an error that says "Cannot start session without errors, please check errors given in your  PHP and/or webserver log file and configure your PHP installation  properly."

Any help on how to proceed from here?

Thank you for your time.

---

### Post by Dave_L on 2011-07-13
Have you checked the PHP and Apache log files for error messages?  The log files should be in /var/log/, possibly in a subdirectory.

---

### Post by 9antreas9 on 2011-07-14
thank you for your response.

In the folder var/log there was a subfolder apache2, that contained a file called error.log.

It's exact contents are below, though i dont think they are significant, because i go to localhost/phpmyadmin, i get the error message i posted in my first post, then i return to the error log and it is the same.
```

[Thu Jul 14 04:10:01 2011] [notice] Apache/2.2.17 (Ubuntu) configured -- resuming normal operations
[Thu Jul 14 04:10:03 2011] [notice] Graceful restart requested, doing restart
[Thu Jul 14 04:10:03 2011] [notice] Apache/2.2.17 (Ubuntu) configured -- resuming normal operations
[Thu Jul 14 04:13:57 2011] [notice] caught SIGTERM, shutting down
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20090626/pdo_mysql.so' - /usr/lib/php5/20090626/pdo_mysql.so: undefined symbol: php_pdo_register_driver in Unknown on line 0
[Thu Jul 14 04:14:01 2011] [notice] Apache/2.2.17 (Ubuntu) PHP/5.3.5-1ubuntu7.2 with Suhosin-Patch configured -- resuming normal operations
```

i was not able to locate the php error log. i turned display_errors on in my php.ini file in case additional information about the problem would appear, but still nothing.

---

