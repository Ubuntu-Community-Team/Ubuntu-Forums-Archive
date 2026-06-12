---
title: "apt-get install error"
date: 2010-08-21
forum: General Help
---

### Post by type8code0 on 2010-08-21
Hi, 

I'm having a problem when trying to perform apt-get install command. Below is the error message. Any help would be highly appreciated.

Thanks

> type8code0@desktop:~$ sudo apt-get install
[sudo] password for type8code0:
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  zekr: Depends: libswt-gtk-3.6-java but it is not installed
E: Unmet dependencies. Try using -f.
type8code0@desktop:~$

> type8code0@desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-21 libswt-cairo-gtk-3.5-jni libswt-gtk-3.5-jni libswt-mozilla-gtk-3.5-jni
  linux-headers-2.6.32-21-generic libswt-gtk-3.5-java
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libswt-gtk-3.6-java
Suggested packages:
  libswt-gtk-3.6-java-gcj
The following NEW packages will be installed:
  libswt-gtk-3.6-java
0 upgraded, 1 newly installed, 0 to remove and 5 not upgraded.
1 not fully installed or removed.
Need to get 0B/1,583kB of archives.
After this operation, 1,769kB of additional disk space will be used.
Do you want to continue [Y/n]?
(Reading database ... 162391 files and directories currently installed.)
Unpacking libswt-gtk-3.6-java (from .../libswt-gtk-3.6-java_3.6-1~ppa4_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libswt-gtk-3.6-java_3.6-1~ppa4_i386.deb (--unpack):
 trying to overwrite '/usr/share/java/swt.jar', which is also in package libswt-gtk-3.5-java 0:3.5.2-1~ppa1
Errors were encountered while processing:
 /var/cache/apt/archives/libswt-gtk-3.6-java_3.6-1~ppa4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
type8code0@desktop:~$


> type8code0@desktop:~$ sudo apt-get update
0% [Connecting to my.archive.ubuntu.com] [Connecting to security.ubuntu.com] [Co
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg
Ign [http://ppa.launchpad.net/zekr/ubuntu/](http://ppa.launchpad.net/zekr/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg
Ign [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Sources
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid Release.gpg
Ign [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Ign [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Ign [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid-updates Release.gpg
Ign [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid Release
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid-updates Release
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid/main Packages
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid/restricted Packages
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid/main Sources
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid/restricted Sources
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid/universe Packages
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid/universe Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://dl.google.com](http://dl.google.com) stable Release.gpg
  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid/multiverse Sources
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid-updates/main Packages
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid-updates/main Sources
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid-updates/multiverse Packages
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid-updates/multiverse Sources
Ign [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable/main Translation-en_US
Get:1 [http://dl.google.com](http://dl.google.com) stable Release [2,544B]
Get:2 [http://dl.google.com](http://dl.google.com) stable/main Packages [1,063B]
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
Fetched 3,607B in 57s (63B/s)
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://dl.google.com/linux/deb/dists/stable/Release.gpg](http://dl.google.com/linux/deb/dists/stable/Release.gpg)  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download, they have been ignored, or old ones used instead.
type8code0@desktop:~$

---

### Post by sikander3786 on 2010-08-21
Try

```

sudo dpkg --remove libswt-gtk-3.6-java_3.6-1~ppa4_i386.deb

```

and then

```

sudo apt-get update && sudo apt-get upgrade

```

---

### Post by dino99 on 2010-08-21
open synaptic (system admin synaptic) repo tab : deactivate all non genuine lucid repo (google for example seen into your post above)

"sudo apt-get install" is the command to install a "package", so you might follow this command by the exact package name:

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

note: if the installer complaint about "unmet dependencies", read the sticky into this forum first, and dont install it for the moment, the missed dependencies are not ready , so be patient

---

### Post by type8code0 on 2010-08-21
> **sikander3786 said:**
> Try

```

sudo dpkg --remove libswt-gtk-3.6-java_3.6-1~ppa4_i386.deb

```

and then

```

sudo apt-get update && sudo apt-get upgrade

```
Thanks sikander3786 :)
However, it's not working

> type8code0@desktop:~$ sudo dpkg --remove libswt-gtk-3.6-java_3.6-1~ppa4_i386.deb
[sudo] password for type8code0:
dpkg: you must specify packages by their own names, not by quoting the names of
the files they come in

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
type8code0@desktop:~$


> type8code0@desktop:~$ sudo apt-get update && sudo apt-get upgrade
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg
Ign [http://ppa.launchpad.net/zekr/ubuntu/](http://ppa.launchpad.net/zekr/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg
Ign [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Sources
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]
Ign [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable/main Translation-en_US
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [2,544B]
Get:3 [http://dl.google.com](http://dl.google.com) stable/main Packages [1,063B]
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid Release.gpg
Ign [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Ign [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Ign [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid-updates Release.gpg
Ign [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid Release
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid-updates Release
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid/main Packages
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid/restricted Packages
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid/main Sources
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid/restricted Sources
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid/universe Packages
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid/universe Sources
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid/multiverse Sources
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid-updates/main Packages
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid-updates/main Sources
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid-updates/multiverse Packages
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid-updates/multiverse Sources
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg [189B]
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
Fetched 3,985B in 37s (107B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  zekr: Depends: libswt-gtk-3.6-java but it is not installed
E: Unmet dependencies. Try using -f.
type8code0@desktop:~$

---

### Post by sikander3786 on 2010-08-21
Have you tried dino99's instructions and

```

sudo apt-get install libswt-gtk-3.6-java

```

---

### Post by type8code0 on 2010-08-21
> **dino99 said:**
> open synaptic (system admin synaptic) repo tab : deactivate all non genuine lucid repo (google for example seen into your post above)

"sudo apt-get install" is the command to install a "package", so you might follow this command by the exact package name:

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

note: if the installer complaint about "unmet dependencies", read the sticky into this forum first, and dont install it for the moment, the missed dependencies are not ready , so be patient
Thanks dino99 for your explanation, :)

I still get the "unmet dependencies" ... guess I need to wait isn't it?
I'm very new to this forum, can you guide me where is the sticky?

Btw, below is the output from the commands that I tried
> type8code0@desktop:~$ sudo apt-get clean

type8code0@desktop:~$ sudo apt-get autoclean
Reading package lists... Done
Building dependency tree
Reading state information... Done

type8code0@desktop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  zekr: Depends: libswt-gtk-3.6-java but it is not installed
E: Unmet dependencies. Try using -f.

type8code0@desktop:~$ sudo apt-get update
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg
Ign [http://ppa.launchpad.net/zekr/ubuntu/](http://ppa.launchpad.net/zekr/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg
Ign [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Sources
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]
Ign [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable/main Translation-en_US
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [2,544B]
Get:3 [http://dl.google.com](http://dl.google.com) stable/main Packages [1,063B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid Release.gpg
Ign [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Ign [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Ign [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid-updates Release.gpg
Ign [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid Release
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid-updates Release
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid/main Packages
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid/restricted Packages
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid/main Sources
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid/restricted Sources
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid/universe Packages
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid/universe Sources
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid/multiverse Sources
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid-updates/main Packages
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid-updates/main Sources
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid-updates/multiverse Packages
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) lucid-updates/multiverse Sources
Fetched 3,796B in 43s (86B/s)
Reading package lists... Done
type8code0@desktop:~$

type8code0@desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-21 libswt-cairo-gtk-3.5-jni libswt-gtk-3.5-jni libswt-mozilla-gtk-3.5-jni
  linux-headers-2.6.32-21-generic libswt-gtk-3.5-java
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libswt-gtk-3.6-java
Suggested packages:
  libswt-gtk-3.6-java-gcj
The following NEW packages will be installed:
  libswt-gtk-3.6-java
0 upgraded, 1 newly installed, 0 to remove and 5 not upgraded.
1 not fully installed or removed.
Need to get 1,583kB of archives.
After this operation, 1,769kB of additional disk space will be used.
Do you want to continue [Y/n]?
Get:1 [http://ppa.launchpad.net/zekr/ubuntu/](http://ppa.launchpad.net/zekr/ubuntu/) lucid/main libswt-gtk-3.6-java 3.6-1~ppa4 [1,583kB]
Fetched 1,583kB in 46s (34.0kB/s)
(Reading database ... 162391 files and directories currently installed.)
Unpacking libswt-gtk-3.6-java (from .../libswt-gtk-3.6-java_3.6-1~ppa4_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libswt-gtk-3.6-java_3.6-1~ppa4_i386.deb (--unpack):
 trying to overwrite '/usr/share/java/swt.jar', which is also in package libswt-gtk-3.5-java 0:3.5.2-1~ppa1
Errors were encountered while processing:
 /var/cache/apt/archives/libswt-gtk-3.6-java_3.6-1~ppa4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
type8code0@desktop:~$

type8code0@desktop:~$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of zekr:
 zekr depends on libswt-gtk-3.6-java; however:
  Package libswt-gtk-3.6-java is not installed.
dpkg: error processing zekr (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 zekr
type8code0@desktop:~$

---

### Post by type8code0 on 2010-08-21
> **sikander3786 said:**
> Have you tried dino99's instructions and

```

sudo apt-get install libswt-gtk-3.6-java

```
Yes, and I still get the same error message
> type8code0@desktop:~$ **sudo apt-get install libswt-gtk-3.6-java**
Reading package lists... Done
Building dependency tree
Reading state information... Done
[B]The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-21 libswt-cairo-gtk-3.5-jni libswt-gtk-3.5-jni libswt-mozilla-gtk-3.5-jni
  linux-headers-2.6.32-21-generic libswt-gtk-3.5-java
Use 'apt-get autoremove' to remove them.[/B]
Suggested packages:
  libswt-gtk-3.6-java-gcj
The following NEW packages will be installed:
  libswt-gtk-3.6-java
0 upgraded, 1 newly installed, 0 to remove and 5 not upgraded.
1 not fully installed or removed.
Need to get 0B/1,583kB of archives.
After this operation, 1,769kB of additional disk space will be used.
(Reading database ... 162391 files and directories currently installed.)
Unpacking libswt-gtk-3.6-java (from .../libswt-gtk-3.6-java_3.6-1~ppa4_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libswt-gtk-3.6-java_3.6-1~ppa4_i386.deb (--unpack):
 trying to overwrite '/usr/share/java/swt.jar', which is also in package libswt-gtk-3.5-java 0:3.5.2-1~ppa1
Errors were encountered while processing:
 /var/cache/apt/archives/libswt-gtk-3.6-java_3.6-1~ppa4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
type8code0@desktop:~$

---

### Post by dino99 on 2010-08-21
"unmet dependencies":

[http://ubuntuforums.org/showthread.php?t=1479146](http://ubuntuforums.org/showthread.php?t=1479146)

note: sometimes when things seem to be broken (cant install), one of the solution is, into synaptic, to remove/purge (right click) the installed broken package(s) then reinstall them

---

### Post by deserthowler on 2010-08-21
In synaptic, click on the status view and see if it shows broken packages.  There should also be a notification at the bottom of the window showing if there are any broken packages.  If so, just fix broken.

Earl

---

