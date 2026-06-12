---
title: "Apache2 not parsing .php files"
date: 2006-02-12
forum: General Help
---

### Post by rmarkin on 2006-02-12
I recently attempted to update my php4 installation to php5 unsuccessfully.  The system had been handling .php files correctly until the upgrade, but afterwards my browser would simply ask if I wanted to to "save" or "open with" the .php file.  I wanted to get it working again so I tried to remove php5 in favor of php4.  (all using newest versions in Synaptic by the way).  I had alot of trouble removing phpmyadmin which I finally figured out with help from the forum.

Long story short, after removing all php components as well as apache2 I re-installed the original setup of apache2 and php4 and I am still getting the same problem with my .php files not being parsed.

I am using the normal phpinfo script as follows in my /var/www folder.

<?php

phpinfo();

?>

Apache seems to be working correctly with .html files just not with .php files.
When the "save" dialog box popped up I downloaded the file just to verify and I was able to see the same script as above which I shouldn't have.

I uncommented the following lines in my apache2.conf file and restarted apache but received the same results.

AddType application/x-httpd-php .php
AddType application/x-httpd-php-source .phps

Any ideas how to start troubleshooting this?

---

### Post by lolocaust on 2006-02-12
try editing /etc/mime.types, and comment out the php lines.

---

### Post by ZylGadis on 2006-02-12
This is exactly the same problem I encountered some time ago after an apache upgrade. After two days of reinstalling, tweaking config files and what not, I accidentally opened apache from another machine - and it worked! The conclusion I reached is that the problem is related to the client side, i.e. to the browser. A browser which was used to open the old .php files (before the upgrade) won't open the new ones (after the upgrade).
You can either try a different browser / machine, or clear the cache of your browser.
I would be very willing to hear a php / apache guru explain the cause for that. And, of course, I hope that helps you solve the problem.

---

### Post by rmarkin on 2006-02-13
Thanks for the replies,

Alex,
I tried clearing the cache in Firefox, using IE (which hadn't attempted to access the site yet), and my wife's Mac.  All received the same result.

lolcaust,
I commented out the five lines in /etc/mime.types that begin with application/x-httpd-php....... php...
I then restarted Apache usind "apache2ctl -k restart", this unfortunately did not change the syptoms either.

In the hopes of isolating the problem, I un-commented those five lines afterwards.  Please correct me if I'm wrong and I will comment them out again.

Robert

---

### Post by jordman13 on 2006-02-14
Hi all, 

I've been having the exact same problems.  My php was working perfectly fine until I installed a few extra php modules and phpmyadmin.  Now it won't parse any .php files no matter what I do.  I tried uninstalling php and reinstalling it but to no avail.  I have no clue what to do.  

Thanks a lot.

---

### Post by evenstranger on 2006-02-15
Has there been any progress on this ? I have had similar problems since upgrading to php5 and then trying to revert to php4, installed/removed several times with no success.

---

### Post by jordman13 on 2006-02-15
Hi all, 

I managed to solve the problem by tweaking several config files.  

I think the two things that did it were, first, pointing symlinks in the /etc/apache2/modules-enabled to the php5 modules in the /etc/apache2/modules-available folder and then in the httpd.conf file I entered this line LoadModule php5_module /usr/lib/apache2/modules/libphp5.so.   

It seemed to work after that.  

Best of luck.

---

### Post by davidcrickett on 2006-02-15
I had the same problem, used lots of time on it, but in the end the solution was to use PHP5 - again. Seems like reverting to PHP4 is impossible. :rolleyes:

---

### Post by schmidty on 2006-02-19
I'm having the same problem and have tried everything I can think of...but to no avail. Any suggestions?

Schmidty

---

### Post by rmarkin on 2006-02-23
Sorry for the delayed response.  I finally was able to get PHP working but the only way that I did was to install from source.  After reading numerous tutorials, I compiled php 4.4.2 from the php.net website and it works.  I am not really sure what the original problem was, but at least now it works.

Schmidty, what do you currently have installed, and what are your current symptons?

---

### Post by az_human on 2006-02-23
In my limited experience with apache / php / ubuntu, I have found that if I initially install apache2 + php4 + various modules and then later remove php4 and go to php5 and decide to go back to 4, it always screws with the links in my /etc/apache2/mods-enabled and /etc/apache2/mods-available folders.  You should have links in the mods-enabled folder to php4(or 5).conf and php4(or 5).load which should physically exist in the mods-available folder.  Removing all packages and modules and such and reinstalling them did not seem to make any difference for me no matter what I did.

In my particular experiences (I have hosed this up on more than one occasion), I took a snapshot of the directories and configuration files while things were working properly with php4.  I then upgraded to php5 and all associated packages / modules.  I then removed php5, went back to php4 and took a second snapshot to see what changed.  The only changes I could see were that the files / links were not in the mods-enabled folder and / or the mods-available folder.  The first time this happened, the php4.load and php4.conf files were gone altogether.  Reinstalling those packages simply wouldn't put those files back... 

Anyhow, that's my experience.  I'd recommend doing some directory and config file backups beforehand while you have a working system in case you decide to upgrade / downgrade.

---

### Post by schmidty on 2006-04-20
I have Breezy, Apache2 and PHP5. I have had this problem before with Hoary and ended up totally re-installing the Ubuntu (for other reasons besides this one). I am somewhat new to the Debian flavor or Linux and was wondering if there is a way to completely ERASE the files with apt-get or dpkg? Thanks for your help...

Schmidty

---

### Post by schmidty on 2006-04-20
Success!!!! I totally re-installed Apache2 and php5 and then clear my browser cache as mentioned above and it worked!!! Thanks for the help on this...

I originally was having problems with php5 and the GD module. When I run the command line interpretor for php I get this error message;

PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20041030/gd.so' - libt1.so.5: cannot open shared object file: No such file or directory in Unknown on line 0

Any suggestions or help on this? Could I re-install php5 and gd from source using dpkg? I am somewhat new to using apt-get and dpkg. Thanks...

Schmidty

---

