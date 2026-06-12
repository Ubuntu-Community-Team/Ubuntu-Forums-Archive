---
title: "Installing LAMP"
date: 2010-07-19
forum: General Help
---

### Post by youngros on 2010-07-19
Windows XP Pro, VMware and Kubuntu as the guest

Tried several different ways of adding LAMP server, via the Konsole and also via Synatpic and although I can get into localhost and it says "it works" doesn't actually take me to a list which includes the links to Apache and phpmyadmin like some tuts show. Also if I make the php test page that also works, but I cannot get phpmyadmin to work.
When I look in the var/www folder there are only 3 files there and not the apache2 and phpmyadmin folders as shown on a lullabot tutorial.

Any ideas as to what is going wrong please? Thanks in advance.

---

### Post by lukeiamyourfather on 2010-07-19
If you install LAMP, its simply that. **L**inux, **A**pache, **M**ySQL, and **P**HP. phpMyAdmin has nothing to do with LAMP, so if you want to use it you'll need to install it manually. You might be confusing LAMP with XAMPP (which comes with phpMyAdmin). Cheers!

---

### Post by betrunkenaffe on 2010-07-19
I just installed it last night on a Debian Lenny server I set up, used these for commands

[http://www.howtoforge.com/ubuntu_debian_lamp_server](http://www.howtoforge.com/ubuntu_debian_lamp_server)

The "It Works" is the default page now.

If you don't have phpmyadmin in /var/www then it's because you didn't install

```
apt-get install phpmyadmin
```

---

### Post by youngros on 2010-07-19
I installed phpmyadmin 
Not confusing it with XAMPP
I'm a WAMP user as well

How can I purge the Apache/Mysql.Php and Phpmyadmin from my system to start again

Have followed all the instructions on several sites including the above but no joy

---

### Post by etdsbastar on 2010-07-19
> **youngros said:**
> I installed phpmyadmin 
Not confusing it with XAMPP
I'm a WAMP user as well

How can I purge the Apache/Mysql.Php and Phpmyadmin from my system to start again

Have followed all the instructions on several sites including the above but no joy


[LIST=1]
[*]Open Synaptic.
[*]Goto Edit -> Mark Packages By Task (See the screenshot)
[*]Uncheck the LAMP Server and then press ok to close the window
[*]Now press the apply button to apply the uninstallation changes.
[*]Reinstall using the same process by checking the option in step-3 and repeating all after.
[/LIST]
Hope this helps.

---

### Post by youngros on 2010-07-19
The LAMP server is greyed out so can't be unchecked.
I also need to delete the files in var/www how do I do that?

---

### Post by etdsbastar on 2010-07-19
> **youngros said:**
> The LAMP server is greyed out so can't be unchecked.
I also need to delete the files in var/www how do I do that?

```
sudo apt-get purge apache2 php5 mysql-server-5.0 phpmyadmin
```

Try this.

---

### Post by rubylaser on 2010-07-19
I'd just use the terminal to remove your non-functional packages
```
sudo apt-get remove --purge mysql* apache* phpmyadmin php*
```

Then, I'd re-install what you need...
```
apt-get update && sudo apt-get install apache2 mysql-server php5 libapache2-mod-php5 php5-xsl php5-gd php-pear libapache2-mod-auth-mysql php5-mysql
```

Then restart Apache
```
/etc/init.d/apache2 restart
```

Hope that works for you.

---

### Post by NUboon2Age on 2010-07-19
> **youngros said:**
> The LAMP server is greyed out so can't be unchecked.
I also need to delete the files in var/www how do I do that?


I'm not sure about the greyed out part -- I wonder if that means Synaptic considers the package broken.  To see if that's the case use the filter for broken packages (there's also a menu item under edit for 'Fix Broken Packages).  

After you get it to an ungreyed state you can use the Synaptic 'Remove Completely' (which equals apt-get purge).

As far as /var/www was that manually installed or automatically created by an apt-get or Synaptic operation?  If it was automatically created then the 'Remove Completely' should purge that automatically too.

---

### Post by etdsbastar on 2010-07-19
**To Re-Install LAMP server for local web development, do the following: **

 This will install Apache2, PHP5, MySql5, and PHPMyAdmin
Firstly, type the following command at the console: 
 ```
apt-get update
``` This will retrieve new lists of packages
Next type:  
 ```
sudo apt-get install apache2 php5 mysql-server-5.0 phpmyadmin
``` This will install all the necessary applications. You may be prompted to decide on a MySQL root password (set one if you want), and to configure PHPMyAdmin (select apache2 as the server type). After this is complete, we need to perform some minor configuration to get PHPMyAdmin working. Type: 
   sudo gedit /etc/apache2/apache2.conf
Scroll right to the bottom of the file that opens, and add: 
 ```
# Enable PHPMyAdmin
Include /etc/phpmyadmin/apache.conf
```Now, edit your Apache.conf file as below:
```
sudo gedit /etc/apache2/apache2.conf
```Add the line on the last of the opened file:
```
ServerName localhost
```Save the file and then exit.
Now save, exit, and type: 
 ```
sudo /etc/init.d/apache2 restart
``` Everything should now be configured - go to [http://127.0.0.1]("http://127.0.0.1/") for webpages, and [http://127.0.0.1/phpmyadmin](http://127.0.0.1/phpmyadmin) for database administration. The webroot is located in /var/www/ by default. This is not particularly useful, as we do not have write access to this directory. So you can change it by following:
```
sudo gedit /etc/apache2/httpd.conf
```In the resulting file (which may well be empty), add the definition for your host! My username is 'etdsbastar', and I want my webpages to be served from a directory named 'www' in my home, so I would add: 
 ```
<VirtualHost *>
 ServerName localhost
 DocumentRoot /home/etdsbastar/www
</Virtualhost>
``` where localhost is the name of the new virtual site (it must match the  above entry in your conf file). 
After this, you need to restart apache so it can load these new  configuration file entries. 
 ```
sudo /etc/init.d/apache2 restart
```

---

### Post by rubylaser on 2010-07-19
etdsbastar, that's a good description for youngros to follow.  I would suggest that you leave you web apps in /var/www they go there by default, because they're owned by www-data:www-data (the Apache user).  If you need privileges, you just need to add your user to the www-data group like this.

```
usermod -a -G www-data rubylaser
```

Also, if you're going to host multiple apps, using Apaches sites-enabled to make a different file for each vhost makes making changes and additions much safer and easier.  This is just a personal preference to make administration easier and more consistent across multiple servers.

---

### Post by etdsbastar on 2010-07-19
> **rubylaser said:**
> etdsbastar, that's a good description for youngros to follow.  I would suggest that you leave you web apps in /var/www the go there by default, because they're owned by www-data:www-data (the Apache user).  If you need privileges, you just need to add your user to the www-data group like this.

```
usermod -a -G www-data rubylaser
```Also, if you're going to host multiple apps, using Apaches sites-enabled to make a different file for each vhost makes making changes and additions much safer and easier.  This is just a personal preference to make administration easier and more consistent across multiple servers.

Thanks ruby for your description and suggestion.

---

### Post by youngros on 2010-07-19
I've run the purge so hopefully that is everything removed, but before I reinstall a couple of things I want to make sure of.

In the var/www folder are three files the index.html file with "it works" on a testphp.php file and a backup of the same file presume one was there as default as I created one to test php the first time.

Should the Apache2 folder still be in the etc folder even though I have removed Apache, as this still has httpd.conf files that I altered following some tutorial, how do I clear these out.

Thanks for the help so far.

---

### Post by etdsbastar on 2010-07-19
> **youngros said:**
> I've run the purge so hopefully that is everything removed, but before I reinstall a couple of things I want to make sure of.

In the var/www folder are three files the index.html file with "it works" on a testphp.php file and a backup of the same file presume one was there as default as I created one to test php the first time.

Should the Apache2 folder still be in the etc folder even though I have removed Apache, as this still has httpd.conf files that I altered following some tutorial, how do I clear these out.

Thanks for the help so far.

Just purge the files and then recreate them as necessary and regarding the httpd.conf file, you can make it again, we will help you... This is for the UBUNTU FORUM COMMUNITY is... Don't worry, nothing goes wrong. If still in doubt, make a backup of those files before doing anything.

---

### Post by rubylaser on 2010-07-19
You could try this first.
```
sudo apt-get remove --purge apache2-common apache2-mpm-prefork apache2-utils ssl-cert
```

And, if they're still in /etc/ you can remove them easily by doing this.
```
sudo rm -rf /etc/apache2
```
That will recursively remove apache2 and all of it's subdirectories.

Then, re-install the packages as was shown previously.

---

### Post by youngros on 2010-07-19
Unfortunately ran into a load of errors so now run a purge and will try again

seems I have complete failure of Kubuntu now just get a black page with login and nothing else

If I can't get this to work there is no way I can wipe windows off

---

### Post by youngros on 2010-07-19
Re installed Kubuntu

Which would be best to use the Konsole or Synaptic

I notice there are differences in what rublaser and etdsbastar suggest installing, hard to know what to install but the intention is to run Drupal as I already have that on WAMP.

---

### Post by etdsbastar on 2010-07-19
> **youngros said:**
> Re installed Kubuntu

Which would be best to use the Konsole or Synaptic

I notice there are differences in what rublaser and etdsbastar suggest installing, hard to know what to install but the intention is to run Drupal as I already have that on WAMP.

no problem drupal or joomla or a personal php file, i suggest you to use the terminal mode which i explained before. It is working fine for me, running on local server too...

Waiting for your smiling face dear... do it quickly...

---

### Post by youngros on 2010-07-19
Well we are getting there, I think some previous tutorials may have been misleading on which files to edit with what.

Anyway I got the "It works" page from [http://localhost/](http://localhost/) but get page not found if I follow this bit even when changing my user name.
[FONT=monospace]
[/FONT]<VirtualHost *>
 ServerName localhost
 DocumentRoot /home/etdsbastar/www
</Virtualhhost> 
I also get the phpmyadmin page when putting in [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/) but then became unstuck over user name and password. Not sure what went wrong there, always have trouble with these passwords and thought I hadn't set any. So how do I reset or find out what I used?

Thanks so much for the help so far on this will keep this on file as it has got me much further than some tutorials.

---

### Post by etdsbastar on 2010-07-19
> **youngros said:**
> Well we are getting there, I think some previous tutorials may have been misleading on which files to edit with what.

Anyway I got the "It works" page from [http://localhost/](http://localhost/) but get page not found if I follow this bit even when changing my user name.
[FONT=monospace]
[/FONT]<VirtualHost *>
 ServerName localhost
 DocumentRoot /home/etdsbastar/www
</Virtualhhost> 
I also get the phpmyadmin page when putting in [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/) but then became unstuck over user name and password. Not sure what went wrong there, always have trouble with these passwords and thought I hadn't set any. So how do I reset or find out what I used?

Thanks so much for the help so far on this will keep this on file as it has got me much further than some tutorials.

**First of all lets solve phpmyadmin problem,**
type the username as root and the password is one you typed when installing phpmyadmin, it must have been asked with a password, if you pressed enter there then no password for root, type root on username and press enter.

**Second making localhost perfect:**
Check if the folder www exists in your home folder if yes then check the permissions and make it to 777 i mean writable to everyone, for this period. then place a file index.php or index.html with some html/php content in it. then try [http://localhost/](http://localhost/)

Check it and then revert here.

---

### Post by youngros on 2010-07-19
no joy with phpmyadmin i don't think I did set a password but it won't allow you not to use one to login. I know we have to have passwords but they can get very confusing unnles you use the same one all the time.

---

### Post by youngros on 2010-07-19
The www folder is there with an index.html file in it that says "It Works" this worked until I change the bit about VirtualHost. I don't see how I can change the permissions though.

---

### Post by rubylaser on 2010-07-19
Okay, I'll be happy to help you login to phpmyadmin.  It's wanting one of your MySQL users to authenticate, and since you don't know the root password, let's just reset it.

First stop MySQL
```
/etc/init.d/mysql stop
```

Then restart MySQL and skip the grant tables
```
/usr/local/mysql/bin/mysqld_safe --skip-grant-tables &
```

It should output something like this...
```
fileserver ~: mysqld_safe --skip-grant-tables &
[1] 6435
```

After that write down the process number, in the example case it's 6435, and then press enter.

MySQL should start up for you. Now you should be able to connect to MySQL without a password.
```
mysql --user=root mysql
```

Finally set a new password...
```
UPDATE user SET Password=PASSWORD('new-password-here') WHERE user='root';
flush privileges;
exit;
```

Kill the mysqld_safe process and restart MySQL
```
kill -9 6435
``` This is the process number you wrote down from earlier.
```
/etc/init.d/mysql restart
```

Finally, you should be able to connect to [http://localhost/phpmyadmin](http://localhost/phpmyadmin) with user root, and the password you just defined.

---

### Post by etdsbastar on 2010-07-20
> **youngros said:**
> The www folder is there with an index.html file in it that says "It Works" this worked until I change the bit about VirtualHost. I don't see how I can change the permissions though.

For the permissions, dear we have told you before to add your username to www-data group, you will automatically get proper permissions for that folder.

---

### Post by youngros on 2010-07-20
I removed the bit about Virtual Host which now gives me "It Works" back on localhost, but I also get the same message when I add phpmyadmin!! Might be easier to purge again and restart it.

---

### Post by youngros on 2010-07-20
Done the purge and reinstalled, if nothing else it gets me more familiar with the console!!

This time I set the passwords and can now get the localhost and login to phpmyadmin. for this morning that will be it. Later on I will sort out the permissions and Virtual Host.

I am used to my www folder in WAMP holding all my folders for different websites so presume this is much the same thing.

Got to be a good day.

---

### Post by etdsbastar on 2010-07-20
> **youngros said:**
> Done the purge and reinstalled, if nothing else it gets me more familiar with the console!!

This time I set the passwords and can now get the localhost and login to phpmyadmin. for this morning that will be it. Later on I will sort out the permissions and Virtual Host.

I am used to my www folder in WAMP holding all my folders for different websites so presume this is much the same thing.

Got to be a good day.

But remember the password what you are using.

---

### Post by youngros on 2010-07-20
Something else going on here and don't know if they are connected but now Kubuntu hangs after the login screen and it can take a couple of attempts at restarting VMware. So back to square one until I find the solution to that problem.

---

### Post by youngros on 2010-07-21
I have now installed Ubuntu and this seems to be OK so far. Localhost and phpmyadmin are all working.

However if I type [FONT=monospace]

[/FONT]usermod -a -G www-data myusername
I get the error of usermod: cannot lock /etc/passwd; try again later

need to put sudo on the front to get root privileges!!

---

### Post by annavlad on 2010-08-03
try here [http://www.edonline.ro/mod/resource/view.php?id=69](http://www.edonline.ro/mod/resource/view.php?id=69)

---

