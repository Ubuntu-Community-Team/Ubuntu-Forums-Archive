---
title: "Java hell"
date: 2012-07-19
forum: General Help
---

### Post by Fergus138 on 2012-07-19
Hello, I am relatively new to Ubuntu and while I am liking the multiboot Ubuntu/Win7 setup that I have, the Ubuntu side of things is giving me some real headaches installing Java.  I have Precise Pangolin and am getting this error:
installArchives() failed: Setting up oracle-java7-installer (7u3-0~eugenesan~precise4) ... 
Downloading... 
--2012-07-19 13:04:38--  [http://download.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz](http://download.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz) 
Resolving download.oracle.com (download.oracle.com)... 23.67.247.107, 23.67.247.106 
Connecting to download.oracle.com (download.oracle.com)|23.67.247.107|:80... connected. 
HTTP request sent, awaiting response... 302 Moved Temporarily 
Location: [https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz](https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz) [following] 
--2012-07-19 13:04:38--  [https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz](https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz) 
Resolving edelivery.oracle.com (edelivery.oracle.com)... 23.2.62.174 
Connecting to edelivery.oracle.com (edelivery.oracle.com)|23.2.62.174|:443... connected. 
HTTP request sent, awaiting response... 302 Moved Temporarily 
Location: [http://download.oracle.com/errors/download-fail-1505220.html](http://download.oracle.com/errors/download-fail-1505220.html) [following] 
--2012-07-19 13:04:39--  [http://download.oracle.com/errors/download-fail-1505220.html](http://download.oracle.com/errors/download-fail-1505220.html) 
Connecting to download.oracle.com (download.oracle.com)|23.67.247.107|:80... connected. 
HTTP request sent, awaiting response... 200 OK 
Length: 5307 (5.2K) [text/html] 
Saving to: `./jdk-7u3-linux-x64.tar.gz.19' 
 
     0K .....                                                 100%% 71.2K=0.07s 
 
2012-07-19 13:04:39 (71.2 KB/s) - `./jdk-7u3-linux-x64.tar.gz.19' saved [5307/5307] 
 
Download done. 
sha256sum mismatch jdk-7u3-linux-x64.tar.gz 
Oracle JDK 7 is NOT installed. 
dpkg: error processing oracle-java7-installer (--configure): 
 subprocess installed post-installation script returned error exit status 1 
No apport report written because MaxReports is reached already
Errors were encountered while processing: 
 oracle-java7-installer 
Error in function:  
Setting up oracle-java7-installer (7u3-0~eugenesan~precise4) ... 
Downloading... 
--2012-07-19 13:04:40--  [http://download.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz](http://download.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz) 
Resolving download.oracle.com (download.oracle.com)... 23.67.247.107, 23.67.247.106 
Connecting to download.oracle.com (download.oracle.com)|23.67.247.107|:80... connected. 
HTTP request sent, awaiting response... 302 Moved Temporarily 
Location: [https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz](https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz) [following] 
--2012-07-19 13:04:40--  [https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz](https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz) 
Resolving edelivery.oracle.com (edelivery.oracle.com)... 23.2.62.174 
Connecting to edelivery.oracle.com (edelivery.oracle.com)|23.2.62.174|:443... connected. 
HTTP request sent, awaiting response... 302 Moved Temporarily 
Location: [http://download.oracle.com/errors/download-fail-1505220.html](http://download.oracle.com/errors/download-fail-1505220.html) [following] 
--2012-07-19 13:04:41--  [http://download.oracle.com/errors/download-fail-1505220.html](http://download.oracle.com/errors/download-fail-1505220.html) 
Connecting to download.oracle.com (download.oracle.com)|23.67.247.107|:80... connected. 
HTTP request sent, awaiting response... 200 OK 
Length: 5307 (5.2K) [text/html] 
Saving to: `./jdk-7u3-linux-x64.tar.gz.20' 
 
     0K .....                                                 100%% 2.73M=0.002s 
 
2012-07-19 13:04:41 (2.73 MB/s) - `./jdk-7u3-linux-x64.tar.gz.20' saved [5307/5307] 
 
Download done. 
sha256sum mismatch jdk-7u3-linux-x64.tar.gz 
Oracle JDK 7 is NOT installed. 
dpkg: error processing oracle-java7-installer (--configure): 
 subprocess installed post-installation script returned error exit status 1

If you could PLEASE direct me as to how I can get Ubuntu to stop rejecting Java, I'd be very grateful.  Thank you for your time

---

### Post by raja.genupula on 2012-07-19
[http://askubuntu.com/questions/126372/sha256sum-mismatch-jdk-7u3-linux-x64-tar-gz-error-when-trying-to-install-orac](http://askubuntu.com/questions/126372/sha256sum-mismatch-jdk-7u3-linux-x64-tar-gz-error-when-trying-to-install-orac)

---

### Post by QIII on 2012-07-19
The Eugene San PPA is, unfortunately, borked.  This is a bit sad, since Eugene San helped with some of the scripting used by webupd8's method.  If you notice, it's trying to install Oracle Java 7 update 3, when update 5 is current.

A similar suggestion for removing it can at the Java link in my signature, which has a specific section about the Eugene San PPA.

I would recommend that link rather than raja's (no disrespect intended, raja!) because the askubuntu answer uses the rm command, which can be dangerous.

The suggestion I give for removing the offending Eugene San bits is:

```
$ sudo apt-get remove --purge oracle-java7-installer*  
$ sudo apt-get install ppa-purge  
$ sudo ppa-purge ppa:eugenesan/java 
$ sudo apt-get clean  
$ sudo apt-get update
```

---

