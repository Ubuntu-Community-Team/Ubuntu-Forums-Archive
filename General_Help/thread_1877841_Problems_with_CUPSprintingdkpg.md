---
title: "Problems with CUPS/printing/dkpg"
date: 2011-11-08
forum: General Help
---

### Post by thyagw on 2011-11-08
Hey guys
i'm not new with ubuntu but i'm experiencing problems since a HD change
I copied everything with Gparted and it's working perfectly, except the printer
When I go to the printer menu, it keeps asking me for a cups server, and does not allow me to click on the "add" button
I tried reinstalling cups. Purged and removed using synaptics, and now when i try to install it, I get this on terminal

```
thiago@thiago-notebook:~$ sudo apt-get install cups
[sudo] password for thiago: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
cups is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up cups (1.4.6-5ubuntu1.4) ...
start: Job failed to start
invoke-rc.d: initscript cups, action "start" failed.
dpkg: error processing cups (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of cups-driver-gutenprint:
 cups-driver-gutenprint depends on cups (>= 1.3.0); however:
  Package cups is not configured yet.
dpkg: error processing cups-driver-gutenprint (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 cups
 cups-driver-gutenprint
W: Duplicate sources.list entry http://ppa.launchpad.net/osd-lyrics/ppa/ubuntu/ natty/main amd64 Packages (/var/lib/apt/lists/ppa.launchpad.net_osd-lyrics_ppa_ubuntu_dists_natty_main_binary-amd64_Packages)
W: You may want to run apt-get update to correct these problems
E: Sub-process /usr/bin/dpkg returned an error code (1)
```could anybody help me? thanks!

---

### Post by thyagw on 2011-11-09
bump

---

### Post by GypD on 2011-11-11
Thank You Thyagw, your input helped my pc to find my HP PSC All-in-One printer/scanner so I hope you find a solution to your printer recognition problem soon -Gypd.

---

### Post by davidvolvox on 2011-11-14
I have the same problem since upgrading to 11.10. As Thyagw says no amount of installing, reinstalling, restarting resolves the issue that cups is not configured so is not running.  What is the dependency conflict? Where do we need to look for that information?

---

### Post by thyagw on 2011-11-18
BUMP
please help me out

---

### Post by thyagw on 2011-11-18
BUMP
please help me out

---

### Post by davidvolvox on 2011-11-20
I am not optimistic about this. I have another machine running 11.04 and CUPS is fine as it was on my problem machine before upgrading to 11.10.

It looks like the old Windows approach of test and test again before going to your mission critical system(s).

---

