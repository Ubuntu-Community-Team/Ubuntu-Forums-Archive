---
title: "GIMP Will Not Run"
date: 2012-05-05
forum: General Help
---

### Post by alligoodw on 2012-05-05
I installed GIMP using Synaptic in Ubuntu 12.4. The icon appeared but when I click it, nothing happens . . . the program will not run. I've removed it and reinstalled and it still will not run. Can someone help me?

---

### Post by llamabr on 2012-05-05
weird.  open a terminal, type:

```
gimp

```
press enter, and copy/paste the output

---

### Post by alligoodw on 2012-05-06
gimp: error while loading shared libraries: libgegl-0.0.so.0: cannot open shared object file: No such file or directory

---

### Post by philinux on 2012-05-06
> **alligoodw said:**
> gimp: error while loading shared libraries: libgegl-0.0.so.0: cannot open shared object file: No such file or directory

I'm running 12.04 with the ppa for gimp 2.8 enabled.
[http://ubuntuforums.org/showpost.php?p=11901444&postcount=4](http://ubuntuforums.org/showpost.php?p=11901444&postcount=4)

However that library does not exist on my system. Is yours a stock install of gimp 2.6?

[edit] just reread first post. Try this.
```
sudo apt-get update
sudo apt-get purge gimp libgegl* 
sudo apt-get clean
sudo apt-get install gimp 
```


```
apt-cache policy libgegl-0.0.so.0
N: Unable to locate package libgegl-0.0.so.0
N: Couldn't find any package by regex 'libgegl-0.0.so.0'

and 

aptitude search libgegl
p   libgegl-0.0-0                                     - Generic Graphics Library                                   
p   libgegl-0.0-0:i386                                - Generic Graphics Library                                   
p   libgegl-0.0-dev                                   - Generic Graphics Library (development files)               
p   libgegl-0.0-dev:i386                              - Generic Graphics Library (development files)               
p   libgegl-0.0-doc                                   - Generic Graphics Library (documentation)                   
i A libgegl-0.2-0                                     - Generic Graphics Library                                   
p   libgegl-0.2-0:i386                                - Generic Graphics Library                                   
p   libgegl-0.2-0-dbg                                 - Generic Graphics Library (debugging symbols)               
p   libgegl-0.2-0-dbg:i386                            - Generic Graphics Library (debugging symbols)               
p   libgegl-dev                                       - Generic Graphics Library (development files)               
p   libgegl-dev:i386                                  - Generic Graphics Library (development files)               
p   libgegl-doc                                       - Generic Graphics Library (documentation)                   
v   libgegl-doc:i386
```

---

### Post by alligoodw on 2012-05-06
I installed GIMP through Synaptic.  When I go in and delete it, I get an error that a package failed to install.  I was trying to install Java and I might have created a problem, at any rate, if there is a program that is failing to install, how do I delete that file so the attempt to install doesn't take place?

On the other hand, I'll use the ppa you have provided and see if I can get GIMP 2.8 to install on my system.

---

### Post by alligoodw on 2012-05-06
I ran the following commands:

sudo apt-get update
sudo apt-get purge gimp libgegl* 
sudo apt-get clean
sudo apt-get install gimp

While it installed and I see the icon for it, GIMP will not load. When I do an installation, I'm always getting an error message that a file failed to install.  It's a file to install oracle-java7.installer.  I don't know how to remedy this problem.  I do believe however, that this may be the issue that is causing my problem with GIMP or any other program I'm trying to install.

---

### Post by alligoodw on 2012-05-06
When I delete GIMP, this is the error message that is generated:


(Reading database ... 179464 files and directories currently installed.)
Removing gimp ...
Purging configuration files for gimp ...
Processing triggers for menu ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Setting up oracle-java7-installer (7u3-0~eugenesan~precise4) ...
Downloading...
--2012-05-06 12:03:42--  [http://download.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz](http://download.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz)
Resolving download.oracle.com (download.oracle.com)... 23.3.12.210, 23.3.12.195
Connecting to download.oracle.com (download.oracle.com)|23.3.12.210|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz](https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz) [following]
--2012-05-06 12:03:42--  [https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz](https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz)
Resolving edelivery.oracle.com (edelivery.oracle.com)... 184.25.210.174
Connecting to edelivery.oracle.com (edelivery.oracle.com)|184.25.210.174|:443... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [http://download.oracle.com/errors/download-fail-1505220.html](http://download.oracle.com/errors/download-fail-1505220.html) [following]
--2012-05-06 12:03:43--  [http://download.oracle.com/errors/download-fail-1505220.html](http://download.oracle.com/errors/download-fail-1505220.html)
Connecting to download.oracle.com (download.oracle.com)|23.3.12.210|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 5307 (5.2K) [text/html]
Saving to: `./jdk-7u3-linux-i586.tar.gz'

     0K .....                                                 100% 2.39M=0.002s

2012-05-06 12:03:43 (2.39 MB/s) - `./jdk-7u3-linux-i586.tar.gz' saved [5307/5307]

Download done.
sha256sum mismatch jdk-7u3-linux-i586.tar.gz
Oracle JDK 7 is NOT installed.
dpkg: error processing oracle-java7-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 oracle-java7-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

---

### Post by philinux on 2012-05-06
Try purging the package.

```
sudo apt-get purge oracle-java7-installer
```

---

### Post by alligoodw on 2012-05-06
This is what I get:


@alligoodw-K52F:~$ sudo apt-get purge oracle-java7-installer
[sudo] password for alligoodw: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  oracle-java7-installer*
0 upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
1 not fully installed or removed.
After this operation, 82.9 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 179227 files and directories currently installed.)
Removing oracle-java7-installer ...
update-alternatives: error: unknown argument `cdrom'
dpkg: error processing oracle-java7-installer (--purge):
 subprocess installed pre-removal script returned error exit status 2
Downloading...
--2012-05-06 12:33:06--  [http://download.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz](http://download.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz)
Resolving download.oracle.com (download.oracle.com)... 23.49.56.160, 23.49.56.155
Connecting to download.oracle.com (download.oracle.com)|23.49.56.160|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily

---

### Post by alligoodw on 2012-05-06
Okay!  I followed your instructions with the ppa and I got GIMP 2.8 to work correctly . . . problem solved.  

I would like to take this moment and express my appreciation for your time and knowledge - thank you!  Now, I need to make this post SOLVED but I'm not exactly sure how this is done . . . can you tell me? :-)

---

