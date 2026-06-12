---
title: "Zend Server CE on 10.04"
date: 2010-04-21
forum: General Help
---

### Post by postalservice14 on 2010-04-21
I can't seem to get Zend Server CE installed on my fairly fresh Ubuntu 10.04 installation.

Here is what I get from aptitude:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages are BROKEN:
  php-5.3-mysql-zend-server php-5.3-mysqli-zend-server 
  php-5.3-pdo-mysql-zend-server 
The following NEW packages will be installed:
  apache2-mpm-prefork{a} apache2-utils{a} apache2.2-bin{a} 
  apache2.2-common{a} help-zend-server-ce{a} libaio1{a} 
  libapache2-mod-php-5.3-zend-server{a} libapr1{a} libaprutil1{a} 
  libaprutil1-dbd-sqlite3{a} libaprutil1-ldap{a} 
  libframework1-zend-server{a} libicu36{a} libkrb53{a} libmcrypt4{a} 
  liboci-us-locales-zend{a} libpng3{a} libpq4{a} lighttpd-zend-server{a} 
  php-5.3-bcmath-zend-server{a} php-5.3-bz2-zend-server{a} 
  php-5.3-calendar-zend-server{a} 
  php-5.3-common-extensions-zend-server-ce{a} php-5.3-ctype-zend-server{a} 
  php-5.3-curl-zend-server{a} php-5.3-data-cache-zend-server{a} 
  php-5.3-debugger-zend-server{a} php-5.3-dev-zend-server{a} 
  php-5.3-exif-zend-server{a} php-5.3-fcgi-zend-server{a} 
  php-5.3-fileinfo-zend-server{a} php-5.3-ftp-zend-server{a} 
  php-5.3-gd-zend-server{a} php-5.3-gettext-zend-server{a} 
  php-5.3-gui-zend-server{a} php-5.3-imap-zend-server{a} 
  php-5.3-intl-zend-server{a} php-5.3-json-zend-server{a} 
  php-5.3-ldap-zend-server{a} php-5.3-mbstring-zend-server{a} 
  php-5.3-mcrypt-zend-server{a} php-5.3-oci8-zend-server{a} 
  php-5.3-optimizer-plus-zend-server{a} php-5.3-pdo-oci-zend-server{a} 
  php-5.3-pdo-pgsql-zend-server{a} php-5.3-pgsql-zend-server{a} 
  php-5.3-phar-zend-server{a} php-5.3-posix-zend-server{a} 
  php-5.3-soap-zend-server{a} php-5.3-sockets-zend-server{a} 
  php-5.3-sqlite-zend-server{a} php-5.3-tidy-zend-server{a} 
  php-5.3-tokenizer-zend-server{a} php-5.3-xmlreader-zend-server{a} 
  php-5.3-xmlwriter-zend-server{a} php-5.3-xsl-zend-server{a} 
  php-5.3-zem-zend-server{a} php-5.3-zend-extensions-ce{a} 
  php-5.3-zendutils-zend-server{a} php-5.3-zip-zend-server{a} sqlite{a} 
  zend-base{a} zend-server-ce-php-5.3 zend-server-doc{a} 
  zend-server-framework{a} 
0 packages upgraded, 68 newly installed, 0 to remove and 0 not upgraded.
Need to get 55.3MB of archives. After unpacking 214MB will be used.
The following packages have unmet dependencies:
  php-5.3-mysqli-zend-server: Depends: libmysqlclient15off (>= 5.0.27-1) which is a virtual package.
  php-5.3-pdo-mysql-zend-server: Depends: libmysqlclient15off (>= 5.0.27-1) which is a virtual package.
  php-5.3-mysql-zend-server: Depends: libmysqlclient15off (>= 5.0.27-1) which is a virtual package.
The following actions will resolve these dependencies:

Keep the following packages at their current version:
help-zend-server-ce [Not Installed]
php-5.3-common-extensions-zend-server-ce [Not Installed]
php-5.3-mysql-zend-server [Not Installed]
php-5.3-mysqli-zend-server [Not Installed]
php-5.3-pdo-mysql-zend-server [Not Installed]
zend-server-ce-php-5.3 [Not Installed]

Score is -9836

Accept this solution? [Y/n/q/?] 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] 
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

Zend Server was successfully installed.

```

But it is NOT successfully installed. :-)

Thanks,

John

---

### Post by greg606 on 2010-04-21
Have you found the solution yet?

---

### Post by postalservice14 on 2010-04-21
Nope

---

### Post by cliffordh on 2010-04-22
The required package has been deleted namely:
https://launchpad.net/ubuntu/lucid/{$arch}/libmysqlclient15off

but if you install the one from karmic then ZendServer will install correctly ;)

This will probably require a bug report against the ZendServer package, as I believe the package is now
https://launchpad.net/ubuntu/lucid/{$arch}/libmysqlclient16

HTH

---

### Post by chirimoya on 2010-04-23
I have the same issue, but i don't know how to install the libmysqlclient15off of karmic.

Can anybody help me?

thx
chiri

---

### Post by Yggdrasil42 on 2010-04-27
Download the package for your platform from [http://packages.ubuntu.com/karmic/libmysqlclient15off]("http://packages.ubuntu.com/karmic/libmysqlclient15off") and install it manually.
According to dpkg this package doesn't conflict with any in 10.04, so it shouldn't cause any problems.

As an example, I took the following steps. Doublecheck them for your platform and to understand what they do!

[LIST=1]
[*]Log into your machine as a user with sudo privileges.
[*][FONT="Courier New"]wget [http://nl.archive.ubuntu.com/ubuntu/pool/universe/m/mysql-dfsg-5.0/libmysqlclient15off_5.1.30really5.0.83-0ubuntu3_amd64.deb](http://nl.archive.ubuntu.com/ubuntu/pool/universe/m/mysql-dfsg-5.0/libmysqlclient15off_5.1.30really5.0.83-0ubuntu3_amd64.deb)[/FONT]
[*][FONT="Courier New"]sudo dpkg -i libmysqlclient15off_5.1.30really5.0.83-0ubuntu3_amd64.deb[/FONT]
[*][FONT="Courier New"]sudo aptitude install zend-server-ce-php-5.3[/FONT]
[*][optional] [FONT="Courier New"]sudo aptitude markauto libmysqlclient15off[/FONT]
[/LIST]

The last step is optional. It marks the libmysqlclient package as automatically installed so it will not linger on your system when Zend updates the dependencies of Zend Server. It will be automatically uninstalled if no other package depends on it any more.

---

### Post by utherwayn on 2010-04-30
Thanks for the help too :)

---

### Post by bibleman on 2010-05-11
Installing the package from karmic did the trick. Did anyone find out why it was removed from Lucid?

---

### Post by tuxar on 2010-05-14
Thank you, the above steps works for me.

---

### Post by giuliano1969 on 2010-05-26
> **bibleman said:**
> Installing the package from karmic did the trick. Did anyone find out why it was removed from Lucid?

In karmic there were libmysqlclient15 and libmysqlclient16.

I think in lucid they simply kept the last one.
The bug is in the Zend deb package, that should be update to the LTS version of Ubuntu

---

### Post by Jon-EM on 2010-06-06
> **Yggdrasil42 said:**
> 
[LIST=1]
[*]Log into your machine as a user with sudo privileges.
[*][FONT="Courier New"]wget [http://nl.archive.ubuntu.com/ubuntu/pool/universe/m/mysql-dfsg-5.0/libmysqlclient15off_5.1.30really5.0.83-0ubuntu3_amd64.deb](http://nl.archive.ubuntu.com/ubuntu/pool/universe/m/mysql-dfsg-5.0/libmysqlclient15off_5.1.30really5.0.83-0ubuntu3_amd64.deb)[/FONT]
[*][FONT="Courier New"]sudo dpkg -i libmysqlclient15off_5.1.30really5.0.83-0ubuntu3_amd64.deb[/FONT]
[*][FONT="Courier New"]sudo aptitude install zend-server-ce-php-5.3[/FONT]
[*][optional] [FONT="Courier New"]sudo aptitude markauto libmysqlclient15off[/FONT]
[/LIST]


I have followed this step for 10.04 and I can't install zend-server-ce-php-5.3.

$ dpkg --get-selections | grep libmysql
libmysqlclient15off				install
libmysqlclient16				install

# aptitude install zend-server-ce-php-5.3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Couldn't find any package whose name or description matched "zend-server-ce-php-5.3"
Couldn't find any package whose name or description matched "zend-server-ce-php-5.3"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done


In my /etc/apt/sources-list I have this listed.
**deb [http://repos.zend.com/deb/ce](http://repos.zend.com/deb/ce) ce non-free** 

When I try to follow the instructions from Zend to install, I get a libkrb53 error if I use either apt-get or aptitude install.

$ apt-get install zend-ce php5-common-extensions-zend-ce php-imap-zend-ce
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  php-imap-zend-ce: Depends: libkrb53 (>= 1.4.2) but it is not installable
  php5-common-extensions-zend-ce: Depends: php-pdo-pgsql-zend-ce but it is not going to be installed
                                  Depends: php-pgsql-zend-ce but it is not going to be installed
E: Broken packages

$ aptitude install zend-ce
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages are BROKEN:
  libpq4 php-imap-zend-ce 
The following NEW packages will be installed:
  libaio1{a} libframework1-zend-ce{a} libicu36{a} libmhash2{a} 
  liboci-zend{a} libpng3{a} lighttpd-zend-ce{a} php-bcmath-zend-ce{a} 
  php-bz2-zend-ce{a} php-calendar-zend-ce{a} php-ctype-zend-ce{a} 
  php-curl-zend-ce{a} php-data-cache-zend-ce{a} php-debugger-zend-ce{a} 
  php-exif-zend-ce{a} php-fcgi-zend-ce{a} php-ftp-zend-ce{a} 
  php-gd-zend-ce{a} php-gettext-zend-ce{a} php-intl-zend-ce{a} 
  php-json-zend-ce{a} php-ldap-zend-ce{a} php-mbstring-zend-ce{a} 
  php-mcrypt-zend-ce{a} php-mhash-zend-ce{a} php-mime-magic-zend-ce{a} 
  php-mysqli-zend-ce{a} php-oci8-zend-ce{a} php-optimizer-plus-zend-ce{a} 
  php-pdo-mysql-zend-ce{a} php-pdo-oci-zend-ce{a} php-pdo-pgsql-zend-ce{a} 
  php-pgsql-zend-ce{a} php-posix-zend-ce{a} php-soap-zend-ce{a} 
  php-sockets-zend-ce{a} php-sqlite-zend-ce{a} php-tidy-zend-ce{a} 
  php-tokenizer-zend-ce{a} php-xmlreader-zend-ce{a} 
  php-xmlwriter-zend-ce{a} php-xsl-zend-ce{a} php-zem-zend-ce{a} 
  php-zendutils-zend-ce{a} php-zip-zend-ce{a} 
  php5-common-extensions-zend-ce{a} sqlite{a} zend-ce zend-ce-doc{a} 
  zend-extensions-ce{a} zend-framework-ce{a} zend-gui-ce{a} 
0 packages upgraded, 54 newly installed, 0 to remove and 4 not upgraded.
Need to get 40.5MB of archives. After unpacking 158MB will be used.
The following packages have unmet dependencies:
  php-imap-zend-ce: Depends: libkrb53 (>= 1.4.2) which is a virtual package.
  libpq4: Depends: libkrb53 (>= 1.4.2) which is a virtual package.
The following actions will resolve these dependencies:

Keep the following packages at their current version:
libpq4 [Not Installed]
php-imap-zend-ce [Not Installed]
php-pdo-pgsql-zend-ce [Not Installed]
php-pgsql-zend-ce [Not Installed]
php5-common-extensions-zend-ce [Not Installed]
zend-ce [Not Installed]

Score is -9836


Can someone help direct me the right direction to install Zend CE?

---

### Post by Jon-EM on 2010-06-06
I have posted a similar question in the Zend forums:  [http://forums.zend.com/viewtopic.php?f=44&t=6641]("http://forums.zend.com/viewtopic.php?f=44&t=6641") so it is possible that someone may respond to this topic, or the one in Zend.

Regardless, if I get an answer and/or figure out how to fix this, I will update the steps that I needed to take to fix the issues.

---

### Post by alpesh76 on 2011-12-27
> **Yggdrasil42 said:**
> Download the package for your platform from [http://packages.ubuntu.com/karmic/libmysqlclient15off](http://packages.ubuntu.com/karmic/libmysqlclient15off) and install it manually.
According to dpkg this package doesn't conflict with any in 10.04, so it shouldn't cause any problems.

As an example, I took the following steps. Doublecheck them for your platform and to understand what they do!

[LIST=1]
[*]Log into your machine as a user with sudo privileges.
[*][FONT=Courier New]wget [http://nl.archive.ubuntu.com/ubuntu/pool/universe/m/mysql-dfsg-5.0/libmysqlclient15off_5.1.30really5.0.83-0ubuntu3_amd64.deb](http://nl.archive.ubuntu.com/ubuntu/pool/universe/m/mysql-dfsg-5.0/libmysqlclient15off_5.1.30really5.0.83-0ubuntu3_amd64.deb)[/FONT]
[*][FONT=Courier New]sudo dpkg -i libmysqlclient15off_5.1.30really5.0.83-0ubuntu3_amd64.deb[/FONT]
[*][FONT=Courier New]sudo aptitude install zend-server-ce-php-5.3[/FONT]
[*][optional] [FONT=Courier New]sudo aptitude markauto libmysqlclient15off[/FONT]
[/LIST]

The last step is optional. It marks the libmysqlclient package as automatically installed so it will not linger on your system when Zend updates the dependencies of Zend Server. It will be automatically uninstalled if no other package depends on it any more.

i have ubuntu 11.10 

i tried ur instruction but it gives following error

wget [http://nl.archive.ubuntu.com/ubuntu/pool/universe/m/mysql-dfsg-5.0/libmysqlclient15off_5.1.30really5.0.83-0ubuntu3_amd64.deb](http://nl.archive.ubuntu.com/ubuntu/pool/universe/m/mysql-dfsg-5.0/libmysqlclient15off_5.1.30really5.0.83-0ubuntu3_amd64.deb)
--2011-12-27 06:51:51--  [http://nl.archive.ubuntu.com/ubuntu/pool/universe/m/mysql-dfsg-5.0/libmysqlclient15off_5.1.30really5.0.83-0ubuntu3_amd64.deb](http://nl.archive.ubuntu.com/ubuntu/pool/universe/m/mysql-dfsg-5.0/libmysqlclient15off_5.1.30really5.0.83-0ubuntu3_amd64.deb)
Resolving nl.archive.ubuntu.com... 213.136.29.211, 2001:7b8:3:37::21:2
Connecting to nl.archive.ubuntu.com|213.136.29.211|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2011-12-27 06:51:52 ERROR 404: Not Found.

---

