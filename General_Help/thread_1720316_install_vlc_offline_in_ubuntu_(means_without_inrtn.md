---
title: "install vlc offline in ubuntu (means without inrtnet)"
date: 2011-04-03
forum: General Help
---

### Post by connect2jan on 2011-04-03
hi
can any one give good solutions
i tried wth deb file ( vlc_1.1.4-1ubuntu1.4_i386.deb)
on terminal
dpkg -i vlc.deb
its giving error
janu@janu:~$ sudo dpkg -i vlc_1.1.4-1ubuntu1.4_i386.deb 
[sudo] password for janu: 
(Reading database ... 122684 files and directories currently installed.)
Preparing to replace vlc 0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3.3 (using vlc_1.1.4-1ubuntu1.4_i386.deb) ...
Unpacking replacement vlc ...
dpkg: dependency problems prevent configuration of vlc:
 vlc depends on vlc-nox (= 1.1.4-1ubuntu1.4); however:
  Package vlc-nox is not installed.
dpkg: error processing vlc (--install):
 dependency problems - leaving unconfigured
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for man-db ...
Processing triggers for python-support ...
Errors were encountered while processing:
 vlc
--------------------------------------------
give deb file sites

i will great thankful to them

---

### Post by Spyderkid on 2011-04-03
Download it on another computer then isntall?

---

### Post by WorMzy on 2011-04-03
You can download the repo versions of packages from here: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

It will also give you a list of dependencies which you also need to have installed.

Here's the VLC package for Maverick: [http://packages.ubuntu.com/maverick-updates/vlc](http://packages.ubuntu.com/maverick-updates/vlc)
and the corresponding vlc-nox package: [http://packages.ubuntu.com/maverick-updates/vlc-nox](http://packages.ubuntu.com/maverick-updates/vlc-nox)

---

### Post by connect2jan on 2011-04-03
hi thnks for reply
i downloaded two files 
**[FONT=Arial Narrow][SIZE=2]vlc_1.1.4-1ubuntu1.4_i386.deb,[/SIZE][/FONT]**

**[FONT=Arial Narrow][SIZE=2]vlc-nox_1.1.4-1ubuntu1.4_i386.deb[/SIZE][/FONT] **


janu@janu:~/Downloads$ sudo dpkg vlc_1.1.4-1ubuntu1.4_i386.deb 
dpkg: need an action option

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked 
[*] produce a lot of output - pipe it through `less' or `more' !
janu@janu:~/Downloads$ sudo dpkg vlc-nox_1.1.4-1ubuntu1.4_i386.deb 
dpkg: need an action option

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked 
[*] produce a lot of output - pipe it through `less' or `more' !
 whats wrong
i am using  [ubuntu ]("http://packages.ubuntu.com/lucid/")(10.04LTS)
 
any help

---

### Post by connect2jan on 2011-04-03
oh i am very soory
i miss tat -i option
its working great thanks

---

### Post by connect2jan on 2011-04-04
[http://packages.ubuntu.com/maverick-updates/vlc-nox](http://packages.ubuntu.com/maverick-updates/vlc-nox)
dpkg: dependency problems prevent configuration of vlc-nox:
 vlc-nox depends on liba52-0.7.4; however:
  Package liba52-0.7.4 is not installed.
 vlc-nox depends on libass4 (>= 0.9.7); however:
  Package libass4 is not installed.
 vlc-nox depends on libavcodec52 (>= 4:0.6-1~) | libavcodec-extra-52 (>= 4:0.6-1~); however:
  Package libavcodec52 is not installed.
  Package libavcodec-extra-52 is not installed.
 vlc-nox depends on libavformat52 (>= 4:0.6-1~) | libavformat-extra-52 (>= 4:0.6-1~); however:
  Package libavformat52 is not installed.
  Package libavformat-extra-52 is not installed.
 vlc-nox depends on libavutil50 (>= 4:0.6-1~) | libavutil-extra-50 (>= 4:0.6-1~); however:
  Package libavutil50 is not installed.
  Package libavutil-extra-50 is not installed.
 vlc-nox depends on libcaca0 (>= 0.99.beta17-1); however:
  Version of libcaca0 on system is 0.99.beta16-3.
 vlc-nox depends on libcddb2; however:
  Package libcddb2 is not installed.
 vlc-nox depends on libdc1394-22; however:
  Package libdc1394-22 is not installed.
 vlc-nox depends on libdca0; however:
  Package libdca0 is not installed.
 vlc-nox depends on libdirac-encoder0; however:
  Package libdirac-encoder0 is not installed.
 vlc-nox depends on libdvbpsi6 (>= 0.1.7); however:
  Package libdvbpsi6 is not installed.
 
where can i get all dependendent pkg at one place (instead of downloading each and every single pkg everytime)

---

