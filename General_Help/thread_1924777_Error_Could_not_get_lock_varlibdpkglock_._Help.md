---
title: "Error Could not get lock /var/lib/dpkg/lock . Help"
date: 2012-02-13
forum: General Help
---

### Post by asifnaz on 2012-02-13
```
sudo apt-get install gimp
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```and

```
sudo apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  icedtea6-plugin ttf-mscorefonts-installer ubuntu-restricted-addons unrar
The following NEW packages will be installed:
  icedtea6-plugin ubuntu-restricted-addons ubuntu-restricted-extras unrar
The following packages will be upgraded:
  ttf-mscorefonts-installer
1 upgraded, 4 newly installed, 0 to remove and 357 not upgraded.
11 not fully installed or removed.
Need to get 0B/230kB of archives.
After this operation, 823kB of additional disk space will be used.
Do you want to continue [Y/n]? y
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
(Reading database ... 
dpkg: warning: files list file for package `ttf-mscorefonts-installer' missing, assuming package has no files currently installed.
(Reading database ... 125352 files and directories currently installed.)
Preparing to replace ttf-mscorefonts-installer 3.2ubuntu2 (using .../ttf-mscorefonts-installer_3.2ubuntu2_all.deb) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing /var/cache/apt/archives/ttf-mscorefonts-installer_3.2ubuntu2_all.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Selecting previously deselected package ubuntu-restricted-addons.
Unpacking ubuntu-restricted-addons (from .../ubuntu-restricted-addons_4_i386.deb) ...
Selecting previously deselected package ubuntu-restricted-extras.
Unpacking ubuntu-restricted-extras (from .../ubuntu-restricted-extras_42_i386.deb) ...
Selecting previously deselected package unrar.
Unpacking unrar (from .../unrar_1%3a3.9.10-1_i386.deb) ...
Selecting previously deselected package icedtea6-plugin.
Unpacking icedtea6-plugin (from .../icedtea6-plugin_6b20-1.9.10-0ubuntu1~10.10.3_i386.deb) ...
Errors were encountered while processing:
 /var/cache/apt/archives/ttf-mscorefonts-installer_3.2ubuntu2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by cortman on 2012-02-13
These are two unrelated problems. The first is caused by another program using apt or dpkg. You can fix it by logging out and back in, which will end all the currently running processes. Or you can find the processes by running

```
ps -ef | grep apt
```

and kill all apt processes.

---

