---
title: "Setting permissions on /var/www/folder"
date: 2009-12-16
forum: General Help
---

### Post by swb_mct on 2009-12-16
I just moved an existing .php web site to a new ubuntu server. I installed apache and managed to copy the the folder "reg" into /var/www/. (There is not supposed to be a default page at the root of the web site. The starting url is [http://domain.com/reg](http://domain.com/reg)).
 
I need to set the permissions on the site which is simple static content.
 
The current permissions look like below and Access to the web site is denied. 
 
swbca@lin:/var/www$ ls -l
total 4
drw-r--r-- 4 root root 4096 2009-12-16 12:19 reg
 
(I am not linux literate, so please make instructions complete) Thank You

---

### Post by ean5533 on 2009-12-16
> **swb_mct said:**
> I just moved an existing .php web site to a new ubuntu server. I installed apache and managed to copy the the folder "reg" into /var/www/. (There is not supposed to be a default page at the root of the web site. The starting url is [http://domain.com/reg](http://domain.com/reg)).
 
I need to set the permissions on the site which is simple static content.
 
The current permissions look like below and Access to the web site is denied. 
 
swbca@lin:/var/www$ ls -l
total 4
drw-r--r-- 4 root root 4096 2009-12-16 12:19 reg
 
(I am not linux literate, so please make instructions complete) Thank You

Right now, public users have "Read" access on that directory but not "eXecute" access. Read access allows them to open files that are in that directory, but not to list the directory's contents; listing directory contents is a function needed for the browser to find the default .html index file.

To add execute access, run this command:

```
sudo chmod 755 reg
```

---

### Post by swb_mct on 2009-12-16
That helped, but now Apache doesn't recognize "index.php" as a web page.  When I go to [http://domain.com/reg](http://domain.com/reg) it ask if I want to save reg.   If i go to [http://domain.com/reg/index.php](http://domain.com/reg/index.php) it asks if I want to save index.php.
 
this site came from a Fedora server I set up 2 years ago, where .php support was in the default Web Server installation.

---

### Post by ean5533 on 2009-12-16
> **swb_mct said:**
> That helped, but now Apache doesn't recognize "index.php" as a web page.  When I go to [http://domain.com/reg](http://domain.com/reg) it ask if I want to save reg.   If i go to [http://domain.com/reg/index.php](http://domain.com/reg/index.php) it asks if I want to save index.php.
 
this site came from a Fedora server I set up 2 years ago, where .php support was in the default Web Server installation.

I've had that problem before with my Apache setup, but I can't remember for the life of me how I fixed it.

Do you have all the proper PHP libraries and apache mods installed? [This slightly outdated guide]("http://www.howtoforge.com/ubuntu_lamp_for_newbies") is a pretty straight forward walkthrough on getting a LAMP stack set up from scratch. You can go through it and determine if you missed any steps. 

Let us know if this still doesn't work for you.

---

### Post by wojox on 2009-12-16
[URL="https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting%20PHP%205"]roubleshooting PHP 5

Does your browser ask if you want to download the php file instead of displaying it? If Apache is not actually parsing the php after you restarted it, install libapache2-mod-php5. It is installed when you install the php5 package, but may have been removed inadvertently by packages which need to run a different version of php.

You may also need to actually enable it, by doing sudo a2enmod php5 followed by sudo /etc/init.d/apache2 restart. If sudo a2enmod php5 returns "$ This module does not exist!", you should purge (not just remove) the libapache2-mod-php5 package and reinstall it.

Be sure to clear your browser's cache before testing your site again. [/URL]

---

### Post by swb_mct on 2009-12-16
FIXED . . thanks.
 
I had installed some of the php5 modules but, then found the PHP5 package which added 1 more component.

---

