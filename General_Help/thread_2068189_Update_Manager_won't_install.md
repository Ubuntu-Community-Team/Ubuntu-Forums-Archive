---
title: "Update Manager won't install"
date: 2012-10-08
forum: General Help
---

### Post by Confused2570 on 2012-10-08
Hello! I accidentally uninstalled update manager ](*,) . I try to install it but it gives a package dependencies error. The error says: 

The following packages have unmet dependencies: 

update-manager: Depends: python (<2.8 ) but 2.7.3-0ubuntu2 is to be installed
             Depends: update-manager-core (= 1:0.156.14) but 1:0.156.14.9 is to be installed

That's the while message. If anyone can tell me how to fix this it I would be very greatful!

---

### Post by zvacet on 2012-10-09
Try to install it from **synaptic**.If you don´t have synaptic installed 

```
sudo apt-get install synaptic
```

Then in synaptic search box type update manager and when you find package install it.

---

### Post by Confused2570 on 2012-10-09
Thanks!

---

### Post by jerrrys on 2012-10-09
Here's how to use it

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=synaptic+package+manager&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=synaptic+package+manager&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by brevardo on 2012-10-09
I tried to install it and here's what I got. What am I missing here: rich@rich-Latitude-D620:~$ sudo apt-get install synaptic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 synaptic : Depends: libept1.4.12 but it is not going to be installed
 ubuntu-sso-client-gtk : Depends: python-ubuntu-sso-client (= 3.0.2-0ubuntu1) but 3.0.2-0ubuntu3 is to be installed
                         Depends: ubuntu-sso-client (= 3.0.2-0ubuntu1) but 3.0.2-0ubuntu3 is to be installed
 ubuntu-sso-client-qt : Depends: python-ubuntu-sso-client (= 3.0.2-0ubuntu1) but 3.0.2-0ubuntu3 is to be installed
                        Depends: ubuntu-sso-client (= 3.0.2-0ubuntu1) but 3.0.2-0ubuntu3 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
rich@rich-Latitude-D620:~$

---

### Post by jerrrys on 2012-10-09
Thought this was solved, its marked solved.

Unmet dependencies.  So you just need to follow the suggestion given.  In terminal enter:

sudo apt-get -f install

Edit:  If this gives you more errors, please post them and also post the output of:

cat /etc/apt/sources.list

---

### Post by brevardo on 2012-10-13
Thanks Jerrys. I just ran that and here's what I get:
                                    Errors were encountered while processing:
 ubuntu-sso-client-gtk
 software-center
 ubuntu-sso-client-qt
E: Sub-process /usr/bin/dpkg returned an error code (1)
rich@rich-Latitude-D620:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  ubuntu-sso-client-gtk ubuntu-sso-client-qt
The following packages will be upgraded:
  ubuntu-sso-client-gtk ubuntu-sso-client-qt
2 upgraded, 0 newly installed, 0 to remove and 17 not upgraded.
3 not fully installed or removed.
Need to get 0 B/569 kB of archives.
After this operation, 1,024 B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: dependency problems prevent configuration of ubuntu-sso-client-gtk:
 ubuntu-sso-client-gtk depends on python-ubuntu-sso-client (= 3.0.2-0ubuntu1); however:
  Version of python-ubuntu-sso-client on system is 3.0.2-0ubuntu3.
 ubuntu-sso-client-gtk depends on ubuntu-sso-client (= 3.0.2-0ubuntu1); however:
  Version of ubuntu-sso-client on system is 3.0.2-0ubuntu3.
dpkg: error processing ubuntu-sso-client-gtk (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          dpkg: dependency problems prevent configuration of software-center:
 software-center depends on ubuntu-sso-client-gtk; however:
  Package ubuntu-sso-client-gtk is not configured yet.
dpkg: error processing software-center (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-sso-client-qt:
 ubuntu-sso-client-qt depends on python-ubuntu-sso-client (= 3.0.2-0ubuntu1); however:
  Version of python-ubuntu-sso-client on system is 3.0.2-0ubuntu3.
 ubuntu-sso-client-qt depends on ubuntu-sso-client (= 3.0.2-0ubuntu1); however:
  Version of ubuntu-sso-client on system is 3.0.2-0ubuntu3.
dpkg: error processing ubuntu-sso-client-qt (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because MaxReports is reached already
        Errors were encountered while processing:
 ubuntu-sso-client-gtk
 software-center
 ubuntu-sso-client-qt
E: Sub-process /usr/bin/dpkg returned an error code (1)
rich@rich-Latitude-D620:~$

---

