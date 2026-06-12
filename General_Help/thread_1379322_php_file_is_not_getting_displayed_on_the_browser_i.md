---
title: "php file is not getting displayed on the browser instead it opens download dialog box"
date: 2010-01-12
forum: General Help
---

### Post by kracekumar on 2010-01-12
i have installed xampp 1.7.3 in ubuntu 9.10 and if i try to open the .php file in the browser it asks the me where to save the file and browser opens the source code rather than parsing the php file.

---

### Post by mörgæs on 2010-01-13
Do you get some kind of confirmation from Xampp, if you go to [http://localhost](http://localhost) in the browser?

---

### Post by kracekumar on 2010-01-15
[http://localhost](http://localhost)

shows the index page of the xampp.if i try to store anything in /opt it shows access denied and i am, admin.

---

### Post by mörgæs on 2010-01-16
So, I assume that Xammp is telling you, that it wants a certain file in /opt. 

You can store anything anywhere with sudo:

```
sudo cp ...from-path.../filename /opt/...to-path.../
```You could also give more rights to a certain folder within /opt, so the ordinary user is allowed to store files here.

---

### Post by kracekumar on 2010-01-18
i tried out saving in /opt and even after saving i am suffering from same problem . .  .

---

### Post by junapp on 2010-01-18
[http://ubuntuforums.org/showthread.php?t=926692](http://ubuntuforums.org/showthread.php?t=926692)

probably a matter of making sure php is installed, but also, be sure to close firefox/clear cache before trying again. Time after time, it seems to be that firefox tried once, it didn't work, user gets everything working, then firefox still doesn't work (but just needed to have cache cleared).

---

### Post by phillw on 2010-01-18
I'm assuming the A in Xammp is still apache 2 ? I only use LAMP.

If it is, then try ```
sudo /etc/init.d/apache2 restart
```

That will restart the Apache module - you should be able to view the files in FFox after that.

If FFox is still complaining, clear the FF cache Tools --> Clear Recent History, Select everything and have just an 'X' in the cache box, then select Clear Now.

Regards,

Phill.

---

### Post by s_ø on 2010-01-18
Why have you installed xampp?

apache is in synaptic and is more less ready to go. The same goes for PHP.
Check out the doc on AMP [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

But its probably a permission issue, the server should never be running as root, so you need to make a folder at make it readable by everyone. ex. /var/www

And then you need to goto /etc/apache2/sites-available/default
and add the document root and appropriate directives.

and then you need to enable the site.

check the /etc/apache2/apache2.conf for some of the directives to set.

---

### Post by kracekumar on 2010-01-18
**if type [http://localhost](http://localhost)**

[B]xampp page is not getting displayed,only below page is displaying.this html file is located in /var/www
[/B]

[B]
[/B]

**It works!**

 This is the default web page for this server.
 The web server software is running but no content has been added, yet.


in apache2 no default-sites directory is found. . . .

---

### Post by s_ø on 2010-01-19
I would seriously recomed you removed the xammp instalation.
I have just made a new instalitaion of LAMP using tasksel on my xubuntu notebook.
It took about 7min minutes and works out of the box with php support.

Did you compile xammp yourself?

To install LAMP after you have removed XAMMP use tasksel:
[https://help.ubuntu.com/community/Tasksel](https://help.ubuntu.com/community/Tasksel)

```
sudo tasksel
```Select LAMP server.

To test the installation and php support make a .php file in /var/www

```
sudo nano /var/www/test.php
```Wrap print/echo in some php tags, save and exit.

restart apache

```
sudo service apache2 restart
```goto localhost/test.php in your browser.

---

### Post by kracekumar on 2010-01-19
i have installed lamp and i tried to restart apache,below o/p  was displayed 

sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
 ... waiting apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName.,
still i m suffering same problem.

---

### Post by s_ø on 2010-01-20
Ok. Is apache running?
```
sudo service apache2 status
```Does [http://localhost](http://localhost) give you the It works! page?

Which page are you trying to access?

check if php module is enabled
```
sudo a2enmod php5
```If its enabled, check the php5.conf file:
```
sudo nano /etc/apache2/mods-enabled/php5.conf
```And post its contents.

Check dir.conf file
```
sudo nano /etc/apache2/mods-enabled/dir.conf
```It needs to look something like this:
<IfModule mod_dir.c>

          DirectoryIndex index.html index.cgi index.pl index.php index.xhtml in$

</IfModule>

---

### Post by nigel_nb on 2010-01-20
It looks like apache is not parsing your php code.  Does your browser ask if you want to download the php file instead of displaying it?

If Apache is not actually parsing the php after you restarted it, install libapache2-mod-php5. It may have been removed inadvertently by packages which need to run a different version of php.

You need to enable it with the following command
```
sudo a2enmod php5
```Now restart apache
```
sudo /etc/init.d/apache2 restart.
```If sudo a2enmod php5 returns "$ This module does not exist!", you should purge (not just remove) the libapache2-mod-php5 package and reinstall it.  Be sure to clear your browser's cache before testing your site again.

---

### Post by kracekumar on 2010-01-20
kracekumar# sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                          apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
 ... waiting apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                      [ OK ]

this is what i m getting .

---

### Post by wojox on 2010-01-20
Try putting 

```
ServerName localhost
```

in 

```
/etc/apache2/httpd.conf
```

---

### Post by kracekumar on 2010-01-20
content of php5 
<IfModule mod_php5.c>
  AddType application/x-httpd-php .php .phtml .php3
  AddType application/x-httpd-php-source .phps
</IfModule>

content of [http://localhost/](http://localhost/)
**It works!**

 This is the default web page for this server.
 The web server software is running but no content has been added, yet.


dir.conf content
sudo nano /etc/apache2/mods-enabled/dir.conf


yields
<IfModule mod_dir.c>

          DirectoryIndex index.html index.cgi index.pl index.php index.xhtml index.htm

</IfModule>

---

### Post by wojox on 2010-01-20
Did you download 

```
libapache2-mod-php5
```

---

### Post by kracekumar on 2010-01-20
php5 module is already enabled is displayed in terminal wen i used sudo a2enmod php5

---

### Post by s_ø on 2010-01-20
Ok. Its pretty clear that Apache is running and php5 is enabled.
What .php file are you testing and where is it?
How did you creat the file? what program?

Check your php.ini file to see if php is enabled.
```
sudo nano /etc/php5/apache2/php.ini
```Look for

;;;;;;;;;;;;;;;;;;;;
; Language Options ;
;;;;;;;;;;;;;;;;;;;;

; Enable the PHP scripting language engine under Apache.
engine = On


(Its the first setting after the introduction text)

If engine = Off change it to engine = On

---

### Post by nigel_nb on 2010-01-20
PHP is a server side scripting language, meaning, you should have your php file inside the 'www' directory of apache and open it from a browser with the address 'http://localhost/test.php' assuming the name of the file is test.php.  If the file is opened any other way, it won't be parsed by apache.

---

### Post by kracekumar on 2010-01-21
i owe a big thanks,finally apache is parsing my .php files.thanks a lot guys. . .:D

---

### Post by s_ø on 2010-01-22
your welcome.
how did you solve it?

---

### Post by kracekumar on 2010-01-22
i the installation and working of components was perfect ,i dint save my files in /www,i stored in some other folder and tried opening it.even now if i save it some other folder and try opening ,stil i face the prob and if use [http://localhost/test.php](http://localhost/test.php)

---

### Post by s_ø on 2010-01-22
Its a security issue. By only allowing apache to serve the files inside /var/www/ the risk is minimal. Imagine if you accidently gave everyone access to your home folder.
You can change the www directory to something else or add additional directories, start by looking at this documentation [https://help.ubuntu.com/9.10/serverguide/C/httpd.html](https://help.ubuntu.com/9.10/serverguide/C/httpd.html)

---

### Post by kracekumar on 2010-01-24
thank u.i need one more favour,can u give me links or some documents how to run,manage,secure web server.basically the information that a web master should posses.  . .

---

