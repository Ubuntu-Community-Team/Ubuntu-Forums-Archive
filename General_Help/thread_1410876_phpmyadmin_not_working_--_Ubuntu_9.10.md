---
title: "phpmyadmin not working -- Ubuntu 9.10"
date: 2010-02-19
forum: General Help
---

### Post by subodh.rohilla on 2010-02-19
I installed phpmyadmin using synaptic manager (selected apache2 as server option ) and then i opened localhost/phpmyadmin .

It gives the following error : 

phpMyAdmin - Error

Cannot start session without errors, please check errors given in your PHP and/or webserver log file and configure your PHP installation properly.


I have apache,php and mysql already installed and I am using them with default configuration . There are many files in /var/log/apache2 and i am not not able to figure out anything

---

### Post by subodh.rohilla on 2010-02-20
phpmyadmin is now working for me. The problem was with the permissions of "session_save.path" attribute of php   to which the we have to give write permission and then it works properly. The default session.save_path in ubuntu is 	/var/lib/php5 which can be seen by printing output of phpinfo() function.

For futher details please check out : [http://wiki.phpmyadmin.net/pma/session.save_path]("http://wiki.phpmyadmin.net/pma/session.save_path")

---

