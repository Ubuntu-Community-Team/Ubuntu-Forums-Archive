---
title: "Trying to install Oracle Java 7"
date: 2012-08-07
forum: General Help
---

### Post by garyzw on 2012-08-07
I entered the following in terminal---

sudo add-apt-repository ppa:webupd8team/java sudo apt-get update sudo apt-get install oracle-java7-installerI get the following output in the Terminal

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  visualvm ttf-kochi-gothic ttf-sazanami-gothic ttf-kochi-mincho
  ttf-sazanami-mincho ttf-arphic-uming
The following packages will be upgraded:
  oracle-java7-installer
1 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0 B/15.3 kB of archives.
After this operation, 3,072 B of additional disk space will be used.
Setting up oracle-java7-installer (7u3-0~eugenesan~precise4) ...
Downloading...
--2012-08-07 18:39:45--  [http://download.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz](http://download.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz)
Resolving download.oracle.com (download.oracle.com)... 24.143.193.147
Connecting to download.oracle.com (download.oracle.com)|24.143.193.147|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz](https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz) [following]
--2012-08-07 18:39:45--  [https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz](https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz)
Resolving edelivery.oracle.com (edelivery.oracle.com)... 184.85.238.174
Connecting to edelivery.oracle.com (edelivery.oracle.com)|184.85.238.174|:443... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [http://download.oracle.com/errors/download-fail-1505220.html](http://download.oracle.com/errors/download-fail-1505220.html) [following]
--2012-08-07 18:39:46--  [http://download.oracle.com/errors/download-fail-1505220.html](http://download.oracle.com/errors/download-fail-1505220.html)
Connecting to download.oracle.com (download.oracle.com)|24.143.193.147|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 5307 (5.2K) [text/html]
Saving to: `./jdk-7u3-linux-i586.tar.gz'

     0K .....                                                 100% 6.46M=0.001s

2012-08-07 18:39:46 (6.46 MB/s) - `./jdk-7u3-linux-i586.tar.gz' saved [5307/5307]

Download done.
sha256sum mismatch jdk-7u3-linux-i586.tar.gz
Oracle JDK 7 is NOT installed.
dpkg: error processing oracle-java7-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 oracle-java7-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by QIII on 2012-08-07
You tried to install the Eugene San version once, didn't you?

Unfortunately, that package is broken.

In the Oracle Java 7 section of the wiki in my signature, I give some instructions for how to untangle the mess.  Just look for the note about the Eugene San PPA.

---

### Post by garyzw on 2012-08-07
It may have been the Eugene San version--I ran the following 

 $ sudo apt-get remove --purge oracle-java7-installer*  $ sudo apt-get install ppa-purge  $ sudo ppa-purge ppa:eugenesan/java  $ sudo apt-get clean  $ sudo apt-get update

How do I install the Sun Java 7?

---

### Post by QIII on 2012-08-07
A little bit above the Eugene San instructions I added a link "Using webupd8.org's strikingly simple method"

It really is strikingly simple.  Those guys are good.

---

### Post by garyzw on 2012-08-07
I did the webupd8.org's strikingly simple method and this is what I got

Reading package lists... Done
gary@gary-FX400:~$ sudo apt-get install oracle-java7-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  visualvm ttf-kochi-gothic ttf-sazanami-gothic ttf-kochi-mincho
  ttf-sazanami-mincho ttf-arphic-uming
The following packages will be upgraded:
  oracle-java7-installer
1 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 15.3 kB of archives.
After this operation, 3,072 B of additional disk space will be used.
Get:1 [http://ppa.launchpad.net/webupd8team/java/ubuntu/](http://ppa.launchpad.net/webupd8team/java/ubuntu/) precise/main oracle-java7-installer all 7u5-0~webupd8~5 [15.3 kB]
Fetched 15.3 kB in 0s (22.9 kB/s)           
Setting up oracle-java7-installer (7u3-0~eugenesan~precise4) ...
Downloading...
--2012-08-07 19:20:48--  [http://download.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz](http://download.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz)
Resolving download.oracle.com (download.oracle.com)... 107.14.38.152, 107.14.38.155
Connecting to download.oracle.com (download.oracle.com)|107.14.38.152|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz](https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz) [following]
--2012-08-07 19:20:48--  [https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz](https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz)
Resolving edelivery.oracle.com (edelivery.oracle.com)... 184.85.238.174
Connecting to edelivery.oracle.com (edelivery.oracle.com)|184.85.238.174|:443... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [http://download.oracle.com/errors/download-fail-1505220.html](http://download.oracle.com/errors/download-fail-1505220.html) [following]
--2012-08-07 19:20:49--  [http://download.oracle.com/errors/download-fail-1505220.html](http://download.oracle.com/errors/download-fail-1505220.html)
Connecting to download.oracle.com (download.oracle.com)|107.14.38.152|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 5307 (5.2K) [text/html]
Saving to: `./jdk-7u3-linux-i586.tar.gz'

     0K .....                                                 100% 7.12M=0.001s

2012-08-07 19:20:49 (7.12 MB/s) - `./jdk-7u3-linux-i586.tar.gz' saved [5307/5307]

Download done.
sha256sum mismatch jdk-7u3-linux-i586.tar.gz
Oracle JDK 7 is NOT installed.
dpkg: error processing oracle-java7-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 oracle-java7-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by QIII on 2012-08-07
The Eugene San PPA was not removed.

Did you run each of the commands in that section independently or did you copy the text from the wiki into the terminal as a chunk?

---

### Post by garyzw on 2012-08-07
The following solved the problem

sudo rm /var/lib/dpkg/info/oracle-java7-installer*
sudo apt-get purge oracle-java7-installer*
sudo rm /etc/apt/sources.list.d/*java* 
sudo apt-get update

sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer

---

### Post by garyzw on 2012-08-07
> **QIII said:**
> The Eugene San PPA was not removed.

Did you run each of the commands in that section independently or did you copy the text from the wiki into the terminal as a chunk?

I did  each section independently--Thanks for your help

---

### Post by 1976MrEMan on 2012-08-12
I've tried every means of installing java that i found in a google search and all to no avail. I'm a new user to ubuntu, but i am pasting the commands in line-by-line and every time i get the error code 1 message. i am aware that the eugene sans package is broken, but all other methods give me the same results.can anybody give me a walkthrough for installing java that doesn't end in frustration? also, i've noticed that these instructions have worked for everyone else, but not for me despite doing it exactly the same. I'm on 12.04, thanks.

---

### Post by cottfcfan on 2012-08-12
Try running the 3 commands in post 7, and post back here with the errors you encounter.

---

### Post by jim_deadlock on 2012-08-12
I always use these instructions, they are excellent. Note there are separate sections for 32 and 64:

[Oracle (Sun) Java JRE for Ubuntu, Linux Mint and Debian]("https://sites.google.com/site/easylinuxtipsproject/java#TOC-Oracle-Sun-Java:-removed-from-all-r")

---

