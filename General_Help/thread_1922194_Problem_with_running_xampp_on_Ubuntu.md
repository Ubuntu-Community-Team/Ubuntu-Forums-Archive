---
title: "Problem with running xampp on Ubuntu"
date: 2012-02-08
forum: General Help
---

### Post by emptycoder on 2012-02-08
Hello everyone.
I wanted to run run WordPress in my localhost on Ubuntu 11.10 x64 using xampp, and every time I try to use it I get this error:

error establishing a database connection

Here what I did so far,
I downloaded xampp-linux-1.7.7.tar.gz

extract xampp and install it
```
$ sudo tar xvfz xampp-linux-1.7.1.tar.gz -C /opt
```Then launch xampp and stop it via Terminal

```
sudo /opt/lampp/lampp start
``````
sudo /opt/lampp/lampp stop
```Then I headed to Worpress file and renamed file wp-config-sample.php to be wp-config.php
Then editing the file itself, wp-config.php

define(‘DB_NAME’, ‘wordpress’); (I named my database wordpress)



 /** MySQL database username */ (my username)


 define(‘DB_USER’, ‘root’); (as default)



 /** MySQL database password */



 define(‘DB_PASSWORD’, ”);  (added my password)


 /** MySQL hostname */ (as default)


 define(‘DB_HOST’, ‘localhost’); (as default)


After that I created a database named wordpress on phpmyadmin.


But every time I try to launch [http://localhost/wordpress](http://localhost/wordpress) it tells me there's an error and it can't connect to the database


error establishing a database connection


I searched all the net for a solution but all posts say that error means there's something wrong with wp-config.php, I don't know what I did wrong, everything seems to me fine.


Please let me know if I forgot or did something wrong.
Thanks.

---

### Post by Lars Noodén on 2012-02-08
I see that there is a package for [Wordpress](apt://wordpress) already in the package repositories.  Where are all these XAMPP problems coming from?  Was there an article or something?

The first thing to do is remove [font=Courier New]/opt/lampp[/font] and then use the package manager to install the pieces you need.  That does several good things, starting with allowing you to automatically manage versions, dependencies and security updates.  

You can use Synaptic, the Software Center or [apt-get](http://manpages.ubuntu.com/manpages/oneiric/en/man8/apt-get.8.html) to install the packages apache2 and php5.  Perl comes built in with any version of Ubuntu so it does not need to be installed.  MySQL is split into several packages (mysql-server, mysql-client, php5-mysql, libdbd-mysql-perl, etc.) but you won't need them until you start to program your own CMS or install one that someone else has built.

Some would claim that the package manager is the [single biggest advancement that Linux has brought to the industry](http://ianmurdock.com/solaris/how-package-management-changed-everything/).  

Here is some good reading on installing software in Ubuntu:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

Let the package manager do the work so that you can spend time working with and using the programs.

---

### Post by emptycoder on 2012-02-12
Thanks a lot!;)

---

