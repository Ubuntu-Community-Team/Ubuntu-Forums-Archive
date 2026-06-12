---
title: "problem launching compiz-config manager"
date: 2009-12-02
forum: General Help
---

### Post by woodmawa on 2009-12-02
bear with me folks - newbie here

installed 9.10 (64 bit ) on pc

installed emerald and compiz-config-settings manager

however if run compiz-config-settings manager from system>preferences

it shows a window start up waits a mo and then vanishes - nos screen comes up 

in a terminal window if i go ccsm i get this 

Traceback (most recent call last):
  File "/usr/bin/ccsm", line 99, in <module>
    import compizconfig
ImportError: No module named compizconfig
will@will-ubuntu-desktop:~$ 

however emerald seems to work (emerald --replace &)  will decorate the windows etc.

tried inunstall compiz and re install (see trace) 
 
will@will-ubuntu-desktop:~$ sudo apt-get remove compiz
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  compiz
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 77.8kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 132495 files and directories currently installed.)
Removing compiz ...
will@will-ubuntu-desktop:~$ sudo apt-get install compizconfig-settings-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
compizconfig-settings-manager is already the newest version.
The following packages were automatically installed and are no longer required:
  compiz-fusion-plugins-extra compiz-fusion-plugins-main
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
will@will-ubuntu-desktop:~$ sudo apt-get autoremove compiz-fusion-plugins-extra compiz-fusion-plugins-main
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  compiz-fusion-plugins-extra compiz-fusion-plugins-main
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 19.5MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 132491 files and directories currently installed.)
Removing compiz-fusion-plugins-extra ...
Removing compiz-fusion-plugins-main ...
will@will-ubuntu-desktop:~$ sudo apt-get install compizconfig-settings-managerReading package lists... Done
Building dependency tree       
Reading state information... Done
compizconfig-settings-manager is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
will@will-ubuntu-desktop:~$ sudo apt-get remove compizconfig-settings-managerReading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-compizconfig
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  compizconfig-settings-manager
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 4,166kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 132198 files and directories currently installed.)
Removing compizconfig-settings-manager ...
Processing triggers for python-support ...
Processing triggers for man-db ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
will@will-ubuntu-desktop:~$ sudo apt-get install compizconfig-settings-manager
Reading package lists... Done
Building dependency tree       

but it still wont start settings manager gui.

anyone got any ideas what i'm doing wrong


did similar build on laptop and that seems to come up fine - just not on my main machine

Any ideas greatfully received 

Will

---

### Post by OpSecShellshock on 2009-12-02
[LEFT]Looks to me like the problem is that you installed CCSM but didn't install compiz-fusion. Without that there aren't any settings to manage.
[/LEFT]

---

### Post by woodmawa on 2009-12-03
ok - thanks for coming back 

i tried what you said  - heres the trace

will@will-ubuntu-desktop:~$ sudo apt-get install compiz-fusion-*
[sudo] password for will: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting compiz-fusion-plugins-extra for regex ‘compiz-fusion-*’
Note, selecting compiz-fusion-bcop for regex ‘compiz-fusion-*’
Note, selecting compiz-fusion-plugins-main for regex ‘compiz-fusion-*’
The following extra packages will be installed:
  compiz-fusion-bcop
The following NEW packages will be installed
  compiz-fusion-bcop
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 9,500B of archives.
After this operation, 119kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/main compiz-fusion-bcop 0.8.2-0ubuntu2 [9,500B]
Fetched 9,500B in 0s (36.0kB/s)           
Selecting previously deselected package compiz-fusion-bcop.
(Reading database ... 132496 files and directories currently installed.)
Unpacking compiz-fusion-bcop (from .../compiz-fusion-bcop_0.8.2-0ubuntu2_all.deb) ...
Setting up compiz-fusion-bcop (0.8.2-0ubuntu2) ...
will@will-ubuntu-desktop:~$ sudo apt-get install compiz
Reading package lists... Done
Building dependency tree       
Reading state information... Done
compiz is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
will@will-ubuntu-desktop:~$ sudo apt-get install compiz-fusion-*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting compiz-fusion-plugins-extra for regex ‘compiz-fusion-*’
Note, selecting compiz-fusion-bcop for regex ‘compiz-fusion-*’
Note, selecting compiz-fusion-plugins-main for regex ‘compiz-fusion-*’
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
will@will-ubuntu-desktop:~$ ccsm
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 99, in <module>
    import compizconfig
ImportError: No module named compizconfig


however despite installing something - when i run the settings manager it still whirls a little and drops out - also when i try ccsm i get the error above 

still not there yet - what i am left to try?

---

