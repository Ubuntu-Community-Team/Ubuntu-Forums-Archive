---
title: "Updated Apache, Now PHP5 Broken"
date: 2010-09-29
forum: General Help
---

### Post by ackatack on 2010-09-29
I'll admit that I'm an Ubuntu novice. Earlier today, I installed the following updates for my Ubuntu 9.10 system:

adobe-flashplugin apache2.2-bin apache2.2-common apache2-prefork-dev apache2-mpm-worker apache2 apache2-mpm-prefork avahi-autoipd avahi-daemon avahi-utils fglrx-modaliases libavahi-client3 libavahi-common-data libavahi-common3 libavahi-compat-libdnssd1 libavahi-core6 libavahi-glib1 libavahi-gobject0 libavahi-ui0 libgdiplus libmikmod2 python-avahi

Immediately following the installation, Apache's PHP5 module fails at start with the following error:

 * Starting web server apache2
apache2: Syntax error on line 185 of /etc/apache2/apache2.conf: Syntax error on line 1 of /etc/apache2/mods-enabled/php5.load: Cannot load /usr/lib/apache2/modules/libphp5.so into server: /usr/lib/apache2/modules/libphp5.so: cannot open shared object file: No such file or directory
   ...fail!

I've tried installing and reinstalling libapache2-mod-php5 but I receive the following errors:

For reinstall: Reinstallation of php5 is not possible, it cannot be downloaded.
For install: The following packages have unmet dependencies:
  libapache2-mod-php5: Depends: php5-common (= 5.2.10.dfsg.1-2ubuntu6.5) but 5.2.14-0.dotdeb.0 is to be installed
E: Broken packages

I've tried installing and reinstalling PHP5 but I receive the following errors:

For reinstall: Reinstallation of php5 is not possible, it cannot be downloaded.
For install: php5 is already the newest version.

I'm at a loss as to how to fix this dependency issue. I've tried using -f in both apt and aptitude but neither could sort out the issue. Any help is very welcomed.

I'm not sure if it will help or not but here is my apt sources list:

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
# deb [http://download.webmin.com/download/repository](http://download.webmin.com/download/repository) sarge contrib # disabled on upgrade to karmic

##PHP5 with GD sources for Drupal
# deb [http://packages.dotdeb.org](http://packages.dotdeb.org) stable all # disabled on upgrade to karmic
# deb-src [http://packages.dotdeb.org](http://packages.dotdeb.org) stable all # disabled on upgrade to karmic

Thanks,

Alex

---

### Post by ackatack on 2010-09-29
Thanks to jrib on IRC for help in fixing this issue! I had used an unsupported repository a few months ago which had installed its own version of PHP5 and the PHP5 components. I had to use "apt-get install PHP5=(required version)" which downgraded the package and removed others. I was then able to install the latest supported version of PHP5 on my server.

---

