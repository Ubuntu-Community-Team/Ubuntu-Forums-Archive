---
title: "Unable to install php5"
date: 2009-08-29
forum: General Help
---

### Post by rajatgarg on 2009-08-29
Hi,

I am trying to do the following - 
sudo aptitude install libapache2-mod-php5 php5 php5-common php5-curl php5-dev php5-gd php5-imagick php5-mcrypt php5-memcache php5-mhash php5-mysql php5-pspell php5-snmp php5-sqlite php5-xmlrpc php5-xsl

And I get this - 
The following packages have been kept back:
  apache2 apache2-mpm-prefork apache2-prefork-dev apache2-utils apache2.2-common
The following NEW packages will be installed:
  ghostscript libapache2-mod-php5 libcupsimage2 libgs8 libgtk2.0-0 libgtk2.0-bin libmagick10 librsvg2-2 libtiff4 libwmf0.2-7 php5 php5-common php5-curl
  php5-dev php5-gd php5-imagick php5-mcrypt php5-memcache php5-mhash php5-mysql php5-pspell php5-snmp php5-sqlite php5-xmlrpc php5-xsl
0 packages upgraded, 25 newly installed, 0 to remove and 6 not upgraded.
Need to get 3685kB/13.8MB of archives. After unpacking 46.1MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main libtiff4 3.8.2-7ubuntu3.1
  404 Not Found [IP: 91.189.88.31 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main libtiff4 3.8.2-7ubuntu3.1
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main php5-common 5.2.4-2ubuntu5.6
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main libapache2-mod-php5 5.2.4-2ubuntu5.6
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main php5 5.2.4-2ubuntu5.6
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main php5-curl 5.2.4-2ubuntu5.6
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main php5-dev 5.2.4-2ubuntu5.6
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main php5-gd 5.2.4-2ubuntu5.6
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main php5-mhash 5.2.4-2ubuntu5.6
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main php5-mysql 5.2.4-2ubuntu5.6
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main php5-pspell 5.2.4-2ubuntu5.6
  404 Not Found


My sudo nano /etc/apt/sources.list
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted universe


Any pointers will be much appreciated?

---

