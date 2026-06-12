---
title: "Package Manager Broken"
date: 2011-03-25
forum: General Help
---

### Post by Orcris on 2011-03-25
I'm sorry if this topic has already come up, but My package manager is broken, and when I press repair, it says it can't repair because the package manager is broken. I'm pretty sure the code is ```
sudo apt-get install -f
``` It still doesn't work. Any suggestions?

---

### Post by garvinrick4 on 2011-03-25
```
sudo apt-get -f install
```
or
```
sudo dpkg --configure -a
```

---

### Post by Orcris on 2011-03-25
Thanks, but when I entered the first code, it said ```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.35-22 linux-headers-2.6.35-22-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  mathematica-fonts
The following NEW packages will be installed:
  mathematica-fonts
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/cache/apt/archives/
``` and when I entered the second one, it said ```
dpkg: dependency problems prevent configuration of ttf-mathematica4.1:
 ttf-mathematica4.1 depends on mathematica-fonts; however:
  Package mathematica-fonts is not installed.
dpkg: error processing ttf-mathematica4.1 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ttf-mathematica4.1
andrew@andrew-DIM4400:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.35-22 linux-headers-2.6.35-22-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  mathematica-fonts
The following NEW packages will be installed:
  mathematica-fonts
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/cache/apt/archives/

```
The error says: E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory
 If I really need to, I can reinstall Ubuntu, since there isn't really anything saved on here, but that is kind of extreme, and I would like to stay away from that.

---

### Post by garvinrick4 on 2011-03-26
Go to Synaptics and type in mathematica-fonts and then right click on and remove.
 by hitting apply arrow, then go to terminal and:
```
sudo dpkg --configure -a
```If you want to in terminal you can try to purge:
```
sudo apt-get purge mathematica-fonts
```Package: mathematica-fonts
State: not installed
Version: 11
Priority: extra
Section: multiverse/fonts
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 127k
Depends: unzip
PreDepends: debconf (>= 0.5) | debconf-2.0
Conflicts: ttf-mathematica4.1 (< 9)
Replaces: ttf-mathematica4.1 (< 9)
Provides: ttf-mathematica4.1
Description: Installer of Mathematica fonts
 **This package downloads Mathematica fonts through an internet and installs them,
 because the license prohibits distribution of the fonts.  NOTE the fonts might
 be removed from a web site so it might happen that you failed to download the
 fonts. 
 
 This package will install only AFM, TTF and Type1 at present.
*Seems you tried to download and install from site at sometime or another.*

---

### Post by Orcris on 2011-03-28
Thanks. It's fixed now, because I accidentally destroyed my home partition and had to reinstall Ubuntu. That posed other problems.

---

### Post by monsterwizard on 2012-01-11
Ok, I had the same problems as the other guy until I put in the second code, 
sudo dpkg --configure -a
and got something different, I got
,
owner@ubuntu:~$ sudo dpkg --configure -a
[sudo] password for owner: 
Setting up linux-image-2.6.38-11-generic (2.6.38-11.50) ...
Running depmod.
Failed to run depmod
dpkg: error processing linux-image-2.6.38-11-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of update-manager:
 update-manager depends on update-manager-core (= 1:0.150.3); however:
  Version of update-manager-core on system is 1:0.150.5.1.
dpkg: error processing update-manager (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.38-11-generic
 update-manager
owner@ubuntu:~$ 

any help?
Scott

---

