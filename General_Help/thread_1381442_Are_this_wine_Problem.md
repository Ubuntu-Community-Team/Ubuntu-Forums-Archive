---
title: "Are this wine Problem"
date: 2010-01-14
forum: General Help
---

### Post by autorobot14 on 2010-01-14
Aloo...I'm new here...i'm using ubuntu 9.10...i have this problem  when i install the some application...i forgot what the application that i was installed.. Everytime is install what ever application the will came to this error..Other than that..my wine cannot running perfectly.. 

> sharp@sharp-desktop:~$ sudo apt-get remove wine
[sudo] password for sharp: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package wine is not installed, so not removed
The following packages were automatically installed and are no longer required:
  ttf-liberation ttf-mscorefonts-installer cabextract winbind
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up libfontconfig1-dev (2.6.0-1ubuntu12) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libfontconfig1-dev (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of libxft-dev:
 libxft-dev depends on libfontconfig1-dev; however:
  Package libfontconfig1-dev is not configured yet.
dpkg: error processing libxft-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libcairo2-dev:
 libcairo2-dev depends on libfontconfig1-dev (>= 2.5.92); however:
  Package libfontconfig1-dev is not configured yet.
dpkg: error processing libcairo2-dev (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    Errors were encountered while processing:
 libfontconfig1-dev
 libxft-dev
 libcairo2-dev
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by llamabr on 2010-01-14
I'm not sure I understand your question, but did you try running:

```
sudo apt-get autoremove
```

---

### Post by Saiko Berry on 2010-01-14
..do you have wine installed?

sudo apt-get install wine

---

### Post by rodrigo.toste.gomes on 2010-01-14
It appears that you have some broken dependencies or some other type of incomplete installation of packages that are impeding apt-get work.
Try reading this:
[http://www.linux.com/archive/feature/48910](http://www.linux.com/archive/feature/48910)
If you don't want to read, try running:
sudo dpkg --configure -a

---

### Post by autorobot14 on 2010-01-15
I do install wine. Then I remove it. sudo apt-get autoremove i have done it..but the problem still the same, evertimes I install or remove a program..There will  show this error. I don't understand what is the problem.

>   Errors were encountered while processing:
 libfontconfig1-dev
 libxft-dev
 libcairo2-dev
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by autorobot14 on 2010-01-15
> **rodrigo.toste.gomes said:**
> It appears that you have some broken dependencies or some other type of incomplete installation of packages that are impeding apt-get work.
Try reading this:
[http://www.linux.com/archive/feature/48910](http://www.linux.com/archive/feature/48910)
If you don't want to read, try running:
sudo dpkg --configure -a

I have try it...but still i have the same problem

---

