---
title: "Help, cannot remove ANYTHING (synaptic/apt-get)"
date: 2009-12-12
forum: General Help
---

### Post by TheNessus on 2009-12-12
I have installed a game through the ubuntu software center: Nexuiz, however, when I try to remove it (or anything else, for that matter) I get this:

jeff@jeff-laptop:~$ sudo apt-get remove nexuiz
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  empathy-doc libmd5-perl libgtk2-sexy-perl libcrypt-ssleay-perl
  libxml-namespacesupport-perl libgtk2-trayicon-perl libxml-sax-expat-perl
  libcrypt-simple-perl libcrypt-blowfish-perl libxml-sax-perl
  libxml-simple-perl libsexymm2 libemail-mime-encodings-perl
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  nexuiz
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 1,982kB disk space will be freed.
Do you want to continue [Y/n]? yes
(Reading database ... 266687 files and directories currently installed.)
Removing nexuiz ...
dpkg (subprocess): unable to execute installed post-removal script: Exec format error
dpkg: error processing nexuiz (--remove):
 subprocess installed post-removal script returned error exit status 2
Errors were encountered while processing:
 nexuiz
E: Sub-process /usr/bin/dpkg returned an error code (1)
jeff@jeff-laptop:~$

---

### Post by Leppie on 2009-12-12
try re-installing the game in synaptic first.

---

### Post by TheNessus on 2009-12-12
hmm, yep, removing it worked now. spanks :)

---

### Post by Leppie on 2009-12-12
glad it worked ;)

---

