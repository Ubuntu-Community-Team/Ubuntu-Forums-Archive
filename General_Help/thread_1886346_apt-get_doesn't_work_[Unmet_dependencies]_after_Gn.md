---
title: "apt-get doesn't work [Unmet dependencies] after Gnome Activty Jo"
date: 2011-11-24
forum: General Help
---

### Post by geryzeck on 2011-11-24
Ubuntu 11.10 32bit
HP Pavilion dm1

hey folks,

i just tried to install the gnome activity journal as a front-end for the Zeitgeist stuff..
anyway, after an installation via terminal the apt-get install function doesn't work any more.
every time i now try to install or remove ANY application via apt-get i get the following
error message: (in this case i tried to install kAlarm.. but in fact it doesn't matter what app it is since its always the same error message)
```
You might want to run 'apt-get -f install' to correct these:
# apt-get install kalarm 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 kalarm : Depends: libkholidays4 (>= 4:4.6) but it is not going to be installed
 zeitgeist : Depends: python-zeitgeist but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```alright, if i do so i'm gettin the following:

```
# apt-get -f install      
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  python-zeitgeist
The following NEW packages will be installed:
  python-zeitgeist
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
5 not fully installed or removed.
Need to get 0 B/36.7 kB of archives.
After this operation, 217 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 226003 files and directories currently installed.)
Unpacking python-zeitgeist (from .../python-zeitgeist_0.8.99~alpha1b-1ubuntu1~ppa1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/python-zeitgeist_0.8.99~alpha1b-1ubuntu1~ppa1_all.deb (--unpack):
 trying to overwrite '/usr/share/pyshared/zeitgeist/__init__.py', which is also in package zeitgeist-core 0.8.2-1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 /var/cache/apt/archives/python-zeitgeist_0.8.99~alpha1b-1ubuntu1~ppa1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```it doesn't matter what i do (even with apt-get -f install python-zeitgeist its the same)
i can't use the apt-get function without getting always this error code


thanks in advance
cheers
:popcorn:

---

### Post by geryzeck on 2011-11-25
alright.. i managed it somehow thanks to this
[http://askubuntu.com/questions/42341/zeitgeist-extension-fts-cant-seem-to-install-after-upgrade-from-10-04-to-10-10](http://askubuntu.com/questions/42341/zeitgeist-extension-fts-cant-seem-to-install-after-upgrade-from-10-04-to-10-10)

its just to remove the zeitgeist ppas in software sources



please mark as [SOLVED]

---

