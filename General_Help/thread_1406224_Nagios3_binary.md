---
title: "Nagios3 binary?"
date: 2010-02-13
forum: General Help
---

### Post by KevKing on 2010-02-13
Have installed Nagios3 using synaptec manager.  All is working.
Trying to install nconf, to help configure Nagios, thought it would be simple, but having issues.  The instructions at

[http://www.nconf.org/dokuwiki/doku.php?id=nconf:help:documentation:installation](http://www.nconf.org/dokuwiki/doku.php?id=nconf:help:documentation:installation) 

are very easy to follow.  Only problem is when I enter [http://mysite.com/nconf](http://mysite.com/nconf) it just displays the php file:

<?php
###
###  WELCOME TO NConf, configuration files are located here : config/..
###
## do not change anything other
##

# look if configuration files exist
if (file_exists('config/main.php') ){
    require_once 'config/main.php';
    require_once 'include/head.php';

    # for all pages show the login or if logged in only version info
    require_once("include/login_form.php");

    # Load serverlist from cmdb if activated
    if ( defined('LOAD_SERVERLIST') AND (LOAD_SERVERLIST == 1)){
        $load_serverlist = 'include/modules/sunrise/load_serverlist.php';
        if (file_exists($load_serverlist) ){
            require_once ($load_serverlist); 
        }
    }
    require_once 'include/foot.php';
}else{
    # config not yet done, load from config.orig the needed data for install (head.php will handle the rest)
    require_once('config.orig/nconf.php');
    require_once('config.orig/authentication.php');
    require_once('include/functions.php');
    require_once 'include/head.php';
    require_once 'include/foot.php';
}



###
### Finish
### anything is loaded until here
###
?>
I have set the neccessary for webserver access, as the .php wouldn't display.  Or is there something missing there too?
Can any one tell me where the binary is for Nagios3, as nconf needs to know where it is to check the config on install, and I'm buggered if I can locate it?
Nagios3 installed at /etc/nagios3

Any pointers anyone?

---

### Post by florizs on 2010-02-26
late reply but I hope you can still use it.

you need to install apache2 php5-mysql libapache2-mod-php5 mysql-server

sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server

then restart the server

sudo /etc/init.d/apache2 restart

---

### Post by KevKing on 2010-02-26
Thanks for the reply floriz.  Problem was solved by enabling php modules globally, which had been due to installation of ispconfig.  All working now, but thanks anyway. I should have posted a follow up, to save peoples time submitting replies.

---

### Post by SporkD2 on 2010-07-23
Is there a more in depth guide other then the one listed in the first post? I succesfully installed nagios but am pretty clueless on this nconf. I need something for people to be able to easily add a host and figured this would be it.

---

