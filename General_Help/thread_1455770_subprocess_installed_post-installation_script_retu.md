---
title: "subprocess installed post-installation script returned error exit status 2"
date: 2010-04-16
forum: General Help
---

### Post by Mazlaghan on 2010-04-16
hello world,

i have a problem and it's been persisting since i installes MST Core fonts.

any ideas?

terminal log is here:

-----------start of pasting -----

user@Ubuntu9:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up ttf-liberation (1.05.1.20090721-0ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing ttf-liberation (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up ttf-mscorefonts-installer (3.0) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing ttf-mscorefonts-installer (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 ttf-liberation
 ttf-mscorefonts-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
user@Ubuntu9:~$ 

----end of pasting ----

:guitar: your help is most appreciated. the problem comes up every time i install / update the system (the apps still get installed)

thanks for your help!!!

---

### Post by dcstar on 2010-04-17
> **Mazlaghan said:**
> hello world,

i have a problem and it's been persisting since i installes MST Core fonts.

any ideas?
////////
Errors were encountered while processing:
[B] ttf-liberation
 ttf-mscorefonts-installer[/B]
E: Sub-process /usr/bin/dpkg returned an error code (1)
user@Ubuntu9:~$ 

----end of pasting ----

:guitar: your help is most appreciated. the problem comes up every time i install / update the system (the apps still get installed)

thanks for your help!!!

Remove those packages and reinstall them.

---

