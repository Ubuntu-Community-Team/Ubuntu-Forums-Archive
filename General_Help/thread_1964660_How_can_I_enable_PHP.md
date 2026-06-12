---
title: "How can I enable PHP?"
date: 2012-04-24
forum: General Help
---

### Post by boxcorner on 2012-04-24
I am trying to use wview interface software with a Davis Vantage Vue weather station [http://www.wviewweather.com/release-notes/wview-User-Manual.html]("http://www.wviewweather.com/release-notes/wview-User-Manual.html")

Whenever I type: [http://localhost/wviewmgmt/login.php](http://localhost/wviewmgmt/login.php), in my browser, the file login.php is downloaded instead of being displayed as a wview management page.

It's been suggested that the web server is missing something in the config, or the PHP module isn't loaded / installed.

I can access the config using Webmin via localhost:10000 > Others > PHP Configuration, where I can see 3 PHP ini files: 
[INDENT]/etc/php5/apache2/php.ini[/INDENT] 
[INDENT]/etc/php5/cgi/php.ini[/INDENT]
[INDENT]/etc/php5/cli/php.ini[/INDENT] 
Webmin provides options to Manage | Edit Manually, however I don't know what changes to make! 

I under the impression that Ubuntu already included PHP.  What do I need to do in order to enable PHP?

I'm using Chromium 18.0.1025.151 (Developer Build 130497 Linux) Ubuntu 11.10 

Any help would be much appreciated!

---

### Post by bodhi.zazen on 2012-04-24
From [https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting_PHP_5](https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting_PHP_5)

> Does your browser ask if you want to download the php file instead of displaying it? If Apache is not actually parsing the php after you restarted it, install libapache2-mod-php5. It is installed when you install the php5 package, but may have been removed inadvertently by packages which need to run a different version of php.

If sudo a2enmod php5 returns "$ This module does not exist!", you should purge (not just remove) the libapache2-mod-php5 package and reinstall it.

Be sure to clear your browser's cache before testing your site again. To do this in Firefox 4: Edit &#8594; Preferences … Privacy &#8594; History: clear your recent history &#8594; Details : choose "Everything" in "Time range to clean" and check only "cache", then click on "Clear now". 

You might want to review the server guide as well

[https://help.ubuntu.com/11.10/serverguide/C/](https://help.ubuntu.com/11.10/serverguide/C/)

---

### Post by boxcorner on 2012-04-24
Excellent!  That did the trick.  Many thanks indeed.

---

