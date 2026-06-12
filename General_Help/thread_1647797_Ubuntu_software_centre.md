---
title: "Ubuntu software centre"
date: 2010-12-17
forum: General Help
---

### Post by whvw on 2010-12-17
Ever since I had trouble downloading a programme called "WebHTTrack Website Copier" , the Ubuntu software centre won't work. Some pgms will download, but all will return errors. Here's a printout:

installArchives() failed: Selecting previously deselected package xpn. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 171793 files and directories currently installed.) 
Unpacking xpn (from .../xpn_1.2.6-1ubuntu1_all.deb) ... 
Processing triggers for desktop-file-utils ... 
Processing triggers for man-db ... 
Processing triggers for menu ... 
Setting up ttf-mscorefonts-installer (3.0) ... 
 
These fonts were provided by Microsoft "in the interest of cross- 
platform compatibility".  This is no longer the case, but they are 
still available from third parties. 
 
You are free to download these fonts and use them for your own use, 
but you may not redistribute them in modified form, including changes 
to the file name or packaging format. 
 
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name. 
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name. 
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name. 
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name. 
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name. 
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name. 
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name. 
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name. 
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name. 
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name. 
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name. 
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name. 
sha256sum: andale32.exe: No such file or directory 
andale32.exe: FAILED open or read 
sha256sum: WARNING: 1 of 1 listed file could not be read 
Checksum mismatch for andale32.exe, aborting! 
dpkg: error processing ttf-mscorefonts-installer (--configure): 
 subprocess installed post-installation script returned error exit status 1 
dpkg: dependency problems prevent configuration of msttcorefonts: 
 msttcorefonts depends on ttf-mscorefonts-installer; however: 
  Package ttf-mscorefonts-installer is not configured yet. 
dpkg: error processing msttcorefonts (--configure): 
 dependency problems - leaving unconfigured 
Setting up xpn (1.2.6-1ubuntu1) ... 
No apport report written because the error message indicates its a followup error from a previous failure.
 
Processing triggers for menu ... 
Errors were encountered while processing: 
 ttf-mscorefonts-installer 
 msttcorefonts 


Yes, I've tried changing to "direct internet connection", and the M$ fonts thing,* all to no avail*. Internet browsing & e-mail work fine. Can anyone help?

---

### Post by dcstar on 2010-12-18
> **whvw said:**
> Ever since I had trouble downloading a programme called "WebHTTrack Website Copier" , the Ubuntu software centre won't work. Some pgms will download, but all will return errors. Here's a printout:
........ 
**Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.** 
........
Yes, I've tried changing to "direct internet connection", and the M$ fonts thing,* all to no avail*. Internet browsing & e-mail work fine. Can anyone help?

Your system is set to use some bogus HTTP Proxy Server. Fix the Proxy settings in Synaptic as well as the System-Preferences-Network Proxy.

---

### Post by whvw on 2010-12-18
No, both network connections and synaptic are both set to "direct internet connection".

---

### Post by A N on 2011-06-12
i am new to ubuntu, just installed ubuntu 11.04 on my new laptop a few days ago
the ubuntu software centre was working perfectly well for me till yesterday, when i tried to install gparted using the terminal:
sudo apt-get install gparted

it was giving me an error and i was asked to use either the update or fix-missing command, i used the former:
sudo apt-get update

but neither the update reached its successful end after taking a long time, nor does the sw centre now download anything
from then on the software centre gives me the error:** check your internet connection**
i suppose these issues are linked, but all i want is my SW Centre working properly, also rest of the Ubuntu

HELP PLEASE, A.S.A.P.
I'll be really greatful

---

### Post by danieee on 2011-06-16
> **A N said:**
> i am new to ubuntu, just installed ubuntu 11.04 on my new laptop a few days ago
the ubuntu software centre was working perfectly well for me till yesterday, when i tried to install gparted using the terminal:
sudo apt-get install gparted

it was giving me an error and i was asked to use either the update or fix-missing command, i used the former:
sudo apt-get update

but neither the update reached its successful end after taking a long time, nor does the sw centre now download anything
from then on the software centre gives me the error:** check your internet connection**
i suppose these issues are linked, but all i want is my SW Centre working properly, also rest of the Ubuntu


I'll be really greatful

HELP PLEASE, A.S.A.P.

This usually happens when you do not completely install and application.  it kinda leaves the app neither uninstalled nor installed.
try this,,
run synaptic package manager app,, click on edit menu, and then click on fix broken..
after this run sudo apt-get update from a terminal 
hope this helps

---

