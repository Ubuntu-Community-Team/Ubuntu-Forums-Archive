---
title: "'Login' package blocking any package upgrades"
date: 2009-11-04
forum: General Help
---

### Post by crackotter on 2009-11-04
HI All,
 I tried to do a package upgrade in apt (aptitude) recently, and seems to have blocked all my other packages. I can't see to get around it. I have tried to "autoclean", tried using apt and even went tried a 'dpkg -i'. 

Here is my example:
```

Writing extended state information... Done
(Reading database ... 40684 files and directories currently installed.)
Preparing to replace login 4.0.13-7ubuntu3.4 (using .../login_1%3a4.0.13-7ubuntu3.4_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/login_1%3a4.0.13-7ubuntu3.4_i386.deb (--unpack):
 unable to install updated status of `login': No such file or directory
E: Sub-process /usr/bin/dpkg received a segmentation fault.
A package failed to install.  Trying to recover:
dpkg: error processing login (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Errors were encountered while processing:
 login

```

I can't figure out any way to get around this, and some of my services are down because of this. Anyone have any ideas or information I can provide?

---

### Post by michy99 on 2009-11-04
Open up /var/lib/dpkg/status for editing as root.```
gksudo gedit /var/lib/dpkg/status
```Use the find function to locate the entry for the package login. Delete the entry (everything from 'Package: login' to the next package entry.) Save and exit. Now run```
sudo dpkg --configure -a
``` and see if you get any errors.

---

### Post by crackotter on 2009-11-04
No errors:

```

root@serenity:/home/jhurtado# dpkg --configure -a
root@serenity:/home/jhurtado# 

```

But still getting the following errors:

```

Writing extended state information... Done
Selecting previously deselected package login.
(Reading database ... 40621 files and directories currently installed.)
Unpacking login (from .../login_1%3a4.0.13-7ubuntu3.4_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/login_1%3a4.0.13-7ubuntu3.4_i386.deb (--unpack):
 unable to install updated status of `login': No such file or directory
E: Sub-process /usr/bin/dpkg received a segmentation fault.
A package failed to install.  Trying to recover:

```

---

### Post by michy99 on 2009-11-04
What command were you running when you got the error?

Did you delete the 'Package: login' entry from /var/lib/dpkg/status?

---

### Post by crackotter on 2009-11-04
Aptitude, also have tried apt. Here is the entire command (also deleted the references for "Package: login" in the file you mentioned.

```

 aptitude reinstall login
Reading package lists... Done
Building dependency tree... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
login is not currently installed, so it will not be reinstalled.
The following packages are BROKEN:
  passwd ubuntu-minimal 
The following packages have been kept back:
  apache2 apache2-common apache2-mpm-prefork apache2-utils apt apt-utils bind9-host clamav 
  clamav-base clamav-daemon clamav-freshclam cron dhcp3-client dhcp3-common dnsutils 
  libapache2-mod-php5 libapr0 libarchive-tar-perl libavahi-client3 libavahi-common-data 
  libavahi-common3 libavahi-glib1 libbind9-0 libcurl3 libdbus-1-2 libdbus-glib-1-2 libdns21 
  libfreetype6 libgnutls12 libisc11 libisccc0 libisccfg1 libkrb53 liblwres9 libmysqlclient15off 
Package: xmodmap
  libnewt0.51 libpango1.0-0 libpango1.0-common libpng12-0 libpq4 libruby1.8 libsasl2 
  libsasl2-modules libsasl2-modules-sql libsndfile1 libssl0.9.8 libtiff4 libvorbis0a 
  libvorbisfile3 libxml2 linux-image-server linux-restricted-modules-common linux-server locales 
  mysql-client mysql-client-5.0 mysql-common mysql-server mysql-server-5.0 ntpdate nvidia-glx 
  openssh-client openssh-server openssl perl perl-base perl-modules php-pear php5-cgi php5-cli 
  php5-common php5-gd php5-mysql php5-mysqli python2.4 python2.4-libxml2 python2.4-minimal 
  ruby1.8 sasl2-bin spamassassin spamc tar udev wget whiptail xterm 
0 packages upgraded, 0 newly installed, 0 to remove and 87 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
The following packages have unmet dependencies:
  passwd: Depends: login (>= 970502-1) but it is not installable
  ubuntu-minimal: Depends: login but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Install the following packages:
login [1:4.0.13-7ubuntu3.4 (dapper-updates, dapper-security)]

Score is 99984

Accept this solution? [Y/n/q/?] y
The following NEW packages will be automatically installed:
  login 
The following packages have been kept back:
  apache2 apache2-common apache2-mpm-prefork apache2-utils apt apt-utils bind9-host clamav 
  clamav-base clamav-daemon clamav-freshclam cron dhcp3-client dhcp3-common dnsutils 
  libapache2-mod-php5 libapr0 libarchive-tar-perl libavahi-client3 libavahi-common-data 
  libavahi-common3 libavahi-glib1 libbind9-0 libcurl3 libdbus-1-2 libdbus-glib-1-2 libdns21 
  libfreetype6 libgnutls12 libisc11 libisccc0 libisccfg1 libkrb53 liblwres9 libmysqlclient15off 
  libnewt0.51 libpango1.0-0 libpango1.0-common libpng12-0 libpq4 libruby1.8 libsasl2 
  libsasl2-modules libsasl2-modules-sql libsndfile1 libssl0.9.8 libtiff4 libvorbis0a 
  libvorbisfile3 libxml2 linux-image-server linux-restricted-modules-common linux-server locales 
  mysql-client mysql-client-5.0 mysql-common mysql-server mysql-server-5.0 ntpdate nvidia-glx 
  openssh-client openssh-server openssl passwd perl perl-base perl-modules php-pear php5-cgi 
  php5-cli php5-common php5-gd php5-mysql php5-mysqli python2.4 python2.4-libxml2 
  python2.4-minimal ruby1.8 sasl2-bin spamassassin spamc tar udev wget whiptail xterm 
The following NEW packages will be installed:
  login 
0 packages upgraded, 1 newly installed, 0 to remove and 87 not upgraded.
Need to get 0B/241kB of archives. After unpacking 2089kB will be used.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
Selecting previously deselected package login.
(Reading database ... 40621 files and directories currently installed.)
Unpacking login (from .../login_1%3a4.0.13-7ubuntu3.4_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/login_1%3a4.0.13-7ubuntu3.4_i386.deb (--unpack):
 unable to install updated status of `login': No such file or directory
E: Sub-process /usr/bin/dpkg received a segmentation fault.
A package failed to install.  Trying to recover:

```

---

### Post by michy99 on 2009-11-04
Try this:```
sudo apt-get clean
sudo aptitude install login
```Also, what version of Ubuntu are you running?

---

### Post by crackotter on 2009-11-04
Running Dapper. Thanks for the help so far.

```

root@serenity:/home/jhurtado# sudo apt-get clean
root@serenity:/home/jhurtado# sudo aptitude install login
Reading package lists... Done
Building dependency tree... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages have been kept back:
  apache2 apache2-common apache2-mpm-prefork apache2-utils apt apt-utils bind9-host clamav 
  clamav-base clamav-daemon clamav-freshclam cron dhcp3-client dhcp3-common dnsutils 
  libapache2-mod-php5 libapr0 libarchive-tar-perl libavahi-client3 libavahi-common-data 
  libavahi-common3 libavahi-glib1 libbind9-0 libcurl3 libdbus-1-2 libdbus-glib-1-2 libdns21 
  libfreetype6 libgnutls12 libisc11 libisccc0 libisccfg1 libkrb53 liblwres9 libmysqlclient15off 
  libnewt0.51 libpango1.0-0 libpango1.0-common libpng12-0 libpq4 libruby1.8 libsasl2 
  libsasl2-modules libsasl2-modules-sql libsndfile1 libssl0.9.8 libtiff4 libvorbis0a 
  libvorbisfile3 libxml2 linux-image-server linux-restricted-modules-common linux-server locales 
  mysql-client mysql-client-5.0 mysql-common mysql-server mysql-server-5.0 ntpdate nvidia-glx 
  openssh-client openssh-server openssl passwd perl perl-base perl-modules php-pear php5-cgi 
  php5-cli php5-common php5-gd php5-mysql php5-mysqli python2.4 python2.4-libxml2 
  python2.4-minimal ruby1.8 sasl2-bin spamassassin spamc tar udev wget whiptail xterm 
The following packages will be upgraded:
  login 
1 packages upgraded, 0 newly installed, 0 to remove and 87 not upgraded.
Need to get 241kB of archives. After unpacking 2089kB will be used.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
Get:1 http://us.archive.ubuntu.com dapper-updates/main login 1:4.0.13-7ubuntu3.4 [241kB]
Fetched 241kB in 1s (159kB/s) 
(Reading database ... 40684 files and directories currently installed.)
Preparing to replace login 1:4.0.13-7ubuntu3.4 (using .../login_1%3a4.0.13-7ubuntu3.4_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/login_1%3a4.0.13-7ubuntu3.4_i386.deb (--unpack):
 unable to install updated status of `login': No such file or directory
E: Sub-process /usr/bin/dpkg received a segmentation fault.
A package failed to install.  Trying to recover:
root@serenity:/home/jhurtado# 

```

---

### Post by michy99 on 2009-11-04
Well, I don't know if this is part of the problem or not, but Dapper has not been supported for a long time now. Have you considered upgrading to a newer version?

---

### Post by grandtoubab on 2009-11-04
i would try

sudo apt-get update

sudo apt-get upgrade

---

### Post by crackotter on 2009-11-04
Plan to do a dist-upgrade once I can around this problem. Any other recommendations?

---

### Post by michy99 on 2009-11-04
Seems to be a problem with the package itself. Sorry, but that is all the tricks I know on this one. Maybe someone else can help.

As for upgrading, it might be best to just backup all data and do a fresh install.

---

### Post by grandtoubab on 2009-11-04
try to manage using dpkg, first check

**sudo dpkg ** [B]--audit


[http://unixhelp.ed.ac.uk/CGI/man-cgi?dpkg](http://unixhelp.ed.ac.uk/CGI/man-cgi?dpkg)
[/B]

---

### Post by crackotter on 2009-11-04
You are correct, so how do I get dpkg to install, overridding the problems it sees?

```

root@serenity:/home/jhurtado# sudo dpkg  --audit
The following packages are in a mess due to serious problems during
installation.  They must be reinstalled for them (and any packages
that depend on them) to function properly:
 login                

root@serenity:/home/jhurtado# 

```

---

### Post by grandtoubab on 2009-11-05
so 

dpkg -r | --remove | -P | --purge package ... | -a | --pending 	      Remove an installed package.  -r or --remove  remove  everything 	      except  configuration files.  This may avoid having to reconfig- 	      ure the package if  it  is  reinstalled  later.	(Configuration 	      files  are  the  files  listed  in  the debian/conffiles control 	      file).  -P or --purge removes everything,  including  configura- 	      tion  files.   If  -a or --pending is given instead of a package 	      name, then all packages unpacked, but marked to  be  removed  or 	      purged  in  file	/var/lib/dpkg/status,  are  removed or purged, 	      respectively. 


```
sudo dpkg -P login
```


and the try to reinstall it with Synaptic: System -> Administration ->..Synaptic

---

