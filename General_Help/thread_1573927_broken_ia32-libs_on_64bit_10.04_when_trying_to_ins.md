---
title: "broken ia32-libs on 64bit 10.04 when trying to install Flash"
date: 2010-09-13
forum: General Help
---

### Post by wwwbrowse on 2010-09-13
My 32bit installation of flash broke some time ago [http://ubuntuforums.org/showthread.php?t=1559647]("http://ubuntuforums.org/showthread.php?t=1559647"). Today I again tried to repair it. when doing "apt-get -f install" to reinstall ia32-libs which had been uninstalled I get the following error (at bottom of terminal)

```
david@david-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies...Done
The following extra packages will be installed:
  ia32-libs
The following NEW packages will be installed
  ia32-libs
0 upgraded, 1 newly installed, 0 to remove and 29 not upgraded.
3 not fully installed or removed.
Need to get 36.6MB of archives.
After this operation, 159MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 http://ubuntu.virginmedia.com/archive/ lucid-updates/universe ia32-libs 2.7ubuntu26 [36.6MB]
Fetched 36.6MB in 1min 54s (318kB/s)                                           
(Reading database ... 249401 files and directories currently installed.)
Unpacking ia32-libs (from .../ia32-libs_2.7ubuntu26_amd64.deb) ...
Replaced by files in installed package lib32ncurses5 ...
dpkg: error processing /var/cache/apt/archives/ia32-libs_2.7ubuntu26_amd64.deb (--unpack):
 unable to create `/lib32/libacl.so.1.1.0.dpkg-new' (while processing `./lib32/libacl.so.1.1.0'): No such file or directory
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/ia32-libs_2.7ubuntu26_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
david@david-desktop:~$ 

```

What is this error and how do I repair it. I feel this has been the problem all along. Many thanks for your help.

---

### Post by wwwbrowse on 2010-09-13
I've just noticed that the following error:-

```
dpkg: error processing /var/cache/apt/archives/ia32-libs_2.7ubuntu26_amd64.deb (--unpack):
 unable to create `/lib32/libacl.so.1.1.0.dpkg-new' (while processing `./lib32/libacl.so.1.1.0'): No such file or directory
```

is looking for directory /lib32/ which doesn't exist. lib and lib64 exist only.

---

### Post by wwwbrowse on 2010-09-13
lib32 is there it was just hidden in nautilus.

---

### Post by wwwbrowse on 2010-09-13
sorry no /lib32, only /lib and /lib64

---

