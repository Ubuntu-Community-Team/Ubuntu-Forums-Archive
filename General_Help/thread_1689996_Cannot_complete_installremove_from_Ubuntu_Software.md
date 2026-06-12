---
title: "Cannot complete install/remove from Ubuntu Software Center"
date: 2011-02-17
forum: General Help
---

### Post by micael3000 on 2011-02-17
Hello,

When I try to install or remove ANYTHING from Ubuntu Software Center that's what happens:

```
installArchives() failed: (Reading database ...  
(Reading database ... 5% 
(Reading database ... 10% 
(Reading database ... 15% 
(Reading database ... 20% 
(Reading database ... 25% 
(Reading database ... 30% 
(Reading database ... 35% 
(Reading database ... 40% 
(Reading database ... 45% 
(Reading database ... 50% 
(Reading database ... 55% 
(Reading database ... 60% 
(Reading database ... 65% 
(Reading database ... 70% 
(Reading database ... 75% 
(Reading database ... 80% 
(Reading database ... 85% 
(Reading database ... 90% 
(Reading database ... 95% 
(Reading database ... 100% 
(Reading database ... 282337 files and directories currently installed.) 
Removing kmess ... 
Processing triggers for menu ... 
Processing triggers for man-db ... 
Processing triggers for hicolor-icon-theme ... 
Processing triggers for desktop-file-utils ... 
Processing triggers for python-gmenu ... 
Rebuilding /usr/share/applications/desktop.en_US.UTF8.cache... 
Processing triggers for python-support ... 
Setting up prelude-lml (1.0.0-1) ... 
Starting Prelude LML: prelude-lmlinvoke-rc.d: initscript prelude-lml, action "start" failed. 
dpkg: error processing prelude-lml (--configure): 
 subprocess installed post-installation script returned error exit status 1 
No apport report written because MaxReports is reached already
Errors were encountered while processing: 
 prelude-lml 
Setting up prelude-lml (1.0.0-1) ... 
Starting Prelude LML: prelude-lmlinvoke-rc.d: initscript prelude-lml, action "start" failed. 
dpkg: error processing prelude-lml (--configure): 
 subprocess installed post-installation script returned error exit status 1 

```Does anyone know how can I fix it? :/

Thanks :)

---

### Post by micael3000 on 2011-02-18
Bump...

I have installed all language packs and, at the end of installation, I, again, got the prelude error :/

---

### Post by Rubi1200 on 2011-02-18
Try the following in the terminal:

```
sudo apt-get install -f

sudo dpkg --configure -a

sudo apt-get update
```

If any of these report errors, post back here with the specifics please.

---

### Post by micael3000 on 2011-02-18
```
micael@SLaptop:~$ sudo apt-get install -f
[sudo] password for micael: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up prelude-lml (1.0.0-1) ...
Starting Prelude LML: prelude-lmlinvoke-rc.d: initscript prelude-lml, action "start" failed.
dpkg: error processing prelude-lml (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 prelude-lml
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

```
micael@SLaptop:~$ sudo dpkg --configure -a
Setting up prelude-lml (1.0.0-1) ...
Starting Prelude LML: prelude-lmlinvoke-rc.d: initscript prelude-lml, action "start" failed.
dpkg: error processing prelude-lml (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 prelude-lml

```

apt-get update OK

---

### Post by Rubi1200 on 2011-02-18
It seems this prelude-lml package is causing the problems.

Did you install it directly or as part of something else?

Have you checked that it has all the required dependencies?

You might want to try reinstalling it again and see what happens.

---

### Post by micael3000 on 2011-02-19
I have removed it (apt-get remove ...) and the problem now is fixed.

I had no idea that it was a package 'removable' heheh

---

### Post by Rubi1200 on 2011-02-19
Glad you got things sorted out :-)

---

