---
title: "Remove phpmyadmin and then reinstall"
date: 2011-04-22
forum: General Help
---

### Post by dragonfly41 on 2011-04-22
I have followed instructions here to install apache + php5 + mysql

[http://surferzworld.com/2010/10/installing-lamp-linux-apache-mysql-php-server-ubuntu/](http://surferzworld.com/2010/10/installing-lamp-linux-apache-mysql-php-server-ubuntu/)

Apache 2 server is working.   phpinfo.php shows php working.

...

I've previously installed phpmyadmin .. but this time I've made some error in installing phpmyadmin.

I would like to start afresh .. remove and reinstall.

I looked in Synaptic Package Manager and phpmyadmin had a green marker .. showing installed.

I tried "Mark for complete removal"

But I can't purge phpmyadmin installation to try again.  See screenshot.

Any tips to purge?

---

### Post by dragonfly41 on 2011-04-22
I managed to uninstall phpmyadmin through Synaptic Package Manager 
by just accepting the default ticks which came up in sequence
(with rather odd ticked options such as "retry" which was confusing).

I then reinstalled and followed the instructions here to reset root password.

[https://help.ubuntu.com/community/MysqlPasswordReset](https://help.ubuntu.com/community/MysqlPasswordReset)

I'm not sure if all these steps were necessary but I've now got phpmyadmin working.

---

