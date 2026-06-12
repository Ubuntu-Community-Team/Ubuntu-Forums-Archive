---
title: "testdisk install hangs"
date: 2011-06-17
forum: General Help
---

### Post by iconoclast hero on 2011-06-17
I started with 
```
sudo apt-get install testdisk
```
it hung so I hit Ctrl-Z then ps -a and found the process and
```
sudo kill -9 PID
```
I went and deleted the lock file in /var/lib/dpkg/ on the install and ran 
```
sudo dpkg --configure -a
```  
I rebooted and it is still hanging when I do a sudo apt-get upgrade it still hangs at testdisk:
```
Preconfiguring packages ...
(Reading database ... 
dpkg: warning: files list file for package `testdisk' missing, assuming package has no files currently installed.
(Reading database ... 159122 files and directories currently installed.)
Preparing to replace testdisk 6.11-1 (using .../testdisk_6.11-1_i386.deb) ...
Unpacking replacement testdisk ...

```

I tried to uninstall it via the package manager and it hangs there too...

Any idea what to do?  I'm in 10.10...and I think this is the only time I've had an install hang...

---

### Post by tgalati4 on 2011-06-17
sudo apt-get clean
sudo apt-get purge testdisk
sudo apt-get install testdisk

---

### Post by iconoclast hero on 2011-06-17
> **tgalati4 said:**
> sudo apt-get clean
sudo apt-get purge testdisk
sudo apt-get install testdisk

Nope:
```
E: Unable to lock the download directory
root@pc:~# sudo apt-get clean
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory
root@pc:~# sudo rm /var/cache/apt/archives/lock
root@pc:~# sudo apt-get clean
root@pc:~# sudo apt-get remove testdisk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  testdisk
0 upgraded, 0 newly installed, 1 to remove and 14 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? 
dpkg: error processing testdisk (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 testdisk
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by wildmanne39 on 2011-06-18
> **iconoclast hero said:**
> Nope:
```
E: Unable to lock the download directory
root@pc:~# sudo apt-get clean
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory
root@pc:~# sudo rm /var/cache/apt/archives/lock
root@pc:~# sudo apt-get clean
root@pc:~# sudo apt-get remove testdisk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  testdisk
0 upgraded, 0 newly installed, 1 to remove and 14 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? 
dpkg: error processing testdisk (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 testdisk
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
Hi, I have seen other people with that problem and they installed the package completely then uninstalled it, they had to use the force command. I am not saying you should use the force command that is something you should only do as a last resort.

---

### Post by wildmanne39 on 2011-06-18
Hi, you can also try
```
sudo apt-get install -f install
```
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by iconoclast hero on 2011-06-18
> **wildmanne39 said:**
> Hi, you can also try
```
sudo apt-get install -f install
``````
sudo apt-get update && sudo apt-get upgrade
```

I can't figure out how to use the dpkg --force command...  the suggestion above did not work:

```
root@pc:~# apt-get install -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package install
root@pc:~# apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  testdisk
The following packages will be upgraded:
  testdisk
1 upgraded, 0 newly installed, 0 to remove and 14 not upgraded.
1 not fully installed or removed.
Need to get 0B/1,547kB of archives.
After this operation, 4,784kB of additional disk space will be used.
Do you want to continue [Y/n]? 
(Reading database ... 
dpkg: warning: files list file for package `testdisk' missing, assuming package has no files currently installed.
(Reading database ... 159122 files and directories currently installed.)
Preparing to replace testdisk 6.11-1 (using .../testdisk_6.11-1_i386.deb) ...
Unpacking replacement testdisk ...

```

and...  wait for it...  hangs.

from dpkg-query -l:
```

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
iHR testdisk       6.11-1         (no description available)

```

When I try dpkg --force-remove-reinstreq testdisk I get
```
dpkg: need an action option

```
I don't understand what more of an action it needs than remove-reinstreq.

---

### Post by iconoclast hero on 2011-06-18
```
dpkg --remove --force-remove-reinstreq testdisk
```
from [http://www.ubuntugeek.com/package-installation-error-and-solution.html](http://www.ubuntugeek.com/package-installation-error-and-solution.html) got rid of the testdisk problem...  unfortunately, there seems to be a larger problem unpacking files:

```
sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  flashplugin-installer flashplugin-nonfree grub-common grub-pc
  icedtea-6-jre-cacao icedtea6-plugin libxml2 libxml2-utils openjdk-6-jre
  openjdk-6-jre-headless openjdk-6-jre-lib python-libxml2
  ttf-symbol-replacement-wine1.3 wine1.3
14 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 50.3MB of archives.
After this operation, 319kB of additional disk space will be used.
Do you want to continue [Y/n]? 
Get:1 http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ maverick/main ttf-symbol-replacement-wine1.3 all 1.3.22-0ubuntu1~ppa1~maverick1 [59.4kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main libxml2 i386 2.7.7.dfsg-4ubuntu0.2 [824kB]
Get:3 http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ maverick/main wine1.3 i386 1.3.22-0ubuntu1~ppa1~maverick1 [12.3MB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse flashplugin-installer i386 10.3.181.26ubuntu0.10.10.1 [20.6kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse flashplugin-nonfree i386 10.3.181.26ubuntu0.10.10.1 [1,768B]
Get:6 http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main grub-pc i386 1.98+20100804-5ubuntu3.3 [788kB]
Get:7 http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main grub-common i386 1.98+20100804-5ubuntu3.3 [1,547kB]
Get:8 http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main libxml2-utils i386 2.7.7.dfsg-4ubuntu0.2 [89.5kB]
Get:9 http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main icedtea6-plugin i386 6b20-1.9.8-0ubuntu1~10.10.1 [78.7kB]
Get:10 http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main icedtea-6-jre-cacao i386 6b20-1.9.8-0ubuntu1~10.10.1 [417kB]
Get:11 http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main openjdk-6-jre-lib all 6b20-1.9.8-0ubuntu1~10.10.1 [6,156kB]
Get:12 http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main openjdk-6-jre-headless i386 6b20-1.9.8-0ubuntu1~10.10.1 [27.5MB]
Get:13 http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main openjdk-6-jre i386 6b20-1.9.8-0ubuntu1~10.10.1 [251kB]
Get:14 http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main python-libxml2 i386 2.7.7.dfsg-4ubuntu0.2 [217kB]
Fetched 50.3MB in 1min 23s (599kB/s)                                           
Preconfiguring packages ...
(Reading database ... 159122 files and directories currently installed.)
Preparing to replace ttf-symbol-replacement-wine1.3 1.3.21-0ubuntu1~maverick1~ppa2 (using .../ttf-symbol-replacement-wine1.3_1.3.22-0ubuntu1~ppa1~maverick1_all.deb) ...
Unpacking replacement ttf-symbol-replacement-wine1.3 ...

```

This hangs as well...  what should I look for to troubleshoot this?

---

### Post by iconoclast hero on 2011-06-18
I'm moving this to a more descriptive thread:  [http://ubuntuforums.org/showthread.php?p=10953366#post10953366](http://ubuntuforums.org/showthread.php?p=10953366#post10953366)

---

### Post by bapoumba on 2011-06-18
Thread closed.

---

