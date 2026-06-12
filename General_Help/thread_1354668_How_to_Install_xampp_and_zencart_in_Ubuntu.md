---
title: "How to Install xampp and zencart in Ubuntu"
date: 2009-12-14
forum: General Help
---

### Post by aimwin on 2009-12-14
---------------------------------------------------------------------
I think it is easier for LAMP installation than xampp yes.
But still cannot recommend those who are used to xampp to swich to LAMP totally since I still could not find a few other functions that is equivalent to
1. /opt/lampp/lampp security
2. security status check
-----------------------------------------------------------------
****** please note ***** edited 10 April 2010
Please read the #2 post by cariboo907 which suggest to use LAMP.(Thank you very much)
and my post #4 "LAMP"&Zencart Installation (which inspired by cariboo907) 
before decide to try this XAMPP&Zencart installation.

Also I found the following link since 2006 which give more details on how to install XAMPP
[http://ubuntuforums.org/showthread.php?p=1302487#post1302487](http://ubuntuforums.org/showthread.php?p=1302487#post1302487)
--------------------------
[COLOR="Red"]****** edited July 7 2010.*****
XAMPP new version [xampp-linux-1.7.3a]("http://www.apachefriends.org/en/xampp-linux.html#374")
Zencart new verion [zen-cart-v1.3.9d-full-fileset-06032010]("http://www.zen-cart.com/")
Ubuntu 10.04 
>>>> work with the following tutorial >>> all fully compatible with each other. 
"Work out of the box" with not problems and you can ignore the No. 12 and 13..[/COLOR]

[COLOR="Blue"]Summary of the commands.
Details tutorial for new Ubuntu user ---> please see detail tutorial below this section.
My default Ubuntu user name is "user1", working directory is "Desktop" and shopping cart directory is "Zencart"
If want, you can change
: "user1" to your Ubuntu User Name.
: "Desktop" to your other preferred directory 
: "zencart" to other directory name.

--install xampp ---
1. copy xampp-linux-1.7.3a.tar.gz, to Desktop.
2. Open Terminal

3. cd Desktop

4. sudo tar xvfz xampp-linux-1.7.3a.tar.gz -C /opt
    sudo /opt/lampp/lampp start
    sudo /opt/lampp/lampp security
 >>>> setup your passwords on all options.

sudo /opt/lampp/lampp restart

--install Zencart-----(unzip zencart.tar.gz to /home/user1/Desktop, then rename unzip folder to "zencart".)

sudo mv /home/user1/Desktop/zencart /opt/lampp/htdocs/zencart
sudo cp /opt/lampp/htdocs/zencart/admin/includes/dist-configure.php /opt/lampp/htdocs/zencart/admin/includes/configure.php
sudo cp /opt/lampp/htdocs/zencart/includes/dist-configure.php /opt/lampp/htdocs/zencart/includes/configure.php

cd /opt/lampp/htdocs/zencart

sudo chmod -R 777 ./cache
sudo chmod -R 777 ./pub
sudo chmod -R 777 ./images
sudo chmod -R 777 ./includes/languages/english/html_includes
sudo chmod -R 777 ./media
sudo chmod -R 777 ./pub
sudo chmod -R 777 ./admin/backups
sudo chmod -R 777 ./admin/images/graphs
sudo chmod 777 ./includes/configure.php
sudo chmod 777 ./admin/includes/configure.php

sudo /opt/lampp/lampp restart

Goto Firefox key in "http://localhost"
login with "user lampp" and your password
login to "phpmyAdmin" with "user root" and your password,
 >>.....to creat your database name, "zencart" (or your choice).

key in firefox "http://localhost/zencart/zc_install" follow the instructions.

After finish installation of zencart. use Firefox "http://localhost/zencart"

sudo mv /opt/lampp/htdocs/zencart/zc_install /opt/lampp/htdocs/zencart/yourname_zc_install

cd /opt/lampp/htdocs/zencart
sudo chmod 444 ./includes/configure.php

Finish
[/COLOR]

[COLOR="Red"]For details instruction please read further[/COLOR]

-------------------------------------
Zencart 1.38a (06/12/2009) not compatible with xampp 1.7.2
you will have error try to install with this version.

And that is the reason made me write this tutorial.
[COLOR="Red"]But as I have edit this tutorial on July 7 2010,
New Versions of XAMPP 1.7.3a, Zencart 1.3.9d and Ubuntu 10.04 work out of the box.
So you can ignore the below patches and problems.[/COLOR]

I also has successfully modify zencart 1.38a to suit xampp 1.7.2, 
by following instruction in the following links.
[http://www.zen-cart.com/forum/showthread.php?p=879890](http://www.zen-cart.com/forum/showthread.php?p=879890)
[http://www.zen-cart.com/forum/showthread.php?t=140960](http://www.zen-cart.com/forum/showthread.php?t=140960)

For this article we use standard package.
------------------------------------------

I test with ubuntu 9.04 / 9.10
I use zen-cart-v1.3.8a-full-fileset-12112007.zip
and xampp-linux-1.7.1.tar.gz
and assume that we will use default install directory /zencart
and unzip downloaded zencartxxx.zip to "Desktop" and Ubuntu user name is "user1"
If want, you can change
: "user1" to your Ubuntu User Name.
: "Desktop" to your other preferred directory 
: "zencart" to other directory name.
But don't forget to change in all command lines.

I will recommend the new user to create new "user1" with admin privilege and login to Ubuntu with "user1".
Download zencart and xampp to Desktop. and don't change anything in the commands below.
 
[COLOR="Red"]You can copy the "sudo command lines" and paste in the Terminal[/COLOR]

[COLOR="Magenta"]sudo command will give you administrative rights to modify file systems.
you need to use your "user password" to key in in order to continue to execute the resest of the commnands.[/COLOR]
--------------------------

[COLOR="Green"]A) Intall XAMPP 1.7.1[/COLOR]

1. Download xampp-linux-1.7.1.tar.gz to "your directory".( /home/user1 for my computer)

2. Unzip xampp using tar

open terminal(Aplication> Accessories> Terminal)
Make sure you are in your directory, user1
if not key in the command in the Terminal.

cd /home/user1

(in my case "cd /home/user1" then I have "user1@user1-desktop:~$............." show in the Terminal)
then key in or copy and past and ENTER (don't use Ctrl V -- you must use mouse right click in the Terminal)

sudo tar xvfz xampp-linux-1.7.1.tar.gz -C /opt

3. We need to setup security for xampp
Go to Terminal

sudo /opt/lampp/lampp start
sudo /opt/lampp/lampp security

set password for your lampp login
set mysql to be or not to be access by network user.
set password for php myadmin
set password for mysql root
set password for nobody Ftp account.

sudo /opt/lampp/lampp restart

[COLOR="Green"]B) Install Zencart[/COLOR]

4. download zencart and unzip to /home/user1/Desktop (or your directory)
and rename "zen-cart-v1.3.8a-full-fileset-12112007" directory to "zencart"

5. go back to Terminal

sudo mv /home/user1/Desktop/zencart /opt/lampp/htdocs/zencart

or use 

gksudo nautilus

use "root_nautilus" to copy the "whole" zencart directory to /opt/lampp/htdocs/

(you click on "Filesystem" on the left colum,
then click on "home" on the right pane window.
then click on "user1", "Desktop" and right click on "zencart" and choose copy,
then go back to "Filesystem" then left clik on "opt", "lampp" then "htdocs", right click and paste)

so you will have /opt/lampp/htdocs/zencart as your Zencart installed directory now.

6. You have to rename 2 "dist_config.php"
And need to change permission to a number of directories.

Goto Terminal

sudo cp /opt/lampp/htdocs/zencart/admin/includes/dist-configure.php /opt/lampp/htdocs/zencart/admin/includes/configure.php
sudo cp /opt/lampp/htdocs/zencart/includes/dist-configure.php /opt/lampp/htdocs/zencart/includes/configure.php
cd /opt/lampp/htdocs/
sudo chmod -R 777 ./zencart
cd zencart
sudo chmod -R 777 ./cache
sudo chmod -R 777 ./pub
sudo chmod -R 777 ./images
sudo chmod -R 777 ./includes/languages/english/html_includes
sudo chmod -R 777 ./media
sudo chmod -R 777 ./pub
sudo chmod -R 777 ./admin/backups
sudo chmod -R 777 ./admin/images/graphs
sudo chmod 777 ./includes/configure.php
sudo chmod 777 ./admin/includes/configure.php

[COLOR="Red"]9. at Terminal

sudo /opt/lampp/lampp restart

10. creat "zencart" database
Goto firfox key in

"http://localhost"

Choose the language you want, mine is English.
The: login user id is "lampp" 
and the password you have chosen.
click on the almost to the bottom of left hand side menu "phpMyAdmin"
login user id "root" and password you have chosen.
type "zencart" or your chosen database name.
Click create then after sucessful creation,
Click on exit.[/COLOR]

11. key in firefox "http://localhost/zencart/zc_install"
follow the instructions.

12. if you have error "Register Globals = ON"
***do not follow the link tutorial in zencart, there is problem,
from [http://localhost/zencart/zc_install/...?error_code=69](http://localhost/zencart/zc_install/...?error_code=69)
I have modified the first line by
deleting "php_value session.use_trans_sid off"
becuase it cause error in NO. 13 - despite the correction procedure in No.13,
I have to spend 2 hours to identify this issue.)

Goto Terminal

sudo gedit .htaccess

copy the below lines

php_value register_globals off
#php_value register_globals off
<Files ".ht*">
deny from all
</Files>

save the file in /opt/lampp/htdocs/zencart
using the name .htaccess

13. if you have error "PHP session.use_trans_sid = ON"

goto Terminal

sudo gedit /opt/lampp/etc/php.ini

click on "search" tap on the menu bar.
copy and paste
"session.use_trans_sid"
and click "find"
change the value "1" to "0" (zero)
and Click "save"

*** and you must do this step before try to refresh "http://localhost/zencart/zc_install/..." ***
Go to Terminal

sudo /opt/lampp/lampp restart

Now try to refresh or recheck in your "http://localhost/zencart/zc_install/....".

Then continue with the Zencart installation instructions.

14. After finish installation of zencart.
use Firefox
"http://localhost/zencart"
there should be 2 errors

14.1 "Installation directory exists at: /opt/lampp/htdocs/zencart/zc_install..."
correct this error by

Go to Terminal

sudo mv /opt/lampp/htdocs/zencart/zc_install /opt/lampp/htdocs/zencart/yourname_zc_install

14.2 "I am able to write to the configuration file: /opt/lampp/htdocs/zencart/includes/configure.php....."
correct this error by

cd /opt/lampp/htdocs/zencart
sudo chmod 444 ./includes/configure.php

Go to Firefox and Reload the "http://localhost/zencart"
all the 2 errors should disappear.

15 finished

I am not an advance user, just ordinary user but took me 7 days to install zencart 1.38a to xampp 1.7.2
and found out that it can not be done, must use Xampp 1.7.1 becuase it is not compatible yet.
and finally find other problems and all bit and pieces from differents posts and decide to wrote this tutorial to help the newbies like me
So not to waste time so much again.

I copy some command from this sites
[http://www.zen-cart.com/forum/showthread.php?t=43937](http://www.zen-cart.com/forum/showthread.php?t=43937)


since I did not intend to write this tutorial at the beginning.
Untill I found that those tutorials and posts misled me to many wrong paths.
And I have to correct certain bits and pieces to concluded to this tutorial.

It work with my environment, there may be problems, please be cautions and try the tutorial.
I cannot guarantee it will work 100% on your system.

---

### Post by cariboo on 2009-12-14
Just a question, why not use LAMP, which is in the repositories, instead of jumping through hoops getting xampp installed?

---

### Post by aimwin on 2009-12-15
I have been using xampp and zencart for long time on windows before I migrate to ubuntu, and I found it easy to use.

To start with LAMP I face new TASK of learning.
I did install ubuntu server and I am a novice.
I end up give up using ubuntu server for the time being.

UNTIL I have a bit more time.

I just try now to use ubuntu software center (I prefer the old Add Remove Program) I get no where to install LAMP, neither Synaptic.

Next post I found how to install LAMP using Terminal.

---

### Post by aimwin on 2009-12-15
update
11 April 2010
> **cariboo907 said:**
> Just a question, why not use LAMP, which is in the repositories, instead of jumping through hoops getting xampp installed?
---------------------------------------------------------------------
I think it is easier for LAMP installation than xampp yes.
But still cannot recommend those who are used to xampp to swich to LAMP totally since I still could not find a few other functions that is equivalent to
1. /opt/lampp/lampp security
2. security status check
----------------------------------------------------------------
Before you proceed, if you install LAMP, you will not be able to use XAMPP while LAMP is running.
So if you want to run XAMPP after -- I don't know how to disable LAMP stacks.
I only know how to un-install LAMP from following link 
[http://tuxtweaks.com/2010/01/how-to-uninstall-lamp-in-ubuntu-9-10-karmic-koala/](http://tuxtweaks.com/2010/01/how-to-uninstall-lamp-in-ubuntu-9-10-karmic-koala/)
after that you can use XAMPP again.
---------------------------------------------------------------------------------

from
[http://ubuntuforums.org/showthread.php?t=1336428&highlight=LAMP](http://ubuntuforums.org/showthread.php?t=1336428&highlight=LAMP)
I have install LAMP and PHPmyAdmin using

sudo tasksel install lamp-server

then

sudo apt-get install phpmyadmin

If everything work successful,
[http://localhost](http://localhost)
you should get
[COLOR="Blue"]
"It works!
This is the default web page for this server.
The web server software is running but no content has been added, yet."[/COLOR]

and 
[http://localhost/phpmyadmin](http://localhost/phpmyadmin)

should bring up the "[COLOR="Magenta"]phpmyadmin control page or panel[/COLOR]"

I use

sudo nautilus

to bring up "root nautilus" to unzip, rename the directory to zencart,
and copy it to /var/www
and start the installation process by using the following command lines

sudo cp /var/www/zencart/admin/includes/dist-configure.php /var/www/zencart/admin/includes/configure.php
sudo cp /var/www/zencart/includes/dist-configure.php /var/www/zencart/includes/configure.php

cd /var/www/

sudo chmod -R 777 ./zencart

cd zencart

sudo chmod -R 777 ./cache
sudo chmod -R 777 ./pub
sudo chmod -R 777 ./images
sudo chmod -R 777 ./includes/languages/english/html_includes
sudo chmod -R 777 ./media
sudo chmod -R 777 ./pub
sudo chmod -R 777 ./admin/backups
sudo chmod -R 777 ./admin/images/graphs
sudo chmod 777 ./includes/configure.php
sudo chmod 777 ./admin/includes/configure.php

then
[http://localhost/zencart](http://localhost/zencart)

and follow the normal installation instruction on the screens.
untill I get

: Zen Cart&#8482; Setup - Finished
Congratulations!
You have successfully installed Zen Cart&#8482; on your system!

[http://localhost/zencart/](http://localhost/zencart/)
[http://localhost/zencart/index.php](http://localhost/zencart/index.php)
[http://localhost/zencart/admin/](http://localhost/zencart/admin/)

produced blank white pages.
I cannot install Zencart in LAMP_Ubuntu
==============================================================================
I found out later that Zencart 1.3.8 is not compatible with php 5.3,
and I am using UBUNTU 10.04 beta1, synaptic show php 5.3.2
so I need to update with patch from
[http://www.zen-cart.com/forum/showpost.php?p=804484&postcount=2](http://www.zen-cart.com/forum/showpost.php?p=804484&postcount=2)
I works now, don't know if I will face other problems yet, will report later.
===============================================================

Since I have done the following steps try to solve the Zencart malfunction,
before I found out the above php 5.3 and Zencart patch.
So I will leave them here until I found out if those following steps are need or not.
Gurus please help me too, I will try to do fresh install later when I have time.
============================================================================
I try [COLOR="Red"]blindly[/COLOR] with
[COLOR="Red"]https://help.ubuntu.com/community/ApacheMySQLPHP[/COLOR]

sudo cp /etc/apache2/sites-available/default /etc/apache2/sites-available/mysite 

gksudo gedit /etc/apache2/sites-available/mysite

sudo a2dissite default && sudo a2ensite mysite

sudo /etc/init.d/apache2 restart

To test the new site, create a file in /home/user/public_html/:

echo '<b>Hello! It is working!</b>' > /var/www/zencart/index.html

[http://localhost/zencart](http://localhost/zencart)
produce 
Hello! It is working!

What should I do next.
Thank you

---

### Post by cariboo on 2010-04-11
What do the error logs show you?

I also noted a mistake in these two lines:

> sudo mv /var/www/zencart/admin/includes/dist-configure.php /var/www/zencart/admin/includes/configure.php
sudo mv /var/www/zencart/includes/dist-configure.php /var/www/zencart/includes/configure.php

The command should be cp instead of mv, that way you still have the original files if you need them.

---

### Post by aimwin on 2010-04-11
> **cariboo907 said:**
> What do the error logs show you?

I also noted a mistake in these two lines:



The command should be cp instead of mv, that way you still have the original files if you need them.

Thank you, I have update them

---

### Post by flameash on 2010-12-05
thx for posting.

it was really helpful.

I got my phpmyadmin working by following your tutorial.

however now im stuck at the progress of downloading and installing zencart on my LAMP box. Could you help out?

My Lamp box is a local testing server which is a different machine from my pc (windows 7).
So i couldn't figure out how to download zen from lamp box..>< coz i hav no desktop on that machine

---

### Post by aimwin on 2010-12-17
> **flameash said:**
> thx for posting.

it was really helpful.

I got my phpmyadmin working by following your tutorial.

however now im stuck at the progress of downloading and installing zencart on my LAMP box. Could you help out?

My Lamp box is a local testing server which is a different machine from my pc (windows 7).
So i couldn't figure out how to download zen from lamp box..>< coz i hav no desktop on that machine

1. Download Zencart to your PC. 
(You should try to use UBUNTU instead of Windows 7 - more stable and almost no virus and spyware)
2. You use FTP client to upload the files to the server.
3. Use you Firefox to install Zencart by accessing your www server.

I hope that will work.

---

### Post by aimwin on 2012-07-08
I have successfully use the top instructions to install 
Xampp 1.7.7 
and 
Zencart 1.5
in 
Ubuntu 12.04 LTS (fully updated as 8/7/2012)
=================
So every thing works out of the box with no issues,

not like the older versions, that made me wrote the tutorial.

---

