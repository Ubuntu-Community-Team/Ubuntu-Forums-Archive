---
title: "mysql / php problem"
date: 2011-07-13
forum: General Help
---

### Post by stellaconcepts on 2011-07-13
Hi All, 

I have a question - I am pulling down the latest version of the package php5-mysql

sudo apt-get install php5-mysql
Reading package lists... Done
Building dependency tree       
Reading state information... Done
php5-mysql is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 180 not upgraded.

Seems to work just fine - except it doesnt....

Configuration File (php.ini) Path /etc/php5/apache2  Loaded Configuration File /etc/php5/apache2/php.ini  



When I do phpinfo - the mysql module is not loaded...

Loaded Modules core mod_log_config  mod_logio prefork http_core mod_so mod_alias mod_auth_basic  mod_authn_file mod_authz_default mod_authz_groupfile mod_authz_host  mod_authz_user mod_autoindex mod_cgi mod_deflate mod_dir mod_env  mod_mime mod_negotiation mod_php5 mod_reqtimeout mod_setenvif mod_status  


YES, I've restarted apache after the apt-get 



What am I missing? I need that mysql lib!!!! driving me nutso!!!

Thanks for your help.

---

### Post by stellaconcepts on 2011-07-13
its ok - got it sorted.

there goes 3 hours of my life ill never get back.


why do we do this job people - seriously.

---

