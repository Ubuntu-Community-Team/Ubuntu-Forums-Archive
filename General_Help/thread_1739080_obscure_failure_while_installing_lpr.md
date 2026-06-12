---
title: "obscure failure while installing lpr"
date: 2011-04-25
forum: General Help
---

### Post by ub40d on 2011-04-25
I can't seem to be able to install lpr (for printing) and can't make sense of the error message. Restarting from scratch, here is what I get. What should I do? This is ubuntu 10.10.

~ $>sudo apt-get remove lpr
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package lpr is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

~ $>sudo apt-get install lpr
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  magicfilter apsfilter
The following NEW packages will be installed
  lpr
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 115kB of archives.
After this operation, 426kB of additional disk space will be used.
Get:1 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick/universe lpr i386 1:2008.05.17 [115kB]
Fetched 115kB in 1s (73.2kB/s)
Selecting previously deselected package lpr.
(Reading database ... 371832 files and directories currently installed.)
Unpacking lpr (from .../lpr_1%3a2008.05.17_i386.deb) ...
Processing triggers for ureadahead ...
Processing triggers for man-db ...
Setting up lpr (1:2008.05.17) ...
update-rc.d: warning: /etc/init.d/lpd missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
start: Unknown job: lpd
invoke-rc.d: initscript lpd, action "start" failed.
dpkg: error processing lpr (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports has already been reached
                                                                    Errors were encountered while processing:
 lpr
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

