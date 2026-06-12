---
title: "Remove stubborn package"
date: 2011-06-25
forum: General Help
---

### Post by JenKue74 on 2011-06-25
I seem to have broken my package database by manually half installing a package which I now can not remove. When I try to install the correct version of the package from the repos I get this:

```

jens@Phobos:~$ sudo aptitude install picard
The following NEW packages will be installed:
  picard 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/678 kB of archives. After unpacking 2,916 kB will be used.
dpkg: error processing /var/cache/apt/archives/picard_0.12.1-0ubuntu2_amd64.deb (--unpack):
 picard: 0.12.1-0ubuntu2 (Multi-Arch: no) is not co-installable with picard:i386 0.15~beta+bzr1117~ppa5~natty1 (Multi-Arch: no) which is currently installed
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 /var/cache/apt/archives/picard_0.12.1-0ubuntu2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of picard:i386:
 picard:i386 depends on python (<< 2.8).
 picard:i386 depends on python (>= 2.6).
 picard:i386 depends on python-central (>= 0.6.11).
 picard:i386 depends on python2.6.
 picard:i386 depends on libavcodec52 (>= 4:0.6-1~) | libavcodec-extra-52 (>= 4:0.6-1~).
 picard:i386 depends on libavformat52 (>= 4:0.6-1~) | libavformat-extra-52 (>= 4:0.6-1~).
 picard:i386 depends on libc6 (>= 2.3.6-6~).
 picard:i386 depends on libfftw3-3.
 picard:i386 depends on libgcc1 (>= 1:4.1.1).
 picard:i386 depends on libofa0 (>= 0.9.3).
 picard:i386 depends on libstdc++6 (>= 4.1.1).
 picard:i386 depends on python-qt4 (>= 4.1).
 picard:i386 depends on python-mutagen (>= 1.11).
 picard:i386 depends on libdiscid0.
dpkg: error processing picard:i386 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 picard:i386

```

I have already deleted the files that were installed by the package as well as some files from /var/lib/dpkg manually. Now I am at a loss what to try next.

---

### Post by 23dornot23d on 2011-06-25
Ok lets ask some questions first ....

what does it show you when you enter this in a terminal ......

**uname -a**

and how was it initially installed ..... Software Centre - gdebi - or something else ....

give me a few minutes going to swap into a 64 bit system to try it out .........

```

keith@keith-MS-7181:~/Downloads$ gdebi picard_0.14-1~getdeb2~natty_amd64.deb
The program 'gdebi' is currently not installed.  You can install it by typing:
sudo apt-get install gdebi-core
keith@keith-MS-7181:~/Downloads$ sudo apt-get install gdebi-core
[sudo] password for keith: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  gdebi-core
0 upgraded, 1 newly installed, 0 to remove and 398 not upgraded.
Need to get 11.3 kB of archives.
After this operation, 131 kB of additional disk space will be used.
Get:1 http://fr.archive.ubuntu.com/ubuntu/ oneiric/main gdebi-core all 0.8~exp2 [11.3 kB]
Fetched 11.3 kB in 0s (31.2 kB/s)
Selecting previously deselected package gdebi-core.
(Reading database ... 368509 files and directories currently installed.)
Unpacking gdebi-core (from .../gdebi-core_0.8~exp2_all.deb) ...
Processing triggers for man-db ...
Setting up gdebi-core (0.8~exp2) ...
keith@keith-MS-7181:~/Downloads$ su
Password: 
root@keith-MS-7181:/home/keith/Downloads# gdebi picard_0.14-1~getdeb2~natty_amd64.deb
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Building data structures... Done 
Building data structures... Done 


Next-Generation MusicBrainz audio files tagger
 Picard is the next generation MusicBrainz tagging application.
 .
 This new tagging concept is album oriented, as opposed to track oriented
 like the others taggers are.
Do you want to install the software package? [y/N]:y
Selecting previously deselected package picard.
(Reading database ... 368523 files and directories currently installed.)
Unpacking picard (from picard_0.14-1~getdeb2~natty_amd64.deb) ...
Setting up picard (0.14-1~getdeb2~natty) ...
Processing triggers for man-db ...
Processing triggers for menu ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for gnome-menus ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for python-support ...

root@keith-MS-7181:/home/keith/Downloads# 


```Ok installed first time for me .....did you use the software centre .... ?


I find this where they ask a yes or no ..... then sometimes it does not work properly ... in the software centre.

so I use gdebi .........




How did you remove it ?

> 
I have already deleted the files that were installed by the package as  well as some files from /var/lib/dpkg manually. Now I am at a loss what  to try next.


This is not the method you should use to remove anything in LINUX ,,,,,

the first thing you should have tried is this if you used aptitude to install it ......

aptitude -f install

any other method and you would need to look at the correct way of removing it too .....

I downloaded the file from the link below and used gdebi to install it ......

[http://pkgs.org/download/ubuntu-11.04/getdeb-apps-amd64/picard_0.14-1~getdeb2~natty_amd64.deb.html](http://pkgs.org/download/ubuntu-11.04/getdeb-apps-amd64/picard_0.14-1~getdeb2~natty_amd64.deb.html)

---

