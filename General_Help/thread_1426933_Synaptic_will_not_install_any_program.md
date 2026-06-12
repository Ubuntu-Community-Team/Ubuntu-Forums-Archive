---
title: "Synaptic will not install any program"
date: 2010-03-10
forum: General Help
---

### Post by jyanek on 2010-03-10
Using Ubuntu 9.10, with no problems for some time.  Now when I try to install any package, I will get the following:

```
(Reading database ... 45%dpkg: unrecoverable fatal error, aborting:
 failed in buffer_read(fd): files list for package 'linux-headers-2.6.31-20': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
```

No matter which package I try to install, it will hang at 45% and give the same error.

Thoughts?  Thanks in advance!

---

### Post by dcstar on 2010-03-10
> **jyanek said:**
> Using Ubuntu 9.10, with no problems for some time.  Now when I try to install any package, I will get the following:

```
(Reading database ... 45%dpkg: unrecoverable fatal error, aborting:
 failed in buffer_read(fd): files list for package 'linux-headers-2.6.31-20': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
```

No matter which package I try to install, it will hang at 45% and give the same error.

Thoughts?  Thanks in advance!

Select a different Software Source (repository) and then Reload, report back what happens.

---

### Post by jyanek on 2010-03-11
> **dcstar said:**
> Select a different Software Source (repository) and then Reload, report back what happens.
I tried two other sources, and both give identical errors (even both stopping at 45%).  Note that all servers will download the packages.  It is during the install that I get hung up, no matter which package (nor server) I use.

---

### Post by plucky on 2010-03-11
Try ```
sudo dpkg --configure -a
```

and if that fails,try ```
sudo apt-get install -f
``` or use Synaptic Package Manager to fix broken packages.

Good Luck

---

### Post by jyanek on 2010-03-11
> **plucky said:**
> Try ```
sudo dpkg --configure -a
```

and if that fails,try ```
sudo apt-get install -f
``` or use Synaptic Package Manager to fix broken packages.

Good Luck
Thanks.  I tried all three of those suggestions.  Synaptic still hangs at 45%.  Same response whether I do it from the package manager, command line, etc.

---

### Post by sandyd on 2010-03-11
> **jyanek said:**
> Thanks.  I tried all three of those suggestions.  Synaptic still hangs at 45%.  Same response whether I do it from the package manager, command line, etc.

```

sudo dpkg --purge --force all linux-headers-2.6.31-20
sudo rm /var/cache/apt/archives/*
sudo apt-get install linux-headers-2.6.31-20

```

---

### Post by jyanek on 2010-03-11
> **carlee said:**
> ```

sudo dpkg --purge --force all linux-headers-2.6.31-20
sudo rm /var/cache/apt/archives/*
sudo apt-get install linux-headers-2.6.31-20

```

I executed the above; however, still same issue.  Note below that when I executed the first command, you will see the same "(Reading database ... 45%" issue, and again when it attempted to install packages.  Here is the entire extract of my session.:

```
poodles@happy:~$ sudo dpkg --purge --force all linux-headers-2.6.31-20
dpkg: linux-headers-2.6.31-20: dependency problems, but removing anyway as you requested:
 linux-headers-2.6.31-20-generic depends on linux-headers-2.6.31-20.
(Reading database ... 45%dpkg: unrecoverable fatal error, aborting:
 failed in buffer_read(fd): files list for package `linux-headers-2.6.31-20': Input/output error
poodles@happy:~$ sudo rm /var/cache/apt/archives/*
rm: cannot remove `/var/cache/apt/archives/partial': Is a directory
poodles@happy:~$ sudo apt-get install linux-headers-2.6.31-20
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
poodles@happy:~$ sudo dpkg --configure -a
poodles@happy:~$ sudo apt-get install linux-headers-2.6.31-20
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.31-20 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
poodles@happy:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  devede
The following packages will be upgraded:
  dpkg gnome-screensaver tzdata tzdata-java
4 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 7,184kB of archives.
After this operation, 4,096B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://us.archive.ubuntu.com karmic-updates/main dpkg 1.15.4ubuntu2.1 [2,171kB]
Get:2 http://us.archive.ubuntu.com karmic-updates/main tzdata-java 2010e-0ubuntu0.9.10 [144kB]
Get:3 http://us.archive.ubuntu.com karmic-updates/main tzdata 2010e-0ubuntu0.9.10 [683kB]
Get:4 http://us.archive.ubuntu.com karmic-updates/main gnome-screensaver 2.28.0-0ubuntu3.5 [4,186kB]
Fetched 7,184kB in 26s (271kB/s)                                               
Preconfiguring packages ...
(Reading database ... 45%dpkg: unrecoverable fatal error, aborting:
 failed in buffer_read(fd): files list for package `linux-headers-2.6.31-20': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)
poodles@happy:~$ 

```

---

### Post by plucky on 2010-03-12
> (Reading database ... 45%dpkg: unrecoverable fatal error, aborting:
 failed in buffer_read(fd): files list for package `linux-headers-2.6.31-20': Input/output error


It seems to be having problems reading linux-headers-2.6.31-20.list.

You could from a terminal ```
sudo mv /var/lib/dpkg/info/linux-headers-2.6.31-20.list /var/lib/dpkg/info/linux-headers-2.6.31-20.list.old
```

Then open synaptic package manager and search for **linux-headers-2.6.31.20** and reinstall which will recreate the list.It will complain that the file is missing,but it will then recreate it.

Good Luck

---

### Post by jyanek on 2010-03-12
> **plucky said:**
> It seems to be having problems reading linux-headers-2.6.31-20.list.

You could from a terminal ```
sudo mv /var/lib/dpkg/info/linux-headers-2.6.31-20.list /var/lib/dpkg/info/linux-headers-2.6.31-20.list.old
```

Then open synaptic package manager and search for **linux-headers-2.6.31.20** and reinstall which will recreate the list.It will complain that the file is missing,but it will then recreate it.

Good Luck

SOLVED!  THANK YOU.  Renaming the linux-headers-2.6.31-20.list and reinstalling them solved my problem.  THANKS!

This can be marked "solved" now; however, I do not know how to do this myself.  Thanks.

---

### Post by davidpbrown on 2010-03-12
> This can be marked "solved" now; however, I do not know how to do this myself.

At the top [Thread Tools] has ~'mark thread as solved'.

---

### Post by jyanek on 2010-03-12
> **davidpbrown said:**
> At the top [Thread Tools] has ~'mark thread as solved'.

Done.  Thanks all for the quick help!  Great use of the forum.

---

### Post by jobsworth on 2010-03-13
Sorry to be a wet blanket but I am not solved.

I am running Ubuntu 9.10 in a Sun Virtual Box Version 3.1.4 r57640 
under Windows XP,
which may be a little different.
I have tried all of this and more.
I still get the same error message.

Preconfiguring packages ...
(Reading database ... 45%dpkg: unrecoverable fatal error, aborting:
 files list file for package 'openoffice.org-core' is missing final newline
E: Sub-process /usr/bin/dpkg returned an error code (2)


I also run Ubuntu 9.10 as a dual boot with Windows XP,
where I do not have this problem.

---

### Post by el duderino's dude on 2010-06-13
```
mike@Mikes-Computational:~$ sudo apt-get update
[sudo] password for mike: 
Get:1 http://dl.google.com stable Release.gpg [189B]
Ign http://dl.google.com/linux/deb/ stable/main Translation-en_US              
Hit http://archive.canonical.com lucid Release.gpg                             
Ign http://archive.canonical.com/ lucid/partner Translation-en_US              
Hit http://archive.ubuntu.com lucid Release.gpg                                
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu/ lucid/main Translation-en_US
Hit http://us.archive.ubuntu.com lucid Release.gpg                             
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US          
Get:2 http://dl.google.com stable Release [2,544B]                             
Hit http://archive.canonical.com lucid Release                                 
Hit http://archive.ubuntu.com lucid Release                                    
Hit http://ppa.launchpad.net lucid Release                                     
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US    
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid-updates Release.gpg           
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Get:3 http://dl.google.com stable/main Packages [1,061B]
Hit http://us.archive.ubuntu.com lucid-security Release.gpg              
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US 
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid Release                                 
Hit http://archive.canonical.com lucid/partner Packages                        
Hit http://archive.ubuntu.com lucid/main Sources                               
Hit http://ppa.launchpad.net lucid/main Packages                     
Hit http://us.archive.ubuntu.com lucid-updates Release
Hit http://us.archive.ubuntu.com lucid-security Release              
Hit http://archive.ubuntu.com lucid/restricted Sources               
Hit http://us.archive.ubuntu.com lucid/main Packages
Hit http://us.archive.ubuntu.com lucid/restricted Packages
Hit http://us.archive.ubuntu.com lucid/universe Packages
Hit http://us.archive.ubuntu.com lucid/multiverse Packages
Hit http://us.archive.ubuntu.com lucid/main Sources
Hit http://us.archive.ubuntu.com lucid/restricted Sources
Hit http://us.archive.ubuntu.com lucid/universe Sources
Hit http://us.archive.ubuntu.com lucid/multiverse Sources
Hit http://us.archive.ubuntu.com lucid-updates/main Packages
Hit http://us.archive.ubuntu.com lucid-updates/restricted Packages
Hit http://us.archive.ubuntu.com lucid-updates/universe Packages
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Packages
Hit http://us.archive.ubuntu.com lucid-updates/main Sources
Hit http://us.archive.ubuntu.com lucid-updates/restricted Sources
Hit http://us.archive.ubuntu.com lucid-updates/universe Sources
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Sources
Hit http://us.archive.ubuntu.com lucid-security/main Packages
Hit http://us.archive.ubuntu.com lucid-security/restricted Packages
Hit http://us.archive.ubuntu.com lucid-security/universe Packages
Hit http://us.archive.ubuntu.com lucid-security/multiverse Packages
Hit http://us.archive.ubuntu.com lucid-security/main Sources
Hit http://us.archive.ubuntu.com lucid-security/restricted Sources
Hit http://us.archive.ubuntu.com lucid-security/universe Sources
Hit http://us.archive.ubuntu.com lucid-security/multiverse Sources
Fetched 3,794B in 1s (3,271B/s)
Reading package lists... Error!
E: Read error - read (5: Input/output error)
E: Problem opening /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_lucid-updates_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
mike@Mikes-Computational:~$
```

i have tried everything that you and many other people have suggested 

i think im missing a file in var/lib/apt/lists because i have this red circle with a line through it and it say

an error occurred, please run package manager from the right click menu or apt-get in a terminal to see what is wrong and the error code is: 

error:opening the cache (e:read error - read (5:input/output error), E: problem opeing /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_lucid-updates_universe_binary-i386_packages, E: The package lists or status file could not be parsed or opened.)

when i click on this package it pulls up a file in gedit but it then says couldn't open the file and it had an: error reading file: input/output error

anything you can do to help will be appreciated i cant update or install anything to try and help because of it

---

### Post by Soul-Sing on 2010-06-14
try: 
```

sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
```

---

### Post by el duderino's dude on 2010-06-14
thank you that worked but now when i try to download something it does this thanks for all your help in advance and for what you have done

```
mike@Mikes-Computational:~$ sudo apt-get install ubiquity
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
mike@Mikes-Computational:~$ sudo apt-get install ubiquity
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  bogl-bterm cryptsetup dmraid ecryptfs-utils keyutils libdebconfclient0
  libdebian-installer4 libdmraid1.0.0.rc16 libecryptfs0 python-pyicu rdate
  reiserfsprogs ubiquity-casper ubiquity-frontend-debconf
  ubiquity-ubuntu-artwork
Suggested packages:
  opencryptoki
The following NEW packages will be installed:
  bogl-bterm cryptsetup dmraid ecryptfs-utils keyutils libdebconfclient0
  libdebian-installer4 libdmraid1.0.0.rc16 libecryptfs0 python-pyicu rdate
  reiserfsprogs ubiquity ubiquity-casper ubiquity-frontend-debconf
  ubiquity-ubuntu-artwork
0 upgraded, 16 newly installed, 0 to remove and 103 not upgraded.
Need to get 0B/6,803kB of archives.
After this operation, 21.5MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Selecting previously deselected package bogl-bterm.
(Reading database ... 95%dpkg: unrecoverable fatal error, aborting:
 failed in buffer_read(fd): files list for package `libaprutil1-dbd-sqlite3': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)
mike@Mikes-Computational:~$ 
```

---

### Post by Soul-Sing on 2010-06-15
It looks you had at least two package managers open or running.
Maybe close all -apt/dpkg and package managers. Take a look at your
procesmanager also, and look for apt/dpkg processes.

---

### Post by Soul-Sing on 2010-06-15
If this doesn't help: try apt-get -f install to force the install. Then try apt-get update and apt-get upgrade, apt-get -f install back and forth until only the package that has the error is left.

if this doesn't help because of a broken package:

```
gksudo nautilus
```

move via nautilus to /var/lib/dpkg/info

remove the package which gives the error

close nautilus

run ```
sudo apt-get update
```

---

### Post by el duderino's dude on 2010-06-15
again thank you for your help but here is what happened 
```

mike@Mikes-Computational:~$ sudo apt-get -f install ubiquity
[sudo] password for mike: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  bogl-bterm cryptsetup dmraid ecryptfs-utils keyutils libdebconfclient0
  libdebian-installer4 libdmraid1.0.0.rc16 libecryptfs0 python-pyicu rdate
  reiserfsprogs ubiquity-casper ubiquity-frontend-debconf
  ubiquity-ubuntu-artwork
Suggested packages:
  opencryptoki
The following NEW packages will be installed:
  bogl-bterm cryptsetup dmraid ecryptfs-utils keyutils libdebconfclient0
  libdebian-installer4 libdmraid1.0.0.rc16 libecryptfs0 python-pyicu rdate
  reiserfsprogs ubiquity ubiquity-casper ubiquity-frontend-debconf
  ubiquity-ubuntu-artwork
0 upgraded, 16 newly installed, 0 to remove and 103 not upgraded.
Need to get 0B/6,803kB of archives.
After this operation, 21.5MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Selecting previously deselected package bogl-bterm.
(Reading database ... 95%dpkg: unrecoverable fatal error, aborting:
 failed in buffer_read(fd): files list for package `libaprutil1-dbd-sqlite3': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)
mike@Mikes-Computational:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic
The following packages will be upgraded:
  cairo-dock-plug-ins cairo-dock-plug-ins-data cairo-dock-plug-ins-integration
  compiz compiz-core compiz-dbg compiz-dev compiz-gnome compiz-kde
  compiz-plugins docky eucalyptus-common eucalyptus-java-common evolution
  evolution-common evolution-data-server evolution-data-server-common
  evolution-plugins fglrx-modaliases gdm gstreamer0.10-plugins-good
  gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pulseaudio
  indicator-application kdepimlibs-data kdepimlibs5 kpackagekit krb5-multidev
  libappindicator0 libc-bin libc-dev-bin libc6 libc6-dev libc6-i686
  libcamel1.2-14 libdecoration0 libdecoration0-dev libebackend1.2-0
  libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6
  libedataserver1.2-11 libedataserverui1.2-8 libegroupwise1.2-13
  libexchange-storage1.2-3 libgdata-google1.2-1 libgdata1.2-1
  libgnomekbd-common libgnomekbd4 libgssapi-krb5-2 libgssrpc4 libido-0.1-0
  libk5crypto3 libkadm5clnt-mit7 libkadm5srv-mit7 libkdb5-4 libkrb5-3
  libkrb5-dev libkrb5support0 libpam-modules libpam-runtime libpam0g
  libpoppler-glib4 libpoppler5 libsdl1.2debian libsdl1.2debian-pulseaudio
  libservlet2.5-java libservlet2.5-java-doc libtomcat6-java libvirtodbc-dev
  linux-firmware linux-libc-dev nvidia-current-modaliases openssh-client
  openssh-server pm-utils-powersave-policy poppler-utils python-appindicator
  python-docky python-ubuntuone-client software-center ssh-askpass-gnome
  telepathy-butterfly tomcat6 tomcat6-admin tomcat6-common tomcat6-docs
  tomcat6-examples tomcat6-user ubuntu-system-service ubuntuone-client
  ubuntuone-client-gnome udisks update-manager update-manager-core
  update-manager-kde virtuoso-nepomuk xserver-common xserver-xorg-core
100 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 72.4MB of archives.
After this operation, 3,719kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main libpam-modules 1.1.1-2ubuntu3 [358kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main libc-bin 2.11.1-0ubuntu7.2 [723kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main libc6 2.11.1-0ubuntu7.2 [3,779kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main libc6-i686 2.11.1-0ubuntu7.2 [1,228kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main libc-dev-bin 2.11.1-0ubuntu7.2 [213kB]
Get:6 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main libc6-dev 2.11.1-0ubuntu7.2 [4,839kB]
Get:7 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main linux-libc-dev 2.6.32-23.37 [779kB]
Get:8 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main libpam-runtime 1.1.1-2ubuntu3 [115kB]
Get:9 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main libpam0g 1.1.1-2ubuntu3 [123kB]
Get:10 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main libkrb5-dev 1.8.1+dfsg-2ubuntu0.1 [35.7kB]
Get:11 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main krb5-multidev 1.8.1+dfsg-2ubuntu0.1 [102kB]
Get:12 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main libk5crypto3 1.8.1+dfsg-2ubuntu0.1 [96.2kB]
Get:13 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main libgssapi-krb5-2 1.8.1+dfsg-2ubuntu0.1 [120kB]
Get:14 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main libkrb5-3 1.8.1+dfsg-2ubuntu0.1 [350kB]
Get:15 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main libkrb5support0 1.8.1+dfsg-2ubuntu0.1 [42.2kB]
Get:16 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main libgssrpc4 1.8.1+dfsg-2ubuntu0.1 [75.0kB]
Get:17 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main libkdb5-4 1.8.1+dfsg-2ubuntu0.1 [58.8kB]
Get:18 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main libkadm5srv-mit7 1.8.1+dfsg-2ubuntu0.1 [71.7kB]
Get:19 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main libkadm5clnt-mit7 1.8.1+dfsg-2ubuntu0.1 [58.7kB]
Get:20 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main openssh-server 1:5.3p1-3ubuntu4 [285kB]
Get:21 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main openssh-client 1:5.3p1-3ubuntu4 [761kB]
Get:22 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main update-manager 1:0.134.9 [802kB]
Get:23 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main update-manager-core 1:0.134.9 [196kB]
Get:24 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/universe cairo-dock-plug-ins-data 2.1.3-10-lucid-0ubuntu2.1 [3,398kB]
Get:25 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/universe cairo-dock-plug-ins-integration 2.1.3-10-lucid-0ubuntu2.1 [50.7kB]
Get:26 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/universe cairo-dock-plug-ins 2.1.3-10-lucid-0ubuntu2.1 [594kB]
Get:27 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main libdecoration0-dev 1:0.8.4-0ubuntu15.1 [51.9kB]
Get:28 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main libdecoration0 1:0.8.4-0ubuntu15.1 [62.2kB]
Get:29 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main compiz-gnome 1:0.8.4-0ubuntu15.1 [105kB]
Get:30 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/universe compiz-kde 1:0.8.4-0ubuntu15.1 [113kB]
Get:31 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main compiz-plugins 1:0.8.4-0ubuntu15.1 [510kB]
Get:32 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main compiz-core 1:0.8.4-0ubuntu15.1 [248kB]
Get:33 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main compiz 1:0.8.4-0ubuntu15.1 [42.8kB]
Get:34 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main compiz-dbg 1:0.8.4-0ubuntu15.1 [2,055kB]
Get:35 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main compiz-dev 1:0.8.4-0ubuntu15.1 [75.1kB]
Get:36 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/universe python-docky 2.0.4-0ubuntu1 [7,252B]
Get:37 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/universe docky 2.0.4-0ubuntu1 [655kB]
Get:38 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main libedataserver1.2-11 2.28.3.1-0ubuntu3 [128kB]
Get:39 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main libcamel1.2-14 2.28.3.1-0ubuntu3 [357kB]
Get:40 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main libebackend1.2-0 2.28.3.1-0ubuntu3 [15.5kB]
Get:41 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main libebook1.2-9 2.28.3.1-0ubuntu3 [80.8kB]
Get:42 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main libecal1.2-7 2.28.3.1-0ubuntu3 [103kB]
Get:43 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main libedata-book1.2-2 2.28.3.1-0ubuntu3 [49.8kB]
Get:44 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main libedata-cal1.2-6 2.28.3.1-0ubuntu3 [66.9kB]
Get:45 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main libegroupwise1.2-13 2.28.3.1-0ubuntu3 [67.8kB]
Get:46 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main libgdata1.2-1 2.28.3.1-0ubuntu3 [76.6kB]
Get:47 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main libgdata-google1.2-1 2.28.3.1-0ubuntu3 [13.4kB]
Get:48 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main evolution-data-server 2.28.3.1-0ubuntu3 [489kB]
Get:49 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main evolution-data-server-common 2.28.3.1-0ubuntu3 [87.1kB]
Get:50 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main libedataserverui1.2-8 2.28.3.1-0ubuntu3 [87.4kB]
Get:51 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main libexchange-storage1.2-3 2.28.3.1-0ubuntu3 [120kB]
Get:52 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main evolution 2.28.3-0ubuntu10 [2,427kB]
Get:53 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main evolution-common 2.28.3-0ubuntu10 [3,234kB]
Get:54 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main evolution-plugins 2.28.3-0ubuntu10 [223kB]
Get:55 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main gdm 2.30.2.is.2.30.0-0ubuntu1 [734kB]
Get:56 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main gstreamer0.10-plugins-good 0.10.21-1ubuntu3 [1,433kB]
Get:57 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/multiverse gstreamer0.10-plugins-ugly-multiverse 0.10.14-0ubuntu2 [62.5kB]
Get:58 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main gstreamer0.10-pulseaudio 0.10.21-1ubuntu3 [88.7kB]
Get:59 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main indicator-application 0.0.19-0ubuntu5 [24.6kB]
Get:60 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main kdepimlibs-data 4:4.4.2-0ubuntu2.1 [148kB]
Get:61 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main kdepimlibs5 4:4.4.2-0ubuntu2.1 [2,345kB]
Get:62 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main python-appindicator 0.0.19-0ubuntu5 [36.0kB]
Get:63 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main libappindicator0 0.0.19-0ubuntu5 [19.6kB]
Get:64 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main libgnomekbd-common 2.30.1-0ubuntu1 [7,592B]
Get:65 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main libgnomekbd4 2.30.1-0ubuntu1 [45.9kB]
Get:66 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main libido-0.1-0 0.1.6-0ubuntu1 [10.4kB]
Get:67 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main libpoppler5 0.12.4-0ubuntu5 [729kB]
Get:68 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main libpoppler-glib4 0.12.4-0ubuntu5 [75.9kB]
Get:69 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main libsdl1.2debian 1.2.14-4ubuntu1.1 [23.3kB]
Get:70 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main libsdl1.2debian-pulseaudio 1.2.14-4ubuntu1.1 [204kB]
Get:71 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main libservlet2.5-java 6.0.24-2ubuntu1.1 [190kB]
Get:72 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main libservlet2.5-java-doc 6.0.24-2ubuntu1.1 [247kB]
Get:73 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main libtomcat6-java 6.0.24-2ubuntu1.1 [3,008kB]
Get:74 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main libvirtodbc-dev 6.1.0-0ubuntu3.1 [8,411kB]
Get:75 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main linux-firmware 1.34.1 [9,508kB]
Get:76 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main nvidia-current-modaliases 195.36.24-0ubuntu1~10.04 [21.2kB]
Get:77 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main pm-utils-powersave-policy 0.3.1 [2,788B]
Get:78 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main poppler-utils 0.12.4-0ubuntu5 [80.9kB]
Get:79 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main ubuntuone-client-gnome 1.2.1-0ubuntu3 [88.9kB]
Get:80 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main ubuntuone-client 1.2.1-0ubuntu3 [23.6kB]
Get:81 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main python-ubuntuone-client 1.2.1-0ubuntu3 [151kB]
Get:82 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main software-center 2.0.5 [279kB]
Get:83 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main ssh-askpass-gnome 1:5.3p1-3ubuntu4 [86.7kB]
Get:84 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main telepathy-butterfly 0.5.11-0ubuntu1 [49.3kB]
Get:85 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main tomcat6-common 6.0.24-2ubuntu1.1 [45.8kB]
Get:86 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main tomcat6 6.0.24-2ubuntu1.1 [30.5kB]
Get:87 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main tomcat6-admin 6.0.24-2ubuntu1.1 [40.8kB]
Get:88 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main tomcat6-docs 6.0.24-2ubuntu1.1 [495kB]
Get:89 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main tomcat6-examples 6.0.24-2ubuntu1.1 [158kB]
Get:90 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main tomcat6-user 6.0.24-2ubuntu1.1 [24.6kB]
Get:91 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main ubuntu-system-service 0.1.20.1 [9,564B]
Get:92 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main udisks 1.0.1-1ubuntu1 [212kB]
Get:93 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main update-manager-kde 1:0.134.9 [49.8kB]
Get:94 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main virtuoso-nepomuk 6.1.0-0ubuntu3.1 [3,370kB]
Get:95 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main xserver-common 2:1.7.6-2ubuntu7.1 [83.3kB]
Get:96 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main xserver-xorg-core 2:1.7.6-2ubuntu7.1 [2,409kB]
Get:97 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main eucalyptus-common 1.6.2-0ubuntu30.2 [362kB]
Get:98 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main eucalyptus-java-common 1.6.2-0ubuntu30.2 [5,688kB]
Get:99 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main fglrx-modaliases 2:8.723.1-0ubuntu4 [15.0kB]
Get:100 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main kpackagekit 0.5.4-0ubuntu4.1 [474kB]
Fetched 72.4MB in 1min 38s (732kB/s)                                           
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 95%dpkg: unrecoverable fatal error, aborting:
 failed in buffer_read(fd): files list for package `libaprutil1-dbd-sqlite3': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)
mike@Mikes-Computational:~$ gksudo nautilus
Initializing nautilus-gdu extension
could not load face 'file:///var/lib/dpkg/info/wireless-tools.preinst': unknown file format
```


and when i opened nautilus i have the package that comes up with there air but there are 5 different things for it how do i know which one to get rid of the libaprutil1-dbd-sqlite3 but they all have defferent endings like what would classify a document (.jpeg; .docx etc.)

---

### Post by Soul-Sing on 2010-06-15
libaprutil1-dbd-sqlite3 is the troublemaker,I really don't know which "ending" you should choose, or if it makes any difference....

---

### Post by el duderino's dude on 2010-06-15
ok found the one that wont open it is /var/lib/dpkg/info/libaprutil1-dbd-sqlite3.list.
but i get this 
Unexpected error: Error reading from file: Input/output error and i dont think i can copy it but i will try then might delete it

---

### Post by el duderino's dude on 2010-06-15
i got rid of the one packet that i was having problems with now when i hit sudo apt-get upgrade this happens 

```
mike@Mikes-Computational:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic
The following packages will be upgraded:
  cairo-dock-plug-ins cairo-dock-plug-ins-data cairo-dock-plug-ins-integration
  compiz compiz-core compiz-dbg compiz-dev compiz-gnome compiz-kde
  compiz-plugins docky eucalyptus-common eucalyptus-java-common evolution
  evolution-common evolution-data-server evolution-data-server-common
  evolution-plugins fglrx-modaliases gdm gstreamer0.10-plugins-good
  gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pulseaudio
  indicator-application kdepimlibs-data kdepimlibs5 kpackagekit krb5-multidev
  libappindicator0 libc-bin libc-dev-bin libc6 libc6-dev libc6-i686
  libcamel1.2-14 libdecoration0 libdecoration0-dev libebackend1.2-0
  libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6
  libedataserver1.2-11 libedataserverui1.2-8 libegroupwise1.2-13
  libexchange-storage1.2-3 libgdata-google1.2-1 libgdata1.2-1
  libgnomekbd-common libgnomekbd4 libgssapi-krb5-2 libgssrpc4 libido-0.1-0
  libk5crypto3 libkadm5clnt-mit7 libkadm5srv-mit7 libkdb5-4 libkrb5-3
  libkrb5-dev libkrb5support0 libpam-modules libpam-runtime libpam0g
  libpoppler-glib4 libpoppler5 libsdl1.2debian libsdl1.2debian-pulseaudio
  libservlet2.5-java libservlet2.5-java-doc libtomcat6-java libusb-0.1-4
  libvirtodbc-dev linux-firmware linux-libc-dev nvidia-current-modaliases
  openssh-client openssh-server pm-utils-powersave-policy poppler-utils
  python-appindicator python-docky python-ubuntuone-client software-center
  ssh-askpass-gnome telepathy-butterfly tomcat6 tomcat6-admin tomcat6-common
  tomcat6-docs tomcat6-examples tomcat6-user ubuntu-system-service
  ubuntuone-client ubuntuone-client-gnome udisks update-manager
  update-manager-core update-manager-kde virtuoso-nepomuk xserver-common
  xserver-xorg-core
101 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 20.4kB/72.4MB of archives.
After this operation, 3,719kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ lucid-proposed/main libusb-0.1-4 2:0.1.12-14ubuntu0.1 [20.4kB]
Fetched 20.4kB in 2s (8,327B/s)     
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 
dpkg: warning: files list file for package `libaprutil1-dbd-sqlite3' missing, assuming package has no files currently installed.
(Reading database ... 289340 files and directories currently installed.)
Preparing to replace libpam-modules 1.1.1-2ubuntu2 (using .../libpam-modules_1.1.1-2ubuntu3_i386.deb) ...
Unpacking replacement libpam-modules ...
dpkg-deb (subprocess): error in buffer_read(stream): failed to write to pipe in copy: Input/output error
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing /var/cache/apt/archives/libpam-modules_1.1.1-2ubuntu3_i386.deb (--unpack):
 short read in buffer_copy (backend dpkg-deb during `./usr/share/doc/libpam-modules/changelog.Debian.gz')
No apport report written because the error message indicates a dpkg I/O error
                                                                             Errors were encountered while processing:
 /var/cache/apt/archives/libpam-modules_1.1.1-2ubuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
mike@Mikes-Computational:~$ 
```

---

### Post by frt975 on 2010-06-15
```
sudo rm /var/cache/apt/archives/libpam-modules_1.1.1-2ubuntu3_i386.deb
```might help

---

### Post by el duderino's dude on 2010-06-15
can you copy that file and then put it on there so i can re download it in to the file system

---

### Post by el duderino's dude on 2010-06-15
just need to install things but the file is still missing and now i can upgrade my last 2 upgrades this is what happens

```
mike@Mikes-Computational:~$ sudo apt-get -f upgrade
[sudo] password for mike: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  compiz-core libcamel1.2-14
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/604kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 
dpkg: warning: files list file for package `libaprutil1-dbd-sqlite3' missing, assuming package has no files currently installed.
(Reading database ... 312022 files and directories currently installed.)
Preparing to replace compiz-core 1:0.8.4-0ubuntu15 (using .../compiz-core_1%3a0.8.4-0ubuntu15.1_i386.deb) ...
Unpacking replacement compiz-core ...
dpkg-deb (subprocess): error in buffer_read(stream): failed to write to pipe in copy: Input/output error
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing /var/cache/apt/archives/compiz-core_1%3a0.8.4-0ubuntu15.1_i386.deb (--unpack):
 short read in buffer_copy (backend dpkg-deb during `./usr/bin/compiz')
No apport report written because the error message indicates a dpkg I/O error
                                                                             Preparing to replace libcamel1.2-14 2.28.3.1-0ubuntu2 (using .../libcamel1.2-14_2.28.3.1-0ubuntu3_i386.deb) ...
Unpacking replacement libcamel1.2-14 ...
dpkg-deb (subprocess): error in buffer_read(stream): failed to write to pipe in copy: Input/output error
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing /var/cache/apt/archives/libcamel1.2-14_2.28.3.1-0ubuntu3_i386.deb (--unpack):
 short read in buffer_copy (backend dpkg-deb during `./usr/lib/libcamel-1.2.so.14.0.1')
No apport report written because the error message indicates a dpkg I/O error
                                                                             Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/compiz-core_1%3a0.8.4-0ubuntu15.1_i386.deb
 /var/cache/apt/archives/libcamel1.2-14_2.28.3.1-0ubuntu3_i386.deb
E: Sub-process /usr/bin/dpkg ret
```

---

### Post by Runaway1956 on 2010-10-07
> **plucky said:**
> It seems to be having problems reading linux-headers-2.6.31-20.list.

You could from a terminal ```
sudo mv /var/lib/dpkg/info/linux-headers-2.6.31-20.list /var/lib/dpkg/info/linux-headers-2.6.31-20.list.old
```

Then open synaptic package manager and search for **linux-headers-2.6.31.20** and reinstall which will recreate the list.It will complain that the file is missing,but it will then recreate it.

Good Luck



Plucky, you are my hero for the day.  I attempted to install updates half a dozen times, using Synaptic, Aptitude, Apt-get, and was pretty well stumped.  A quick google for key words from the error message brought me here.  

root@ubuntu-guy:/var/lib/dpkg/info# mv /var/lib/dpkg/info/libgssrpc4.list /var/lib/dpkg/info/libgssrpc4.list.old

My next attempt installed all updates, no problems at all.

Thank you, thank you, thank you!

---

