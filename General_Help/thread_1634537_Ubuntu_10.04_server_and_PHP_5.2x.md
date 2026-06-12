---
title: "Ubuntu 10.04 server and PHP 5.2x"
date: 2010-11-30
forum: General Help
---

### Post by KayakJim on 2010-11-30
I have followed the many posts for downgrading to PHP 5.2x on Ubuntu 10.04 but for some reason it isn't working for me.

I have created an /etc/apt/sources.d/karmic.list file that contains:
```


deb http://us.archive.ubuntu.com/ubuntu/ karmic main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic main restricted

deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted

deb http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe

deb http://us.archive.ubuntu.com/ubuntu/ karmic multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates multiverse

deb http://security.ubuntu.com/ubuntu karmic-security main restricted
deb-src http://security.ubuntu.com/ubuntu karmic-security main restricted
deb http://security.ubuntu.com/ubuntu karmic-security universe
deb-src http://security.ubuntu.com/ubuntu karmic-security universe
deb http://security.ubuntu.com/ubuntu karmic-security multiverse
deb-src http://security.ubuntu.com/ubuntu karmic-security multiverse

```

I have also created an /etc/apt/preferences.d/php file that contains:

```

Package: php5
Pin: release a=karmic
Pin-Priority: 991

Package: php5-adodb
Pin: release a=karmic
Pin-Priority: 991

Package: php5-auth-pam
Pin: release a=karmic
Pin-Priority: 991

Package: php5-exactimage
Pin: release a=karmic
Pin-Priority: 991

Package: php5-ffmpeg
Pin: release a=karmic
Pin-Priority: 991

Package: php5-geoip
Pin: release a=karmic
Pin-Priority: 991

Package: php5-gpib
Pin: release a=karmic
Pin-Priority: 991

Package: php5-idn
Pin: release a=karmic
Pin-Priority: 991

Package: php5-imagick
Pin: release a=karmic
Pin-Priority: 991

Package: php5-imap
Pin: release a=karmic
Pin-Priority: 991

Package: php5-interbase
Pin: release a=karmic
Pin-Priority: 991

Package: php5-lasso
Pin: release a=karmic
Pin-Priority: 991

Package: php5-librdf
Pin: release a=karmic
Pin-Priority: 991

Package: php5-mapscript
Pin: release a=karmic
Pin-Priority: 991

Package: php5-mcrypt
Pin: release a=karmic
Pin-Priority: 991
Package: php5-memcache
Pin: release a=karmic
Pin-Priority: 991

Package: php5-memcached
Pin: release a=karmic
Pin-Priority: 991

Package: php5-ming
Pin: release a=karmic
Pin-Priority: 991

Package: php5-ps
Pin: release a=karmic
Pin-Priority: 991

Package: php5-radius
Pin: release a=karmic
Pin-Priority: 991

Package: php5-remctl
Pin: release a=karmic
Pin-Priority: 991

Package: php5-sasl
Pin: release a=karmic
Pin-Priority: 991

Package: php5-sqlrelay
Pin: release a=karmic
Pin-Priority: 991

Package: php5-suhosin
Pin: release a=karmic
Pin-Priority: 991

Package: php5-svn
Pin: release a=karmic
Pin-Priority: 991

Package: php5-symfony1.0
Pin: release a=karmic
Pin-Priority: 991

Package: php5-uuid
Pin: release a=karmic
Pin-Priority: 991

Package: php5-xapian
Pin: release a=karmic
Pin-Priority: 991

Package: php5-xcache
Pin: release a=karmic
Pin-Priority: 991

Package: php5-xdebug
Pin: release a=karmic
Pin-Priority: 991

Package: php5-cgi
Pin: release a=karmic
Pin-Priority: 991

Package: php5-cli
Pin: release a=karmic
Pin-Priority: 991

Package: php5-common
Pin: release a=karmic
Pin-Priority: 991

Package: php5-curl
Pin: release a=karmic
Pin-Priority: 991

Package: php5-dbg
Pin: release a=karmic
Pin-Priority: 991

Package: php5-dev
Pin: release a=karmic
Pin-Priority: 991

Package: php5-gd
Pin: release a=karmic
Pin-Priority: 991

Package: php5-gmp
Pin: release a=karmic
Pin-Priority: 991

Package: php5-ldap
Pin: release a=karmic
Pin-Priority: 991

Package: php5-mysql
Pin: release a=karmic
Pin-Priority: 991

Package: php5-odbc
Pin: release a=karmic
Pin-Priority: 991

Package: php5-pgsql
Pin: release a=karmic
Pin-Priority: 991

Package: php5-pspell
Pin: release a=karmic
Pin-Priority: 991

Package: php5-recode
Pin: release a=karmic
Pin-Priority: 991

Package: php5-snmp
Pin: release a=karmic
Pin-Priority: 991

Package: php5-sqlite
Pin: release a=karmic
Pin-Priority: 991

Package: php5-sybase
Pin: release a=karmic
Pin-Priority: 991

Package: php5-tidy
Pin: release a=karmic
Pin-Priority: 991

Package: php5-xmlrpc
Pin: release a=karmic
Pin-Priority: 991

Package: php5-xsl
Pin: release a=karmic
Pin-Priority: 991

Package: php5-enchant
Pin: release a=karmic
Pin-Priority: 991

Package: php5-intl
Pin: release a=karmic
Pin-Priority: 991

Package: libapache2-mod-php5
Pin: release a=karmic
Pin-Priority: 991

Package: libapache2-mod-php5filter
Pin: release a=karmic
Pin-Priority: 991

Package: php-pear
Pin: release a=karmic
Pin-Priority: 991

```

I have also completely removed (purged) all of my php packages and run aptitude update.

Yet when I attempt to install libapache2-mod-php5 or php5-common they are pulling the 5.3 version of the package.

What am I missing and how can I fix this?

---

