---
title: "Help with Installation of libreoffice base"
date: 2012-08-27
forum: General Help
---

### Post by Alcidious on 2012-08-27
Not sure what the problem was... I'm trying to download the base part to build databases, and I ran sudo apt-get install libreoffice-base.  I received errors saying several packages were missing dependencies. So I installed each package.  Should I just have ran update on these packages? Here is the printout:

alcidious42@IronMan:~/Downloads$ sudo apt-get install libreoffice-base
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libreoffice-base : Depends: libreoffice-core (= 1:3.5.2-2ubuntu1) but it is not going to be installed
                    Depends: libreoffice-base-core (= 1:3.5.2-2ubuntu1) but it is not going to be installed
                    Depends: libreoffice-java-common (>= 1:3.5.2~) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

alcidious42@IronMan:~/Downloads$ sudo apt-get install libreoffice-core libreoffice-base-core libreoffice-java-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libreoffice-base-core is already the newest version.
libreoffice-core is already the newest version.
The following package was automatically installed and is no longer required:
  libjpeg62
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libxerces2-java libxml-commons-external-java libxml-commons-resolver1.1-java
Suggested packages:
  libxerces2-java-doc libxerces2-java-gcj libxml-commons-resolver1.1-java-doc
The following NEW packages will be installed:
  libreoffice-java-common libxerces2-java libxml-commons-external-java
  libxml-commons-resolver1.1-java
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 5,994 kB of archives.
After this operation, 10.5 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main libxml-commons-resolver1.1-java all 1.2-7 [91.3 kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main libxml-commons-external-java all 1.4.01-2 [245 kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main libxerces2-java all 2.11.0-4 [1,446 kB]
Get:4 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main libreoffice-java-common all 1:3.5.2-2ubuntu1 [4,212 kB]
Fetched 5,994 kB in 2s (2,129 kB/s)                  
Selecting previously unselected package libxml-commons-resolver1.1-java.
(Reading database ... 232816 files and directories currently installed.)
Unpacking libxml-commons-resolver1.1-java (from .../libxml-commons-resolver1.1-java_1.2-7_all.deb) ...
Selecting previously unselected package libxml-commons-external-java.
Unpacking libxml-commons-external-java (from .../libxml-commons-external-java_1.4.01-2_all.deb) ...
Selecting previously unselected package libxerces2-java.
Unpacking libxerces2-java (from .../libxerces2-java_2.11.0-4_all.deb) ...
Selecting previously unselected package libreoffice-java-common.
Unpacking libreoffice-java-common (from .../libreoffice-java-common_1%3a3.5.2-2ubuntu1_all.deb) ...
Setting up libxml-commons-resolver1.1-java (1.2-7) ...
Setting up libxml-commons-external-java (1.4.01-2) ...
Setting up libxerces2-java (2.11.0-4) ...
Setting up libreoffice-java-common (1:3.5.2-2ubuntu1) ...
alcidious42@IronMan:~/Downloads$ sudo apt-get install libreoffice-base
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libreoffice-base : Depends: libreoffice-core (= 1:3.5.2-2ubuntu1) but it is not going to be installed
                    Depends: libreoffice-base-core (= 1:3.5.2-2ubuntu1) but it is not going to be installed
                    Depends: libreoffice-java-common (>= 1:3.5.2~) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


Sorry if kinda long! I wanted to include my attempts to address it and my final result.  Thanks a bunch

---

### Post by zeroseven0183 on 2012-08-27
Please run ```
sudo apt-get update
``` then try installing again.

---

### Post by Alcidious on 2012-08-27
I tried doing apt-get update, but received more errors.  I also just tried to use ubuntu software center, and also got errors. 

Here is output from terminal:

alcidious42@IronMan:~/Downloads$ sudo apt-get install *.deb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libreoffice-base_3.5.2-2ubuntu1_i386.deb
E: Couldn't find any package by regex 'libreoffice-base_3.5.2-2ubuntu1_i386.deb

Here is the detailed output from software center:


The following packages have unmet dependencies:

libreoffice-base: Depends: libreoffice-core (= 1:3.5.2-2ubuntu1) but 1:3.5.4-0ubuntu1 is to be installed
                  Depends: libreoffice-base-core (= 1:3.5.2-2ubuntu1) but 1:3.5.4-0ubuntu1 is to be installed
                  Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.3-1ubuntu5 is to be installed
                  Depends: libhsqldb-java (< 1.8.1~) but 1.8.0.10-9ubuntu2 is to be installed

Could it be that I need to update my entire libre office suite?

---

### Post by zeroseven0183 on 2012-09-09
It seems that this problem you reported has already been resolved. How were you able to get a solution for it?

---

### Post by tg3793 on 2012-09-19
I got several errors about dependencies not being resolved also. I 'had' libreoffice singing along quite nicely for a few months and then I tried to update it to a more recent version. 

That's when everything started breaking and complaining that dependencies weren't resolved ... It 'would' tell me what the dependencies were, but then like the classmate of a ten year old it would mock me and tell me that it wasn't going to be installed :-)

I let it go for several weeks, revisiting the issue from time to time, changing PPA, purging, updating apt-get, etc. And finally I gave up yesterday and decided to "go manual" on it.

1) downloaded most recent .deb from [http://www.libreoffice.org/download/](http://www.libreoffice.org/download/) (150meg download)

2) followed the enclosed readme file which said to open a CLI in the directory with all of the debs and do a "**sudo dpkg -i *.deb**"

3) Problem solved. ... LibreOffice 3.6.1 is currently installed and singing along.


*The solution above should work for others as well since I'm not even running Ubuntu the "normal" way. I prefer using XFCE so I have Xubuntu installed.*

---

