---
title: "error in aptitude upgrade in ubuntu  10.04 beta2"
date: 2010-04-16
forum: General Help
---

### Post by balki2005 on 2010-04-16
when I would like to  upgrade  my system I recieve  this error, who can help me:

jonay@BlueDragon:~$ sudo aptitude upgrade 
W: The "upgrade" command is deprecated; use "safe-upgrade" instead.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following partially installed packages will be configured:
  libraptor1 librasqal2 librdf0 openoffice.org-base-core openoffice.org-calc openoffice.org-core openoffice.org-draw openoffice.org-gnome 
  openoffice.org-gtk openoffice.org-help-en-gb openoffice.org-help-en-us openoffice.org-impress openoffice.org-math openoffice.org-writer python-uno 
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Setting up libraptor1 (1.4.21-1ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libraptor1 (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of librasqal2:
 librasqal2 depends on libraptor1 (>= 1.4.19); however:
  Package libraptor1 is not configured yet.
dpkg: error processing librasqal2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of librdf0:
 librdf0 depends on libraptor1 (>= 1.4.19); however:
  Package libraptor1 is not configured yet.
 librdf0 depends on librasqal2 (>= 0.9.17); however:
  Package librasqal2 is not configured yet.
dpkg: error processing librdf0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-core:
 openoffice.org-core depends on librdf0 (>= 1.0.9); however:
  Package librdf0 is not configured yet.
dpkg: error procNo apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                                         No apport report written because MaxReports is reached already
                                                                                                                                       No apport report written because MaxReports is reached already
                                          No apport report written because MaxReports is reached already
                                                                                                        No apport report written because MaxReports is reached already
           No apport report written because MaxReports is reached already
                                                                         No apport report written because MaxReports is reached already
                                                                                                                                       No apport report written because MaxReports is reached already
                                          No apport report written because MaxReports is reached already
                                                                                                        No apport report written because MaxReports is reached already
           essing openoffice.org-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-base-core:
 openoffice.org-base-core depends on openoffice.org-core (= 1:3.2.0-7ubuntu1); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-base-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-calc:
 openoffice.org-calc depends on openoffice.org-core (= 1:3.2.0-7ubuntu1); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-calc depends on openoffice.org-base-core (= 1:3.2.0-7ubuntu1); however:
  Package openoffice.org-base-core is not configured yet.
dpkg: error processing openoffice.org-calc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-draw:
 openoffice.org-draw depends on openoffice.org-core (= 1:3.2.0-7ubuntuNo apport report written because MaxReports is reached already
                                                                                                                                    No apport report written because MaxReports is reached already
                                       No apport report written because MaxReports is reached already
                                                                                                     1); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-draw (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-gtk:
 openoffice.org-gtk depends on openoffice.org-core (= 1:3.2.0-7ubuntu1); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-gnome:
 openoffice.org-gnome depends on openoffice.org-core (= 1:3.2.0-7ubuntu1); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-gnome depends on openoffice.org-gtk; however:
  Package openoffice.org-gtk is not configured yet.
dpkg: error processing openoffice.org-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-writer:
 openoffice.org-writer depends on openoffice.org-core (= 1:3.2.0-7ubuntu1); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-writer depends on openoffice.org-base-core (= 1:3.2.0-7ubuntu1); however:
  Package openoffice.org-base-core is not configured yet.
dpkg: error processing openoffice.org-writer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-help-en-gb:
 openoffice.org-help-en-gb depends on openoffice.org-writer | language-support-translations-en; however:
  Package openoffice.org-writer is not configured yet.
  Package language-support-translations-en is not installed.
dpkg: error processing openoffice.org-help-en-gb (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-help-en-us:
 openoffice.org-help-en-us depends on openoffice.org-writer | language-support-translations-en; however:
  Package openoffice.org-writer is not configured yet.
  Package language-support-translations-en is not installed.
dpkg: error processing openoffice.org-help-en-us (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-impress:
 openoffice.org-impress depends on openoffice.org-core (= 1:3.2.0-7ubuntu1); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-impress depends on openoffice.org-draw (= 1:3.2.0-7ubuntu1); however:
  Package openoffice.org-draw is not configured yet.
dpkg: error processing openoffice.org-impress (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-math:
 openoffice.org-math depends on openoffice.org-core (= 1:3.2.0-7ubuntu1); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-math (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-uno:
 python-uno depends on openoffice.org-core (= 1:3.2.0-7ubuntu1); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing python-uno (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libraptor1
 librasqal2
 librdf0
 openoffice.org-core
 openoffice.org-base-core
 openoffice.org-calc
 openoffice.org-draw
 openoffice.org-gtk
 openoffice.org-gnome
 openoffice.org-writer
 openoffice.org-help-en-gb
 openoffice.org-help-en-us
 openoffice.org-impress
 openoffice.org-math
 python-uno
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up libraptor1 (1.4.21-1ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libraptor1 (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of librdf0:
 librdf0 depends on libraptor1 (>= 1.4.19); however:
  Package libraptor1 is not configured yet.
dpkg: error processing librdf0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-core:
 openoffice.org-core depends on librdf0 (>= 1.0.9); however:
  Package librdf0 is not configured yet.
dpkg: error processing openoffice.org-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-draw:
 openoffice.org-draw depends on openoffice.org-core (= 1:3.2.0-7ubuntu1); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-draw (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-gtk:
 openoffice.org-gtk depends on openoffice.org-core (= 1:3.2.0-7ubuntu1); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-calc:
 openoffice.org-calc depends on openoffice.org-core (= 1:3.2.0-7ubuntu1); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-calc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of librasqal2:
 librasqal2 depends on libraptor1 (>= 1.4.19); however:
  Package libraptor1 is not configured yet.
dpkg: error processing librasqal2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-base-core:
 openoffice.org-base-core depends on openoffice.org-core (= 1:3.2.0-7ubuntu1); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-base-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-writer:
 openoffice.org-writer depends on openoffice.org-core (= 1:3.2.0-7ubuntu1); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-writer depends on openoffice.org-base-core (= 1:3.2.0-7ubuntu1); however:
  Package openoffice.org-base-core is not configured yet.
dpkg: error processing openoffice.org-writer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-uno:
 python-uno depends on openoffice.org-core (= 1:3.2.0-7ubuntu1); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing python-uno (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-help-en-us:
 openoffice.org-help-en-us depends on openoffice.org-writer | language-support-translations-en; however:
  Package openoffice.org-writer is not configured yet.
  Package language-support-translations-en is not installed.
dpkg: error processing openoffice.org-help-en-us (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-gnome:
 openoffice.org-gnome depends on openoffice.org-core (= 1:3.2.0-7ubuntu1); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-gnome depends on openoffice.org-gtk; however:
  Package openoffice.org-gtk is not configured yet.
dpkg: error processing openoffice.org-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-impress:
 openoffice.org-impress depends on openoffice.org-core (= 1:3.2.0-7ubuntu1); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-impress depends on openoffice.org-draw (= 1:3.2.0-7ubuntu1); however:
  Package openoffice.org-draw is not configured yet.
dpkg: error processing openoffice.org-impress (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-help-en-gb:
 openoffice.org-help-en-gb depends on openoffice.org-writer | language-support-translations-en; however:
  Package openoffice.org-writer is not configured yet.
  Package language-support-translations-en is not installed.
dpkg: error processing openoffice.org-help-en-gb (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-math:
 openoffice.org-math depends on openoffice.org-core (= 1:3.2.0-7ubuntu1); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-math (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libraptor1
 librdf0
 openoffice.org-core
 openoffice.org-draw
 openoffice.org-gtk
 openoffice.org-calc
 librasqal2
 openoffice.org-base-core
 openoffice.org-writer
 python-uno
 openoffice.org-help-en-us
 openoffice.org-gnome
 openoffice.org-impress
 openoffice.org-help-en-gb
 openoffice.org-math
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

jonay@BlueDragon:~$

thanks  in advance,

Jonay alias balki2005

---

### Post by zvacet on 2010-04-16
```
sudo aptitude safe-upgrade
```

If you get any errors 

```
sudo dpkg --configure -a
```

---

### Post by balki2005 on 2010-04-16
hello,

thanks for  the  quick  answer,  I allready  tried  this .... with  the  same  result:

```

jonay@BlueDragon:~$ sudo dpkg --configure -a
[sudo] password for jonay: 
Sorry, try again.
[sudo] password for jonay: 
Setting up libraptor1 (1.4.21-1ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libraptor1 (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of librdf0:
 librdf0 depends on libraptor1 (>= 1.4.19); however:
  Package libraptor1 is not configured yet.
dpkg: error processing librdf0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-core:
 openoffice.org-core depends on librdf0 (>= 1.0.9); however:
  Package librdf0 is not configured yet.
dpkg: error processing openoffice.org-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-draw:
 openoffice.org-draw depends on openoffice.org-core (= 1:3.2.0-7ubuntu1); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-draw (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-gtk:
 openoffice.org-gtk depends on openoffice.org-core (= 1:3.2.0-7ubuntu1); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-calc:
 openoffice.org-calc depends on openoffice.org-core (= 1:3.2.0-7ubuntu1); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-calc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of librasqal2:
 librasqal2 depends on libraptor1 (>= 1.4.19); however:
  Package libraptor1 is not configured yet.
dpkg: error processing librasqal2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-base-core:
 openoffice.org-base-core depends on openoffice.org-core (= 1:3.2.0-7ubuntu1); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-base-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-writer:
 openoffice.org-writer depends on openoffice.org-core (= 1:3.2.0-7ubuntu1); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-writer depends on openoffice.org-base-core (= 1:3.2.0-7ubuntu1); however:
  Package openoffice.org-base-core is not configured yet.
dpkg: error processing openoffice.org-writer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-uno:
 python-uno depends on openoffice.org-core (= 1:3.2.0-7ubuntu1); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing python-uno (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-help-en-us:
 openoffice.org-help-en-us depends on openoffice.org-writer | language-support-translations-en; however:
  Package openoffice.org-writer is not configured yet.
  Package language-support-translations-en is not installed.
dpkg: error processing openoffice.org-help-en-us (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-gnome:
 openoffice.org-gnome depends on openoffice.org-core (= 1:3.2.0-7ubuntu1); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-gnome depends on openoffice.org-gtk; however:
  Package openoffice.org-gtk is not configured yet.
dpkg: error processing openoffice.org-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-impress:
 openoffice.org-impress depends on openoffice.org-core (= 1:3.2.0-7ubuntu1); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-impress depends on openoffice.org-draw (= 1:3.2.0-7ubuntu1); however:
  Package openoffice.org-draw is not configured yet.
dpkg: error processing openoffice.org-impress (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-help-en-gb:
 openoffice.org-help-en-gb depends on openoffice.org-writer | language-support-translations-en; however:
  Package openoffice.org-writer is not configured yet.
  Package language-support-translations-en is not installed.
dpkg: error processing openoffice.org-help-en-gb (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-math:
 openoffice.org-math depends on openoffice.org-core (= 1:3.2.0-7ubuntu1); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-math (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libraptor1
 librdf0
 openoffice.org-core
 openoffice.org-draw
 openoffice.org-gtk
 openoffice.org-calc
 librasqal2
 openoffice.org-base-core
 openoffice.org-writer
 python-uno
 openoffice.org-help-en-us
 openoffice.org-gnome
 openoffice.org-impress
 openoffice.org-help-en-gb
 openoffice.org-math
jonay@BlueDragon:~$ 

```

---

### Post by zvacet on 2010-04-16
```
sudo apt-get -f install
```

```
sudo dpkg --configure -a
```

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by balki2005 on 2010-04-23
thanks  for youre  solutions. I resolved  by removing first openoffice and install first all  the  dependencies: 
libraptor1
librdf0

now it works fine again.

thanks,

jonay = balki2005

---

