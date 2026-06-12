---
title: "Oracle JDK 7 NOT installed - error code"
date: 2012-04-29
forum: General Help
---

### Post by che47audio on 2012-04-29
I have getting an error code every time I try to update or install software. Something related to not having oracle JDK 7 installed?
check below:

```
Oracle JDK 7 is NOT installed.
dpkg: error processing oracle-java7-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up lame (3.99.3+repack1-1) ...
Errors were encountered while processing:
 oracle-java7-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

So I have tried to install this with the below command:

```
sudo apt-get install oracle-java7-installer 
```

and get the following any ideas?

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
oracle-java7-installer is already the newest version.
The following packages were automatically installed and are no longer required:
  xmms2-plugin-pulse xmms2-plugin-id3v2 xmms2-plugin-alsa libxmmsclient6
  xmms2-core xmms2-plugin-vorbis xmms2-plugin-mad xmms2-icon xmms2-client-cli
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up oracle-java7-installer (7u3-0~eugenesan~precise4) ...
Downloading...
--2012-04-29 16:42:02--  http://download.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz
Resolving download.oracle.com (download.oracle.com)... 62.24.131.32, 62.24.131.81
Connecting to download.oracle.com (download.oracle.com)|62.24.131.32|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz [following]
--2012-04-29 16:42:03--  https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz
Resolving edelivery.oracle.com (edelivery.oracle.com)... 2.17.250.174
Connecting to edelivery.oracle.com (edelivery.oracle.com)|2.17.250.174|:443... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: http://download.oracle.com/errors/download-fail-1505220.html [following]
--2012-04-29 16:42:03--  http://download.oracle.com/errors/download-fail-1505220.html
Connecting to download.oracle.com (download.oracle.com)|62.24.131.32|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 5307 (5.2K) [text/html]
Saving to: `./jdk-7u3-linux-x64.tar.gz'

     0K .....                                                 100%  659K=0.008s

2012-04-29 16:42:03 (659 KB/s) - `./jdk-7u3-linux-x64.tar.gz' saved [5307/5307]

Download done.
sha256sum mismatch jdk-7u3-linux-x64.tar.gz
Oracle JDK 7 is NOT installed.
dpkg: error processing oracle-java7-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 oracle-java7-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

```


Thanks for looking.

---

### Post by Lindexter on 2012-04-29
> **che47audio said:**
> I have getting an error code every time I try to update or install software. Something related to not having oracle JDK 7 installed?
check below:

```
Oracle JDK 7 is NOT installed.
dpkg: error processing oracle-java7-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up lame (3.99.3+repack1-1) ...
Errors were encountered while processing:
 oracle-java7-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

```So I have tried to install this with the below command:

```
sudo apt-get install oracle-java7-installer 
```and get the following any ideas?

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
oracle-java7-installer is already the newest version.
The following packages were automatically installed and are no longer required:
  xmms2-plugin-pulse xmms2-plugin-id3v2 xmms2-plugin-alsa libxmmsclient6
  xmms2-core xmms2-plugin-vorbis xmms2-plugin-mad xmms2-icon xmms2-client-cli
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up oracle-java7-installer (7u3-0~eugenesan~precise4) ...
Downloading...
--2012-04-29 16:42:02--  http://download.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz
Resolving download.oracle.com (download.oracle.com)... 62.24.131.32, 62.24.131.81
Connecting to download.oracle.com (download.oracle.com)|62.24.131.32|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz [following]
--2012-04-29 16:42:03--  https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz
Resolving edelivery.oracle.com (edelivery.oracle.com)... 2.17.250.174
Connecting to edelivery.oracle.com (edelivery.oracle.com)|2.17.250.174|:443... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: http://download.oracle.com/errors/download-fail-1505220.html [following]
--2012-04-29 16:42:03--  http://download.oracle.com/errors/download-fail-1505220.html
Connecting to download.oracle.com (download.oracle.com)|62.24.131.32|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 5307 (5.2K) [text/html]
Saving to: `./jdk-7u3-linux-x64.tar.gz'

     0K .....                                                 100%  659K=0.008s

2012-04-29 16:42:03 (659 KB/s) - `./jdk-7u3-linux-x64.tar.gz' saved [5307/5307]

Download done.
sha256sum mismatch jdk-7u3-linux-x64.tar.gz
Oracle JDK 7 is NOT installed.
dpkg: error processing oracle-java7-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 oracle-java7-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

```Thanks for looking.

Which PPA are you using?

Use this one instead:

sudo add-apt-repository ppa:webupd8team/java

Do you have your partner repo enabled?

---

### Post by che47audio on 2012-04-29
urrrr, not sure what ppa I'm using. How do I determine this? And what is a partner repo? and how does one enable it? All apologies, I'm new to all this.


Its a new installation of ubuntu 12.04. Does chaning the ppa chnage where my downloads/updates are sourced?

Thanks again.

---

### Post by Etendard7 on 2012-04-29
Hi,

This worked for me:

```

sudo rm /var/lib/dpkg/info/oracle-java7-installer*
sudo apt-get purge oracle-java7-installer*
sudo rm /etc/apt/sources.list.d/*java*
sudo apt-get update
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer

```

(found [here]("http://askubuntu.com/questions/126372/sha256sum-mismatch-jdk-7u3-linux-x64-tar-gz-error-when-trying-to-install-orac"))

---

### Post by cazazo on 2012-04-30
I had the same problem... Here is how it was fixed...
[http://rootzwiki.com/topic/23008-howto-install-java-7-on-ubuntu-1204/]("http://rootzwiki.com/topic/23008-howto-install-java-7-on-ubuntu-1204/")
Hope you have it fixed!

---

### Post by josephmills on 2012-04-30
[http://www.youtube.com/watch?v=dmj24FCZGiY](http://www.youtube.com/watch?v=dmj24FCZGiY)

---

### Post by strask on 2012-04-30
I had the same problem, the steps I took to fix it are in this thread: [http://ubuntuforums.org/showthread.php?t=1965486](http://ubuntuforums.org/showthread.php?t=1965486)

---

### Post by plokvenc on 2012-05-01
I think the best way to install JDK is download it from Oracle page and manually install. If you have installed other version JDK (OpenJDK, JDK6, etc.) you need the Update Java utility:
```
sudo add-apt-repository ppa:nilarimogard/webupd8
sudo apt-get update
sudo apt-get install update-java
sudo update-java

```where you choose which version you used. You can check result with
```

java -version
javac -version

```

---

### Post by che47audio on 2012-05-15
Thanks for your replies. It didnt what plokvenc said and it works fine now without any errors . 

Thanks

Do i need to flag this up as "Solved"? If so, how ?

---

### Post by josephpmh on 2012-05-22
Thanx!  Worked for me too.

> **Etendard7 said:**
> Hi,

This worked for me:

```

sudo rm /var/lib/dpkg/info/oracle-java7-installer*
sudo apt-get purge oracle-java7-installer*
sudo rm /etc/apt/sources.list.d/*java*
sudo apt-get update
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer

```

(found [here]("http://askubuntu.com/questions/126372/sha256sum-mismatch-jdk-7u3-linux-x64-tar-gz-error-when-trying-to-install-orac"))

---

