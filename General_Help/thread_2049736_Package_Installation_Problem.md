---
title: "Package Installation Problem"
date: 2012-08-29
forum: General Help
---

### Post by Thanduel on 2012-08-29
Hi

I was downloading the oracle-java7-installer via aptitude when the download was interrupted.

Aptitude has been unable to recover from the interruption and now everytime I run aptitude full-upgrade I get this:


> sha256sum mismatch jdk-7u3-linux-i586.tar.gz
Oracle JDK 7 is NOT installed.
dpkg: error processing oracle-java7-installer (--configure):
 subprocess installed post-installation script returned error exit status 1Any help resolving this would be greatly appreciated.

---

### Post by ajgreeny on 2012-08-29
Try ```
sudo dpkg --configure -a
``` and if that does not do the trick try ```
sudo apt-get -f install
```

---

### Post by Thanduel on 2012-08-29
Thanks for your response, the following is the result I'm afraid neither suggestion worked.

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up oracle-java7-installer (7u3-0~eugenesan~precise4) ...
Downloading...
--2012-08-30 03:57:30--  [http://download.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz](http://download.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz)
Resolving download.oracle.com (download.oracle.com)... 196.33.166.232
Connecting to download.oracle.com (download.oracle.com)|196.33.166.232|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz](https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz) [following]
--2012-08-30 03:57:30--  [https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz](https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz)
Resolving edelivery.oracle.com (edelivery.oracle.com)... 95.101.166.174
Connecting to edelivery.oracle.com (edelivery.oracle.com)|95.101.166.174|:443... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [http://download.oracle.com/errors/download-fail-1505220.html](http://download.oracle.com/errors/download-fail-1505220.html) [following]
--2012-08-30 03:57:31--  [http://download.oracle.com/errors/download-fail-1505220.html](http://download.oracle.com/errors/download-fail-1505220.html)
Connecting to download.oracle.com (download.oracle.com)|196.33.166.232|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 5307 (5,2K) [text/html]
Saving to: `./jdk-7u3-linux-i586.tar.gz'

     0K .....                                                 100%  278K=0,02s

2012-08-30 03:57:31 (278 KB/s) - `./jdk-7u3-linux-i586.tar.gz' saved [5307/5307]

Download done.
sha256sum mismatch jdk-7u3-linux-i586.tar.gz
Oracle JDK 7 is NOT installed.
dpkg: error processing oracle-java7-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 oracle-java7-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)



---

### Post by ajgreeny on 2012-08-30
Not being an Oracle-java user any more, I don't think I can help you further on this, other than suggesting you try to remove the problem archive package from wherever it now is in your system, and then try the installation again from the start.

Your current archive is obviously a bad one, so there is no point trying to install that again.

---

