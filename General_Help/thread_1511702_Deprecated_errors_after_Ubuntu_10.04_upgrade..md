---
title: "Deprecated errors after Ubuntu 10.04 upgrade."
date: 2010-06-17
forum: General Help
---

### Post by pundip on 2010-06-17
I am getting a lot of “Cannot modify header information - headers already sent by” errors after upgrading to 10.04 (not fresh install) php applications such as torrentflux and gallery2 which were working before the upgrade are no longer working. Atmail install is also giving this error. Some research indicates that this maybe because of incompatibility with the new version of php but I am not sure. I not sure where to go from here so any advice will be appreciated.  Dont know much about the lamp stack i usually just install stuff and leave it. 
PHP version is PHP Version 5.3.2-1ubuntu4.2

Examples of the errors include

Warning: Cannot modify header information - headers already sent by (output started at /var/www/mail/libs/PEAR/DB.php:472) in /var/www/mail/install/index.php on line 158
Warning: Cannot modify header information - headers already sent by (output started at /var/www/torrent/adodb/adodb.inc.php:888) in /var/www/torrent/functions.php on line 114

---

