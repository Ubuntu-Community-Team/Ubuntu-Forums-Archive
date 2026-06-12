---
title: "Getting rid of Oracle crap"
date: 2012-06-24
forum: General Help
---

### Post by Jeroen De Dauw on 2012-06-24
I tried installing the Java distribution from Oracle a while back because I wanted to try an IDE that does not support OpenJDK. The installation failed (since instead of getting the package, apt-get is getting a page that whines about having to agree to Oracles terms of service (******* lawyers...)) and now I have this broken thing that I don't know how to get rid of.

As far as I can tell, there is nothing actually installed, but somehow the package is staged for install, and every time I install something else or update something, apt-get also tries to install the broken stuff and throws errors at me, such as this:

> Do you want to continue [Y/n]? Y
Setting up oracle-java7-installer (7u3-0~eugenesan~precise4) ...
Downloading...
--2012-06-24 23:39:18--  [http://download.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz](http://download.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz)
Resolving download.oracle.com (download.oracle.com)... 80.154.79.24, 80.154.79.33
Connecting to download.oracle.com (download.oracle.com)|80.154.79.24|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz](https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz) [following]
--2012-06-24 23:39:18--  [https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz](https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz)
Resolving edelivery.oracle.com (edelivery.oracle.com)... 2.18.250.174
Connecting to edelivery.oracle.com (edelivery.oracle.com)|2.18.250.174|:443... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [http://download.oracle.com/errors/download-fail-1505220.html](http://download.oracle.com/errors/download-fail-1505220.html) [following]
--2012-06-24 23:39:19--  [http://download.oracle.com/errors/download-fail-1505220.html](http://download.oracle.com/errors/download-fail-1505220.html)
Connecting to download.oracle.com (download.oracle.com)|80.154.79.24|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 5307 (5.2K) [text/html]
Saving to: `./jdk-7u3-linux-x64.tar.gz'

     0K .....                                                 100% 1.09M=0.005s

2012-06-24 23:39:20 (1.09 MB/s) - `./jdk-7u3-linux-x64.tar.gz' saved [5307/5307]

Download done.
sha256sum mismatch jdk-7u3-linux-x64.tar.gz
Oracle JDK 7 is NOT installed.
dpkg: error processing oracle-java7-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 oracle-java7-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

Anyone an idea how to get rid of this?

---

### Post by sammiev on 2012-06-24
I use Oracle always as it works. Installed correctly you will never have problems. [This]("https://sites.google.com/site/easylinuxtipsproject/java") is how I install it. :)

---

### Post by pbrane on 2012-06-24
If you installed Oracle java from a ppa then you should try running ppa-purge to remove it.

Otherwise make sure you don't have any repositories enabled for Oracle java. then run 
```

sudo apt-get update

```

then try to install whatever you were before.

I had quite a time removing Oracle java from my system. I use OpenJDK 7, it seems to be working with everything so far.

What IDE were you trying to use that wouldn't work with openjdk? With openjdk 7 I have been able to use Netbeans and Eclipse without any issues.

---

### Post by Jeroen De Dauw on 2012-06-30
I think I did remove all repositories I added to try top get this to work.

```
grep ^ /etc/apt/sources.list /etc/apt/sources.list.d/*

/etc/apt/sources.list:# 
/etc/apt/sources.list:
/etc/apt/sources.list:
/etc/apt/sources.list:
/etc/apt/sources.list:# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
/etc/apt/sources.list:# newer versions of the distribution.
/etc/apt/sources.list:deb http://de.archive.ubuntu.com/ubuntu/ precise main restricted
/etc/apt/sources.list:deb-src http://de.archive.ubuntu.com/ubuntu/ precise main restricted
/etc/apt/sources.list:
/etc/apt/sources.list:## Major bug fix updates produced after the final release of the
/etc/apt/sources.list:## distribution.
/etc/apt/sources.list:deb http://de.archive.ubuntu.com/ubuntu/ precise-updates main restricted
/etc/apt/sources.list:deb-src http://de.archive.ubuntu.com/ubuntu/ precise-updates main restricted
/etc/apt/sources.list:
/etc/apt/sources.list:## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
/etc/apt/sources.list:## team. Also, please note that software in universe WILL NOT receive any
/etc/apt/sources.list:## review or updates from the Ubuntu security team.
/etc/apt/sources.list:deb http://de.archive.ubuntu.com/ubuntu/ precise universe
/etc/apt/sources.list:deb-src http://de.archive.ubuntu.com/ubuntu/ precise universe
/etc/apt/sources.list:deb http://de.archive.ubuntu.com/ubuntu/ precise-updates universe
/etc/apt/sources.list:deb-src http://de.archive.ubuntu.com/ubuntu/ precise-updates universe
/etc/apt/sources.list:
/etc/apt/sources.list:## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
/etc/apt/sources.list:## team, and may not be under a free licence. Please satisfy yourself as to 
/etc/apt/sources.list:## your rights to use the software. Also, please note that software in 
/etc/apt/sources.list:## multiverse WILL NOT receive any review or updates from the Ubuntu
/etc/apt/sources.list:## security team.
/etc/apt/sources.list:deb http://de.archive.ubuntu.com/ubuntu/ precise multiverse
/etc/apt/sources.list:deb-src http://de.archive.ubuntu.com/ubuntu/ precise multiverse
/etc/apt/sources.list:deb http://de.archive.ubuntu.com/ubuntu/ precise-updates multiverse
/etc/apt/sources.list:deb-src http://de.archive.ubuntu.com/ubuntu/ precise-updates multiverse
/etc/apt/sources.list:
/etc/apt/sources.list:## N.B. software from this repository may not have been tested as
/etc/apt/sources.list:## extensively as that contained in the main release, although it includes
/etc/apt/sources.list:## newer versions of some applications which may provide useful features.
/etc/apt/sources.list:## Also, please note that software in backports WILL NOT receive any review
/etc/apt/sources.list:## or updates from the Ubuntu security team.
/etc/apt/sources.list:deb http://de.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
/etc/apt/sources.list:deb-src http://de.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
/etc/apt/sources.list:
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu precise-security main restricted
/etc/apt/sources.list:deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu precise-security universe
/etc/apt/sources.list:deb-src http://security.ubuntu.com/ubuntu precise-security universe
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu precise-security multiverse
/etc/apt/sources.list:deb-src http://security.ubuntu.com/ubuntu precise-security multiverse
/etc/apt/sources.list:
/etc/apt/sources.list:## Uncomment the following two lines to add software from Canonical's
/etc/apt/sources.list:## 'partner' repository.
/etc/apt/sources.list:## This software is not part of Ubuntu, but is offered by Canonical and the
/etc/apt/sources.list:## respective vendors as a service to Ubuntu users.
/etc/apt/sources.list:deb http://archive.canonical.com/ubuntu oneiric partner
/etc/apt/sources.list:# deb-src http://archive.canonical.com/ubuntu oneiric partner
/etc/apt/sources.list:
/etc/apt/sources.list:## This software is not part of Ubuntu, but is offered by third-party
/etc/apt/sources.list:## developers who want to ship their latest software.
/etc/apt/sources.list:deb http://extras.ubuntu.com/ubuntu precise main
/etc/apt/sources.list:deb-src http://extras.ubuntu.com/ubuntu precise main
/etc/apt/sources.list.d/dropbox.list.distUpgrade:deb http://linux.dropbox.com/ubuntu oneiric main
/etc/apt/sources.list.d/dropbox.list.save:# deb http://linux.dropbox.com/ubuntu precise main # disabled on upgrade to precise
/etc/apt/sources.list.d/google-talkplugin.list:### THIS FILE IS AUTOMATICALLY CONFIGURED ###
/etc/apt/sources.list.d/google-talkplugin.list:# You may comment out this entry, but any other modifications may be lost.
/etc/apt/sources.list.d/google-talkplugin.list:deb http://dl.google.com/linux/talkplugin/deb/ stable main
/etc/apt/sources.list.d/google-talkplugin.list.save:### THIS FILE IS AUTOMATICALLY CONFIGURED ###
/etc/apt/sources.list.d/google-talkplugin.list.save:# You may comment out this entry, but any other modifications may be lost.
/etc/apt/sources.list.d/google-talkplugin.list.save:deb http://dl.google.com/linux/talkplugin/deb/ stable main
```

However, I am still getting the error:

```
sudo apt-get update ; sudo apt-get upgrade

... stuff ....

Setting up oracle-java7-installer (7u3-0~eugenesan~precise4) ...
Downloading...
--2012-06-30 15:14:02--  http://download.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz
Resolving download.oracle.com (download.oracle.com)... 194.25.95.73, 194.25.95.98
Connecting to download.oracle.com (download.oracle.com)|194.25.95.73|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz [following]
--2012-06-30 15:14:02--  https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz
Resolving edelivery.oracle.com (edelivery.oracle.com)... 2.18.250.174
Connecting to edelivery.oracle.com (edelivery.oracle.com)|2.18.250.174|:443... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: http://download.oracle.com/errors/download-fail-1505220.html [following]
--2012-06-30 15:14:03--  http://download.oracle.com/errors/download-fail-1505220.html
Connecting to download.oracle.com (download.oracle.com)|194.25.95.73|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 5307 (5.2K) [text/html]
Saving to: `./jdk-7u3-linux-x64.tar.gz'

     0K .....                                                 100% 8.71M=0.001s

2012-06-30 15:14:03 (8.71 MB/s) - `./jdk-7u3-linux-x64.tar.gz' saved [5307/5307]

Download done.
sha256sum mismatch jdk-7u3-linux-x64.tar.gz
Oracle JDK 7 is NOT installed.
dpkg: error processing oracle-java7-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 oracle-java7-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Cheesemill on 2012-06-30
There is a problem with the eugenesan PPA which is causing these errors.

For more information about removing the problem installer check out [this]("http://ubuntuforums.org/showpost.php?p=12062816") thread.

After manually removing the the installer and the eugenesan PPA you can install Java using [these]("http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html") instructions.

---

