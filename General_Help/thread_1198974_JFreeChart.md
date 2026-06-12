---
title: "JFreeChart"
date: 2009-06-28
forum: General Help
---

### Post by John Rogers on 2009-06-28
I am keen to install and use JFreeChart. I am running Ubuntu 8.04 LTS on a Dell GX280
I have downloaded the jfreechart-1.0.13.tar.gz file and unpacked it, which yields
Directories
  ant
  checkstyle
  docfiles
  experimental
  lib
  source
  swt
  tests

and Files
  ChangeLog
  jfreechart-1.0.13-demo.jar
  licence-LGPL.txt
  maven-jfreechart-project.xml
  NEWS
  README.txt

I seem to have reached the limits of my knowledge here.... what do I do next?

---

### Post by hansdown on 2009-06-28
Hi John Rogers.

A far easier,and safer way to install this package is,

click system> administration> synaptic package manager.

Enter your password, click enter.

Search for```
 libjfreechart-java
```.

Check the box, click mark for installation.

Click mark all upgrades.Click apply.Click apply.

---

### Post by John Rogers on 2009-06-28
Thank you, hansdown
I went to Synaptic Package Manager... password... search... libfreechart-java
   and got this

but no box for install.
I'm lost again?

---

### Post by John Rogers on 2009-06-28
A light went on (briefly!) in my brain...
I tried the following:

dell@dell-desktop:~$ sudo aptitude search libjfreechart-java
[sudo] password for dell: 
p   libjfreechart-java              - Chart library for Java                    
p   libjfreechart-java-doc          - Chart library for Java - documentation    
dell@dell-desktop:~$ sudo aptitude install libjfreechart-java
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages have been automatically kept back:
  kdelibs-data kdelibs4c2a libavcodec1d libavformat1d libavutil1d 
  libfreetype6-dev libmodplug0c2 libpostproc1d libpq5 linux-libc-dev 
  linux-restricted-modules-common syslinux 
The following NEW packages will be automatically installed:
  libjcommon-java 
The following packages have been kept back:
  adobe-flashplugin apparmor apparmor-utils apport apport-gtk cron cupsys 
  cupsys-bsd cupsys-client cupsys-common dash doc-base firefox firefox-3.0 
  firefox-3.0-gnome-support firefox-gnome-support gnome-system-tools 
  gparted gstreamer0.10-plugins-good gvfs gvfs-backends gvfs-fuse 
  libcupsimage2 libcupsys2 libfreetype6 libglib2.0-0 libgvfscommon0 
  libicu38 libjasper1 libkrb53 libmagick10 libnss3-1d libpango1.0-0 
  libpango1.0-common libpoppler-glib2 libpurple0 libsndfile1 libvolume-id0 
  libwmf0.2-7 linux-headers-2.6.24-23 linux-headers-generic 
  linux-image-2.6.24-23-generic linux-image-generic 
  linux-restricted-modules-generic network-manager-gnome ntpdate nvidia-glx 
  pidgin pidgin-data pm-utils python-apport python-apt 
  python-problem-report tasksel tasksel-data tzdata udev update-manager 
  update-manager-core xfonts-scalable xulrunner-1.9 
  xulrunner-1.9-gnome-support 
The following NEW packages will be installed:
  libjcommon-java libjfreechart-java 
0 packages upgraded, 2 newly installed, 0 to remove and 74 not upgraded.
Need to get 1825kB of archives. After unpacking 2032kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/main libjcommon-java 1.0.10.dfsg-1 [560kB]
Get:2 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/universe libjfreechart-java 1.0.9-1 [1265kB]
Fetched 1825kB in 6min25s (4736B/s)                                             
Selecting previously deselected package libjcommon-java.
(Reading database ... 170361 files and directories currently installed.)
Unpacking libjcommon-java (from .../libjcommon-java_1.0.10.dfsg-1_all.deb) ...
Selecting previously deselected package libjfreechart-java.
Unpacking libjfreechart-java (from .../libjfreechart-java_1.0.9-1_all.deb) ...
Setting up libjcommon-java (1.0.10.dfsg-1) ...
Setting up libjfreechart-java (1.0.9-1) ...
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
dell@dell-desktop:~$ 

It seems I have installed something.... but where do I find it?... and how do I make it work?

---

### Post by hansdown on 2009-06-28
When synaptic opens,be sure that you have "sections" clicked, and

Make sure "all" is clicked.

Click on the binoculars in the top, right toolbar to open a search

window. Enter ```
 libjfreechart-java
```

Click search, and it should come up.

---

### Post by John Rogers on 2009-06-28
O.K. so I seem to have libjfreechart-java installed....
Thanks for the help so far.
But...  
my next question is "where do I go from here?"
I found one post that suggested cd to the directory where the .jar files appear (that is in "lib" for me) and type the command

java -cp jts.jar:jcommon-1.0.0.jar:jfreechart-1.0.0.jar:jhall.jar:other.jar:rss.jar -Xmx256M jclient.LoginFrame

Um... I have two of these files (jcommon and jfreechart)
Is this the path to follow? Or how else do I get jfreechart to talk to me?

---

### Post by hansdown on 2009-06-29
I have never used this one, but just for the sake of experience, I

installed it from synaptic. I'm a little embarrassed to say, that

I have looked all over without finding much information on

it.

Jcommon is one of the dependancies needed.

[http://packages.ubuntu.com/hardy/libs/libjfreechart-java](http://packages.ubuntu.com/hardy/libs/libjfreechart-java)

I just noticed that```
 java-gcj-compat
``` is a dependancy that

for some reason was not installed.

A suggested package is also not included, but is in the repos.

[CODE]libjfreechart-java-do

---

### Post by ihatetryingtopickaloginna on 2009-06-29
I have had this same problem with other programs. Find something in synaptic, install it, and then no clue how to run it or even find it. Using the command line and the name given in synaptic results in an error since the name is wrong, and doing a search on it brings no results. But synaptic shows it is installed. And I have found where a program is installed to and still can't get it to run. I usually just uninstall and forget about it and look for some other program.

Frustrating.

---

### Post by hansdown on 2009-06-29
> **ihatetryingtopickaloginna said:**
> I have had this same problem with other programs. Find something in synaptic, install it, and then no clue how to run it or even find it. Using the command line and the name given in synaptic results in an error since the name is wrong, and doing a search on it brings no results. But synaptic shows it is installed. And I have found where a program is installed to and still can't get it to run. I usually just uninstall and forget about it and look for some other program.

Frustrating.

Yes, it is a little frustrating. I agree with your username too.:p

---

### Post by John Rogers on 2009-07-01
Thank you for the assistance to get this far.
I think I will retire to a corner and read up on Java, in an attempt to understand what I am trying to do. Then I will try again with JFreeChart. Will update this thread when I get to that point!

---

### Post by hansdown on 2009-07-01
Open office draw does various graphs and charts, but there seems to be a learning curve with this one.

---

