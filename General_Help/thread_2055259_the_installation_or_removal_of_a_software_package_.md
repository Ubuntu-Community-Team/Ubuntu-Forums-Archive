---
title: "the installation or removal of a software package failed ubuntu 12.04"
date: 2012-09-08
forum: General Help
---

### Post by LuisNgo on 2012-09-08
When I install or remove some softwares, I usually face to this problem. Please tell me what it is and how I can fix this.
Thanks

installArchives() failed: Selecting previously unselected package videolan-doc.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 148045 files and directories currently installed.)
Unpacking videolan-doc (from .../videolan-doc_20070626-1_all.deb) ...
Setting up oracle-java7-installer (7u3-0~eugenesan~precise4) ...
Downloading...
--2012-09-09 09:56:53--  [http://download.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz](http://download.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz)
Resolving download.oracle.com (download.oracle.com)... 60.254.131.64, 60.254.131.72
Connecting to download.oracle.com (download.oracle.com)|60.254.131.64|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz](https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz) [following]
--2012-09-09 09:56:53--  [https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz](https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz)
Resolving edelivery.oracle.com (edelivery.oracle.com)... 72.247.118.174
Connecting to edelivery.oracle.com (edelivery.oracle.com)|72.247.118.174|:443... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [http://download.oracle.com/errors/download-fail-1505220.html](http://download.oracle.com/errors/download-fail-1505220.html) [following]
--2012-09-09 09:56:54--  [http://download.oracle.com/errors/download-fail-1505220.html](http://download.oracle.com/errors/download-fail-1505220.html)
Connecting to download.oracle.com (download.oracle.com)|60.254.131.64|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 5307 (5.2K) [text/html]
Saving to: `./jdk-7u3-linux-i586.tar.gz'

     0K .....                                                 100%  124K=0.04s

2012-09-09 09:56:54 (124 KB/s) - `./jdk-7u3-linux-i586.tar.gz' saved [5307/5307]

Download done.
sha256sum mismatch jdk-7u3-linux-i586.tar.gz
Oracle JDK 7 is NOT installed.
dpkg: error processing oracle-java7-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
Setting up videolan-doc (20070626-1) ...
Errors were encountered while processing:
 oracle-java7-installer
Error in function:

After this notification, the program is still installed but I dont know whether it work properly or get some problems

---

