---
title: "Fixing uber broken dependencies"
date: 2010-11-08
forum: General Help
---

### Post by everythingsround on 2010-11-08
I upgraded from 10.04 to 10.10 via command line (disabling third-party repos from sources.list.d and changing all occurrences of lucid to maverick in sources.list).

Now my problem:

I can't install or update because of broken packages...

> 
sudo apt-get update
sudo apt-get dist-upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  gir1.0-glib-2.0: Depends: libgirepository1.0-1 (>= 0.9.3) but it is not installed
  libasound2-plugins: Depends: libjack-jackd2-0 (>= 1.9.5~dfsg-14) but it is not installed or
                               libjack-0.116
  libjack-dev: Depends: libjack0 (= 1:0.118+svn3796-7ubuntu1) but 0.118+svn3796-1ubuntu2 is installed
  libmutter-private0: Depends: libgirepository1.0-1 (>= 0.6.3) but it is not installed
  libxine1-misc-plugins: Depends: libjack-jackd2-0 (>= 1.9.5~dfsg-14) but it is not installed or
                                  libjack-0.116
  mutter: Depends: libgirepository1.0-1 (>= 0.6.3) but it is not installed
  python-gobject: Depends: libgirepository1.0-1 (>= 0.6.14) but it is not installed
                  Recommends: python-gobject-cairo but it is not installed
  qjackctl: Depends: libjack-jackd2-0 (>= 1.9.5~dfsg-14) but it is not installed or
                     libjack-0.116
E: Unmet dependencies. Try using -f.


Then if I try -f install and even --fix-missing, I get:

> sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libprotobuf5 python-twisted-lore gthumb-data python-twisted-news podsleuth libdirectfb-extra python-twisted
  schedtool libgtksourceview1.0-0 virtuoso-nepomuk libwebkit1.1-cil python-twisted-runner libboo2.0.9-cil
  libgtksourceview-common libvamp-sdk2
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libgirepository1.0-1 libjack0
Suggested packages:
  jackd1
The following packages will be REMOVED:
  jackd jamin meterbridge slv2-jack timemachine
The following NEW packages will be installed:
  libgirepository1.0-1
The following packages will be upgraded:
  libjack0
1 upgraded, 1 newly installed, 5 to remove and 2480 not upgraded.
593 not fully installed or removed.
Need to get 0B/108kB of archives.
After this operation, 2,920kB disk space will be freed.
Do you want to continue [Y/n]? y
warning, in file '/var/lib/dpkg/available' near line 118491 package 'virtualbox-3.1':
 error in Version string '3.1.2-56127_Ubuntu_karmic': invalid character in revision number
warning, in file '/var/lib/dpkg/available' near line 118513 package 'virtualbox-3.0':
 error in Version string '3.0.4-50677_Ubuntu_jaunty': invalid character in revision number
(Reading database ... 742267 files and directories currently installed.)
Unpacking libgirepository1.0-1 (from .../libgirepository1.0-1_0.9.3-0ubuntu4_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libgirepository1.0-1_0.9.3-0ubuntu4_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libgirepository-1.0.so.1.0.0', which is also in package libgirepository1.0-0 0.9.3-0ubuntu1~ppa10.04+1
Errors were encountered while processing:
 /var/cache/apt/archives/libgirepository1.0-1_0.9.3-0ubuntu4_amd64.deb
localepurge: checking for existence of /var/cache/localepurge...
localepurge: checking for existence of /var/cache/localepurge/localelist...
localepurge: checking system for new locale ...
localepurge: processing locale files ...
localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: processing man pages ...
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: processing Gnome files ...
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: processing Omf files ...
localepurge: Disk space freed in /usr/share/omf: 0 KiB
localepurge: processing KDE files ...
localepurge: Disk space freed in /usr/share/doc/kde/HTML: 0 KiB

Total disk space freed by localepurge: 0 KiB

E: Sub-process /usr/bin/dpkg returned an error code (1)


How can I manually purge jack or otherwise work around this to get back up?

All and any suggestions are very much appreciated.  Thanks.

---

### Post by everythingsround on 2010-11-08
[https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/636586](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/636586)

Helped me...at the bottom:

$ sudo dpkg --clear-avail
$ sudo aptitude purge virtualbox-2.2 virtualbox-3.0 virtualbox-3.1

Seems to have fixed things for me. SWEETNESS!

Hope this helps others.

---

### Post by everythingsround on 2010-11-08
> **everythingsround said:**
> [https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/636586](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/636586)

Helped me...at the bottom:

$ sudo dpkg --clear-avail
$ sudo aptitude purge virtualbox-2.2 virtualbox-3.0 virtualbox-3.1

Seems to have fixed things for me. SWEETNESS!

Hope this helps others.

Well, this helped a lot - installed and setup a bunch that had been halted during the upgrade - but I still can't get past:

> 
Do you want to continue [Y/n]? 
(Reading database ... 742268 files and directories currently installed.)
Unpacking libgirepository1.0-1 (from .../libgirepository1.0-1_0.9.3-0ubuntu4_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libgirepository1.0-1_0.9.3-0ubuntu4_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libgirepository-1.0.so.1.0.0', which is also in package libgirepository1.0-0 0.9.3-0ubuntu1~ppa10.04+1
Errors were encountered while processing:
 /var/cache/apt/archives/libgirepository1.0-1_0.9.3-0ubuntu4_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


How can I remove this ppa version? Thanks for any help!

---

### Post by dino99 on 2010-11-08
open synaptic (system admin synaptic) and goto repo tab: deselect third parties if any

then on left pane: look at broken package(s): remove/purge them by right clicking

update again and clean the room (unneeded packages, old dependencies: listed in left pane)

note: everything into /var/cache/apt/archives/ can be deleted when things goes wrong (you need to update again to retrieve the packages, thats all)

---

### Post by everythingsround on 2010-11-08
> **dino99 said:**
> open synaptic (system admin synaptic) and goto repo tab: deselect third parties if any

then on left pane: look at broken package(s): remove/purge them by right clicking

update again and clean the room (unneeded packages, old dependencies: listed in left pane)

note: everything into /var/cache/apt/archives/ can be deleted when things goes wrong (you need to update again to retrieve the packages, thats all)

Thanks for the tips, but I am only able to ssh into this box.  Any way I can do that via the CLI?  

I have tried the install -f and --fix-missing to no avail.  Not sure how else to attempt to fix broken packages from the command line.  Any dpkg, apt, or aptitude, CLI tips? Thanks, again.

---

### Post by dino99 on 2010-11-08
into a terminal:

sudo rm -f /var/cache/apt/archives/*

then update again

---

### Post by everythingsround on 2010-11-08
> **dino99 said:**
> into a terminal:

sudo rm -f /var/cache/apt/archives/*

then update again

That looked like a great idea...

I get:
> 
sudo rm -f /var/cache/apt/archives/*
sudo: unable to execute /bin/rm: Argument list too long


So I tried it as root and got:

> 
# rm -f /var/cache/apt/archives/*
rm: cannot remove `/var/cache/apt/archives/partial': Is a directory


then apt-get update and apt-get update gives me:

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  gir1.0-glib-2.0: Depends: libgirepository1.0-1 (>= 0.9.3) but it is not installed
  konqueror: Depends: libkonqsidebarplugin4a (>= 4:4.4.1) but it is not installed
             Depends: kdebase-data (= 4:4.5.1-0ubuntu4) but 4:4.4.2-0ubuntu2 is installed
             Depends: kdebase-bin (= 4:4.5.1-0ubuntu4) but 4:4.4.2-0ubuntu2 is installed
             Recommends: konqueror-nsplugins (= 4:4.5.1-0ubuntu4) but 4:4.4.2-0ubuntu2 is installed
  libmutter-private0: Depends: libgirepository1.0-1 (>= 0.6.3) but it is not installed
  mutter: Depends: libgirepository1.0-1 (>= 0.6.3) but it is not installed
  python-gobject: Depends: libgirepository1.0-1 (>= 0.6.14) but it is not installed
                  Recommends: python-gobject-cairo but it is not installed
E: Unmet dependencies. Try using -f.


So I try sudo apt-get upgrade -f and...waiting ~30 minutes...I'll post back.  

Thanks for your help. Wish me luck.

---

### Post by everythingsround on 2010-11-08
Well, instead of waiting more than an hour to download almost 3GB and find out it didn't work, I removed the apt/archives again after cancelling the get process for upgrade.

Then I simply tried apt-get -f install and get:

> sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libprotobuf5 konqueror-nsplugins python-twisted-lore gthumb-data python-twisted-news podsleuth libdirectfb-extra
  python-twisted schedtool libgtksourceview1.0-0 virtuoso-nepomuk libwebkit1.1-cil kinfocenter python-twisted-runner
  libboo2.0.9-cil libgtksourceview-common libvamp-sdk2
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  kdebase-apps kdebase-bin kdebase-data kdepasswd kfind konsole kwrite libgirepository1.0-1 libkonqsidebarplugin4a
  plasma-widget-folderview
The following packages will be REMOVED:
  kappfinder kdebase-plasma libkonqsidebarplugin4
The following NEW packages will be installed:
  libgirepository1.0-1 libkonqsidebarplugin4a
The following packages will be upgraded:
  kdebase-apps kdebase-bin kdebase-data kdepasswd kfind konsole kwrite plasma-widget-folderview
8 upgraded, 2 newly installed, 3 to remove and 2472 not upgraded.
17 not fully installed or removed.
Need to get 1,667kB of archives.
After this operation, 3,576kB disk space will be freed.
Do you want to continue [Y/n]? 
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main libgirepository1.0-1 0.9.3-0ubuntu4 [54.6kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main libkonqsidebarplugin4a 4:4.5.1-0ubuntu4 [83.0kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main kdebase-bin 4:4.5.1-0ubuntu4 [375kB]
Get:4 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main kdepasswd 4:4.5.1-0ubuntu4 [88.8kB]
Get:5 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main kfind 4:4.5.1-0ubuntu4 [92.4kB]
Get:6 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main konsole 4:4.5.1-0ubuntu4 [421kB]
Get:7 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main kwrite 4:4.5.1-0ubuntu4 [135kB]
Get:8 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main plasma-widget-folderview 4:4.5.1-0ubuntu4 [143kB]
Get:9 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main kdebase-apps 4:4.5.1-0ubuntu4 [69.6kB]
Get:10 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main kdebase-data 4:4.5.1-0ubuntu4 [206kB]
Fetched 1,667kB in 4s (373kB/s)    
(Reading database ... 742278 files and directories currently installed.)
Unpacking libgirepository1.0-1 (from .../libgirepository1.0-1_0.9.3-0ubuntu4_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libgirepository1.0-1_0.9.3-0ubuntu4_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libgirepository-1.0.so.1.0.0', which is also in package libgirepository1.0-0 0.9.3-0ubuntu1~ppa10.04+1
Errors were encountered while processing:
 /var/cache/apt/archives/libgirepository1.0-1_0.9.3-0ubuntu4_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

AHHHH! now what? :popcorn:

---

### Post by everythingsround on 2010-11-09
Well, hope this helps others who are trying to fix broken packages.  Of course this only happened because I was using a PPA.

From this thread:
[http://ubuntuforums.org/showthread.php?t=7296](http://ubuntuforums.org/showthread.php?t=7296)

My problem:
> 
dpkg: error processing /var/cache/apt/archives/libgirepository1.0-1_0.9.3-0ubuntu4_amd64.deb (--unpack):
trying to overwrite '/usr/lib/libgirepository-1.0.so.1.0.0', which is also in package libgirepository1.0-0 0.9.3-0ubuntu1~ppa10.04+1

Solution was at the end of the thread:

> dpkg --force-all -i /var/cache/apt/archives/liblame0_3.96.1-1_i386.deb

apt-get -f install

Of course, replace the package name with your suspect/troubled package.

---

### Post by dino99 on 2010-11-09
the good solution was to remove that ppa or check that it use the good distro release

---

### Post by everythingsround on 2010-11-09
> **dino99 said:**
> the good solution was to remove that ppa or check that it use the good distro release

I had removed all third-party repos and custom PPA's before the upgrade.  How would I remove that package manually? or can you elaborate on what you mean, please? Thanks.

---

