---
title: "A lot has gone wrong."
date: 2012-01-17
forum: General Help
---

### Post by Iblis92 on 2012-01-17
At first I was trying to get Ushare to work, but something didnt work and I just forget it and moved on. I was then trying to get my bluetooth on my netbook to work, and saw some forum where someone typed a command to diagnose the problem or something, i dont remember it was. And now, everytime I type something in, it thinks im trying to force install ushare EVERY TIME. So, 3 things just went wrong in the span of 10 minutes. Lookin for some help on these things, firstly that I pretty much cant use terminal anymore cuz its always displaying this:
[B]iblis@iblis-1005HA:~$ sudo apt-get install rfkill
[sudo] password for iblis: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
rfkill is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-3.0.0-12 linux-headers-3.0.0-12-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 43 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up ushare (1.1a-0ubuntu6) ...
/etc/ushare.conf: 6: Netbook: not found
dpkg: error processing ushare (--configure):
 subprocess installed post-installation script returned error exit status 127
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 ushare
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/B]

Im not sure what to do here. But id like to fix this so I can move on to trying to fix my bluetooth too, which if i may have to make an entire new thread for.
EDIT: now giving the code a more thourough look, i see that rfkill is already on there, however its doing this for every command

---

### Post by raja.genupula on 2012-01-17
sudo apt-get autoclean
sudo apt-get autoremove

sudo apt-get update

try them once.

---

