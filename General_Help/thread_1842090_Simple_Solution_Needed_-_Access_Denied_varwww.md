---
title: "Simple Solution Needed - Access Denied /var/www"
date: 2011-09-10
forum: General Help
---

### Post by littlememo on 2011-09-10
Hi
I am really new to ubuntu and programming and although I've always thought I was a geek but I'm really struggling.  I am trying to install wordpress on a laptop running Ubuntu.  As part of the installation I have gone through the LAMP installation process but when I try and extract the wordpress download files to /var/www I get access denied errors.  
I have been looking all over forums and help pages and everything I try does not seem to work, including various commands in terminal e.g. chmod etc and nothing seems to work.
I need a really simple idiot proof explanation of what to do, if thats possible.
Thanks
:D

---

### Post by bodhi.zazen on 2011-09-10
*Thread moved to **null**.*

Take a look at sudo and linux permissions.

[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

---

### Post by dazman19 on 2011-09-11
I think you will find the /var/www folder will be owned by www-data user.

If you want to put files here you will need to be logged in as a user who has root permissions (a sudo'er)

once the files are in the folder and you are ready to run the wordpress setup before you run it try this:

sudo chown -R www-data:www-data /var/www

You will probably find wordpress will work after this. Because if you run ls-l /var/www it probably will probably have some files owned by root or a user aother than www-data that wordpress needs. Wordpress also needs write access to the server directory (i think).  After running the command above all the files/folders should recursively be owned by the web server user.. 


daz@daz-laptop:/var/www$ ls -l
total 24
-rw-r--r-- 1 www-data www-data  20 Sep 11 14:42 phpinfo.php
-rw-r--r-- 1 www-data www-data 887 Sep 11 16:21 privatekey.key
-rw-r--r-- 1 www-data www-data 272 Sep 11 16:21 publickey.cer
-rw-r--r-- 1 root     root     729 Sep 11 16:16 ssltester_ok.php
-rw-r--r-- 1 www-data www-data 739 Sep 11 16:17 ssltester.php
-rw-r--r-- 1 root     root     998 Sep 11 16:29 ssltester_web.php

in my case not all these files are owned by the web server. there may be permissions problems here in your case.

---

### Post by bodhi.zazen on 2011-09-11
On a web server I keep files owned by root , group www-data

Permissions 440 if possible.

root can always rw the  files even with those permissions, but no reason to allow www-data w access to most files.

---

