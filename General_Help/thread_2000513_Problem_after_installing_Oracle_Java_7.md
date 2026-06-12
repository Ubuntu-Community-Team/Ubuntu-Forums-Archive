---
title: "Problem after installing Oracle Java 7"
date: 2012-06-09
forum: General Help
---

### Post by rhugga on 2012-06-09
I originally followed a link on installing Oracle Java 7 by adding this repository:
ppa:eugenesan/java

This method does not work because Oracle does not allow direct downloads.

I have now installed Java 7 manually and have it working fine.

My problem is that whenever I install/update/manage software it still complains and tries to run "oracle-java7-installer". I've tried removing with dpkg, apt-get, cleaning, removing, etc.. just about anything I can think of. 

I have removed the ppa:eugenesan/java repo before I tried doing all this.

Here is an example of what I see when doing "apt-get autoremove":
root@ubuntu:~# apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up oracle-java7-installer (7u3-0~eugenesan~precise4) ...
Downloading...
--2012-06-09 13:44:29--  [http://download.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz](http://download.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz)
Resolving download.oracle.com (download.oracle.com)... 24.143.193.147, 24.143.193.203
Connecting to download.oracle.com (download.oracle.com)|24.143.193.147|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz](https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz) [following]
--2012-06-09 13:44:29--  [https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz](https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz)
Resolving edelivery.oracle.com (edelivery.oracle.com)... 23.64.10.174
Connecting to edelivery.oracle.com (edelivery.oracle.com)|23.64.10.174|:443... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [http://download.oracle.com/errors/download-fail-1505220.html](http://download.oracle.com/errors/download-fail-1505220.html) [following]
--2012-06-09 13:44:30--  [http://download.oracle.com/errors/download-fail-1505220.html](http://download.oracle.com/errors/download-fail-1505220.html)
Connecting to download.oracle.com (download.oracle.com)|24.143.193.147|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 5307 (5.2K) [text/html]
Saving to: `./jdk-7u3-linux-i586.tar.gz'

     0K .....                                                 100%  680M=0s

2012-06-09 13:44:30 (680 MB/s) - `./jdk-7u3-linux-i586.tar.gz' saved [5307/5307]

Download done.
sha256sum mismatch jdk-7u3-linux-i586.tar.gz
Oracle JDK 7 is NOT installed.
dpkg: error processing oracle-java7-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 oracle-java7-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)


How do I clean this up???

Thx

---

### Post by Frogs Hair on 2012-06-09
If you added a software  source for the program  you may need to remove it. Try update manager > settings > other software and remove both source lines if listed and run check for updates.

---

### Post by tumutanzi.com on 2012-06-09
> **Frogs Hair said:**
> If you added a software  source for the program  you may need to remove it. Try update manager > settings > other software and remove both source lines if listed and run check for updates.

I think it is a standard way to do it too.

---

### Post by rhugga on 2012-06-09
Yea I removed the sources using "add-apt-repository -r". I then went into the Ubuntu Software Center, saw that they were still listed and then removed them from there as well, however its still tying to mess with this package. 

root@ubuntu:~# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y

From this point I get the same error/output as I listed in my original post.

Here is the contents of my /etc/apt/sources.list:
root@ubuntu:~# cat /etc/apt/sources.list  | grep -v "^#"
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse


deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main

Grr... frustrating.

---

### Post by matt_symes on 2012-06-09
Hi

LOL. I just installed it and it is a right pain to remove.

I think a manual removal maybe the way to go. I'm just looking at what the install did to my system and then i will post back.

Kind regards

---

### Post by matt_symes on 2012-06-09
Hi

First thing first. Make a backup of your status file.

Open a terminal and type

```
sudo cp /var/lib/dpkg/status{,.bk}
```

Then type 

```
gksudo gedit /var/lib/dpkg/status
```

Press ctrl + F to bring up the find dialog and search for the words

```
oracle-java7-installer
```

This will find the package in your status file. Remove all the text i have highlighted in the code block below. Leave one line between the previous package and the following one.

Text to remove.

```
Package: oracle-java7-installer
Status: purge ok half-configured
Priority: optional
Section: non-free/java
Installed-Size: 81
Maintainer: Alin Andrei <webupd8@gmail.com>
Architecture: all
Version: 7u3-0~eugenesan~precise4
Replaces: icedtea-6-plugin, icedtea-7-plugin, openjdk-6-jdk, openjdk-6-jre, openjdk-6-jre-headless, openjdk-7-jdk, openjdk-7-jre, openjdk-7-jre-headless, oracle-jdk7-installer, sun-java6-bin, sun-java6-jdk, sun-java6-jre
Provides: default-jre, default-jre-headless, java-jdk, java-runtime, java-runtime-headless, java-virtual-machine, java2-jdk, java2-runtime, java2-runtime-headless, java5-jdk, java5-runtime, java5-runtime-headless, java6-jdk, java6-runtime, java6-runtime-headless, java7-jdk, java7-runtime, java7-runtime-headless, oracle-java7, oracle-java7-plugin, oracle-jdk7-installer
Depends: java-common (>= 0.24), locales, debconf (>= 0.5) | debconf-2.0
Pre-Depends: wget
Recommends: gsfonts-x11
Suggests: binfmt-support, ttf-baekmuk | ttf-unfonts | ttf-unfonts-core, ttf-kochi-gothic | ttf-sazanami-gothic, ttf-kochi-mincho | ttf-sazanami-mincho, ttf-arphic-uming, firefox | firefox-2 | iceweasel | mozilla-firefox | iceape-browser | mozilla-browser | epiphany-gecko | epiphany-webkit | epiphany-browser | galeon | midbrowser | moblin-web-browser | xulrunner | xulrunner-1.9 | konqueror | chromium-browser | midori | google-chrome
Conflicts: j2se-common, oracle-jdk7-installer
Description: Sun Java(TM) Development Kit (JDK) 7
 The JDK(TM) is a development environment for building and running
 applications, applets, and components using the Java programming language.
 .
 The JDK(TM) includes Java Runtime Environment (JRE) for running applications,
 Java Plug-in for running applets in web browsers and tools useful for
 developing and testing programs written in the Java programming language.
 .
 Note that this package does not contain any software from Oracle. This
 package does however contain a script to download and install Oracle JDK 7.
 All information regarding Java itself can be found on this website:
 http://www.oracle.com/
Homepage: http://www.oracle.com/technetwork/java/javase/downloads/index.html
Npp-Applications: ec8030f7-c20a-464f-9b0e-13a3a9e97384, 92650c4d-4b8e-4d2a-b7eb-24ecf4f6b63a
Npp-Mimetype: application/x-java-vm, application/x-java-applet, application/x-java-applet;version=1.1, application/x-java-applet;version=1.1.1, application/x-java-applet;version=1.1.2, application/x-java-applet;version=1.1.3, application/x-java-applet;version=1.2, application/x-java-applet;version=1.2.1, application/x-java-applet;version=1.2.2, application/x-java-applet;version=1.3, application/x-java-applet;version=1.3.1, application/x-java-applet;version=1.4, application/x-java-applet;version=1.4.1, application/x-java-applet;version=1.4.2, application/x-java-applet;version=1.5, application/x-java-applet;version=1.6, application/x-java-applet;jpi-version=1.6.0_07, application/x-java-bean, application/x-java-bean;version=1.1, application/x-java-bean;version=1.1.1, application/x-java-bean;version=1.1.2, application/x-java-bean;version=1.1.3, application/x-java-bean;version=1.2, application/x-java-bean;version=1.2.1, application/x-java-bean;version=1.2.2, application/x-java-bean;version=1.3, application/x-java-bean;version=1.3.1, application/x-java-bean;version=1.4, application/x-java-bean;version=1.4.1, application/x-java-bean;version=1.4.2, application/x-java-bean;version=1.5, application/x-java-bean;version=1.6, application/x-java-bean;jpi-version=1.7.0_03
Npp-Name: The Java(TM) Plug-in, Java SE 7
```

Save and close the file.

To check it has removed the package correctly type

```
sudo apt-get autoremove
```

Assuming that worked then we need to remove the files it installed.

Below is a list of the file and directories it installed the files.

```
matthew@matthew-Aspire-7540 ~/my_storage/linux-3.4.0-4.9/ubuntu-quantal
 % dpkg -L oracle-java7-installer
/.
/usr
/usr/lib
/usr/lib/jvm
/usr/lib/jvm/java-7-oracle
/usr/share
/usr/share/pixmaps
/usr/share/pixmaps/oracle_java7.png
/usr/share/pixmaps/oracle_java7.xpm
/usr/share/doc
/usr/share/doc/oracle-java7-installer
/usr/share/doc/oracle-java7-installer/copyright
/usr/share/doc/oracle-java7-installer/changelog.Debian.gz
/usr/share/applications
/usr/share/applications/JB-jvisualvm.desktop
/usr/share/applications/JB-policytool.desktop
/usr/share/applications/JB-controlpanel.desktop
/usr/share/applications/JB-jconsole.desktop
/usr/share/applications/JB-javaws.desktop
/usr/share/applications/JB-java.desktop
/var
/var/cache
/var/cache/oracle-java7-installer
/var/cache/oracle-java7-installer/javaws-wrapper.sh
/var/cache/oracle-java7-installer/jar.binfmt
matthew@matthew-Aspire-7540 ~/my_storage/linux-3.4.0-4.9/ubuntu-quantal
```

To remove these files in the terminal type these command

```
sudo rm -r var/cache/oracle-java7-installer
sudo rm -r /usr/share/doc/oracle-java7-installer
sudo rm /usr/share/pixmaps/oracle_java7*
sudo rm -r /usr/lib/jvm/java-7-oracle
sudo rm /usr/share/applications/JB-*
sudo rm /var/lib/dpkg/info/oracle-java7-installer*
```

You may find it easier to copy and paste the above commands.

Finally remove the ppa.

```
sudo rm /etc/apt/sources.list.d/eugenesan-java-quantal.list
```

I need to check if it updated any alternatives or left any other files on the system. I will post back soon.

Kind regards

---

### Post by matt_symes on 2012-06-09
Hi

It does not seem to have updated any of my alternatives so i suspect it will not have done yours.

I cannot find any other files on my system from it apart from some files in the cache.

```
sudo rm -r /var/cache/oracle-java7-installer
```

Hopefully you are good to go.

Kind regards

---

### Post by mörgæs on 2012-06-09
Besides the Java stuff: It is generally not recommended to be root in Ubuntu.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

