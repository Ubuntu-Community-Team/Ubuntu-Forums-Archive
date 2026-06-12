---
title: "Apache, Php, MySQL, PhpMyAdmin help needed"
date: 2009-11-24
forum: General Help
---

### Post by osmorphyus on 2009-11-24
hello,

**THE TASK:**
install apache, php & mysql to continue drupal work on ubuntu.


**THE EXPERIENCE:**
have been able to configure xampp for windows in the past.


[B]
THE PROBLEMS:[/B]
i have been trying since last night to properly install and configure xampp to no avail.

to start with, i can no longer find the xampp/lampp package in Synaptic PM.


i am able to install Apache2, and it works.  it tells me, "its working".  ok, thats a start.

i tried to install PhpMyAdmin, and that completes, but i am not able to to configure it, so i am locked oput of it.  its asking for a password and since i wasnt able to configure it to begin with, i have no password for it.

P..MyAdmin installs to another directory rather than the apache, which installs to /var/www

i can enter [http://localhost/phpmyadmin](http://localhost/phpmyadmin) all night long just fine, but when i enter http://localhost/phpmyadmin/scripts/" ...etc... " i get a 404 error - i tried to go to the phpmyadmin setup.php this way.

[B]

WHAT ELSE HAVE I DONE?[/B]
being familiar with how a talkative minority on web forums are, of course i googled, and googled, and googled some more before i setup my ubuntu forums account to ask for help.  since ubuntu is about unity and community, i dont think ill have many of those kinds of people, however.


**WHAT IS INSTALLED AS OF YET?**
libapache2-mod-php5
apache2.2-common
apache2.2-bin
apache2.2-utils
apache2-mpm-prefork

php5-mysql
php5-gd
php5-common
libapache2-mod-php5
php5-mcrypt
libgtksourceview2.0-common
wwwconfig-common

phpmyadmin
mysql-client55.1
mysql-server
mysql-common
mysql-server-5.1
mysql-server-core5.1
libmysqlclient16
libdbd-mysql-perl
libqt4-sql-mysql
ryslog
libdbi-perl

if any of this is duplicated its because i searched it as follows, Apache, PHP, PhpMy on my synaptic and wrote it out as it was displayed.



if i can uninstall everything and have a good walkthru/tutorial on getting it all setup i would appreciate it.

---

### Post by osmorphyus on 2009-11-24
going to this url [http://localhost/phpmyadmin/setup/](http://localhost/phpmyadmin/setup/)

brings me to a login prompt, which of course i have no idea what the user/pass is.

i have tried root, with my system password, ther logged in user name with the system password, etc...

any tips?

---

### Post by osmorphyus on 2009-11-24
*bump*

---

### Post by phillw on 2009-11-24
> **osmorphyus said:**
> *bump*

With LAMP there are tooooo many variables as to why it does not work.

dump your MySQL databases and do a completely fresh install of the packages.

[http://www.howtoforge.com/ubuntu_lamp_for_newbies](http://www.howtoforge.com/ubuntu_lamp_for_newbies) 

Covers the installation.

Dumping your databases can be done by following this 

```
# mysqldump -u username -ppassword database_name > FILE.sql 
```FILE.sql will appear in whatever directory you are in when you issue the dump command - if you have several dbases to backup - do change the name-  leaving it as sql makes it easier for phpmyadmin

both MySQL and phpmyadmin can import databases backed up that way.

As in my Sig, my How-To's are currently not available :-\

Send me a Private Message if you need any more guidance on the backing up & re-installing of your databases.

Regards,

Phill.

---

### Post by BQAggie2006 on 2009-11-25
You can either follow the HowToForge article in the previous post (it's a good article, I've used it myself plenty of times) or you can run the following from a terminal:

```
sudo tasksel
```

Then select the LAMP server option and install

---

### Post by darkksyde on 2009-11-25
sudo tasksel - select lamp server
sudo apt-get install phpmyadmin

---

### Post by phillw on 2009-11-25
> **BQAggie2006 said:**
> You can either follow the HowToForge article in the previous post (it's a good article, I've used it myself plenty of times) or you can run the following from a terminal:

```
sudo tasksel
```Then select the LAMP server option and install

Of all things LAMP, the mysqldump and bhodi's articles on security are THE best things I've ever come accross. Ossecc is thoroughly enjoying 9.10, e-mails R Us ;-)  If, like me, you liked the Howto Forge one for LAMP, you'll love the mail server one -->  [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

Not for faint hearted, but, crikey, what a suite of protection he puts on :p

Regards,

Phill.

---

### Post by osmorphyus on 2009-11-25
thanks for the tips, guys.  ill update after i hammer these out.

---

### Post by osmorphyus on 2009-11-25
phill, thanks for the url you provided!

with it, i was able to assign a password for phpmyadmin, and everything seems to be working now.  thank you very much!  you eased a lot of frustration.  ithink that ubuntu should come with the steps in that URL embedded into it when it comes to setting up LAMP!

---

### Post by osmorphyus on 2009-12-01
hmm, this is odd, or is it?

second box:  trying to setup LAMP as follows thru the link that worked for me before, now i get a 404 when trying to go localhost/phpmyadmin


i did everything step by step.  any idea why this is happening to me?  if this is vague, trust me, the situation at hand is quite vague.

---

