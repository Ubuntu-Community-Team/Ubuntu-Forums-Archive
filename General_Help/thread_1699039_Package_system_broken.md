---
title: "Package system broken"
date: 2011-03-03
forum: General Help
---

### Post by alambpencil on 2011-03-03
sudo apt-get upgrade

[SIZE="1"]ic@thinkpadt410:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 finch : Depends: pidgin-data (>= 1:2.7.9) but 1:2.7.3-1ubuntu3.2 is installed
 pidgin : Depends: pidgin-data (>= 1:2.7.9) but 1:2.7.3-1ubuntu3.2 is installed
E: Unmet dependencies. Try using -f.[/SIZE]


The package system is broken Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f

sudo apt-get install -f 


[SIZE="1"]ic@thinkpadt410:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  pidgin-data
The following packages will be upgraded:
  pidgin-data
1 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
2 not fully installed or removed.
Need to get 0B/8,589kB of archives.
After this operation, 24.1MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 175304 files and directories currently installed.)
Preparing to replace pidgin-data 1:2.7.3-1ubuntu3.2 (using .../pidgin-data_1%3a2.7.9-1ubuntu0+pidgin1.10.10_all.deb) ...
Unpacking replacement pidgin-data ...
dpkg: error processing /var/cache/apt/archives/pidgin-data_1%3a2.7.9-1ubuntu0+pidgin1.10.10_all.deb (--unpack):
 trying to overwrite '/usr/share/pixmaps/pidgin/protocols/16/facebook.png', which is also in package pidgin-facebookchat 1.69
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/pidgin-data_1%3a2.7.9-1ubuntu0+pidgin1.10.10_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)[/SIZE]

---

