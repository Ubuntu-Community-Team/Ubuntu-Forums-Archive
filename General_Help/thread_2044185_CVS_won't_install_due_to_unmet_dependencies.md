---
title: "CVS won't install due to unmet dependencies"
date: 2012-08-18
forum: General Help
---

### Post by giovannik on 2012-08-18
I'm unable to install CVS due to unmet dependencies. The dependencies are for libraries that are older than what's currently on the system.  Here is the error message being displayed:
The following packages have unmet dependencies:
 bind9 : Depends: libbind9-80 (= 1:9.8.1.dfsg.P1-4ubuntu0.1) but 1:9.8.1.dfsg.P1-4ubuntu0.2 is to be installed
         Depends: libdns81 (= 1:9.8.1.dfsg.P1-4ubuntu0.1) but 1:9.8.1.dfsg.P1-4ubuntu0.2 is to be installed
         Depends: libisc83 (= 1:9.8.1.dfsg.P1-4ubuntu0.1) but 1:9.8.1.dfsg.P1-4ubuntu0.2 is to be installed
         Depends: libisccc80 (= 1:9.8.1.dfsg.P1-4ubuntu0.1) but 1:9.8.1.dfsg.P1-4ubuntu0.2 is to be installed
         Depends: libisccfg82 (= 1:9.8.1.dfsg.P1-4ubuntu0.1) but 1:9.8.1.dfsg.P1-4ubuntu0.2 is to be installed
         Depends: liblwres80 (= 1:9.8.1.dfsg.P1-4ubuntu0.1) but 1:9.8.1.dfsg.P1-4ubuntu0.2 is to be installed
         Depends: bind9utils (= 1:9.8.1.dfsg.P1-4ubuntu0.1) but 1:9.8.1.dfsg.P1-4ubuntu0.2 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

I tried to the apt-get -f install option but to no avail.  I'm attempting to install this on a Ubuntu 12.04 LTS Server.

Thanks in advance for any help/suggestions.

---

### Post by giovannik on 2012-08-19
So, what I need to figure out is how do I make CVS install with these more recent libraries.  Or how do I get the older libraries to install so CVS will install?

Thanks

---

### Post by mc4man on 2012-08-19
I would open software sources, from terminal it would be 
```
software-properties-gtk
```
Under the 'Ubuntu Software' tab make sure the 1st 4 are checked

Most importantly under the 'Updates' make sure that the 1st 2 are checked
Then close out & update your sources

sudo apt-get update

If bind9 doesn't then show an upgrade to 1:9.8.1.dfsg.P1-4ubuntu0.2 you could try 

sudo apt-get dist-upgrade

Or install synaptic & see why not.

current bind9 in ubuntu 12.04 was a security update
[http://packages.ubuntu.com/precise-updates/bind9](http://packages.ubuntu.com/precise-updates/bind9)

---

### Post by giovannik on 2012-09-11
It looks to me like  1:9.8.1.dfsg.P1-4ubuntu0.2 is currently installed on my system.  The installer seems to be complaining that it wants a prior version of this library on my system instead.  I've noticed now that no matter what software I install I get this message or something similar:

bind9 : Depends: libbind9-80 (= 1:9.8.1.dfsg.P1-4ubuntu0.1) but 1:9.8.1.dfsg.P1-4ubuntu0.2 is to be installed
         Depends: libdns81 (= 1:9.8.1.dfsg.P1-4ubuntu0.1) but 1:9.8.1.dfsg.P1-4ubuntu0.2 is to be installed
         Depends: libisc83 (= 1:9.8.1.dfsg.P1-4ubuntu0.1) but 1:9.8.1.dfsg.P1-4ubuntu0.2 is to be installed
         Depends: libisccc80 (= 1:9.8.1.dfsg.P1-4ubuntu0.1) but 1:9.8.1.dfsg.P1-4ubuntu0.2 is to be installed
         Depends: libisccfg82 (= 1:9.8.1.dfsg.P1-4ubuntu0.1) but 1:9.8.1.dfsg.P1-4ubuntu0.2 is to be installed
         Depends: liblwres80 (= 1:9.8.1.dfsg.P1-4ubuntu0.1) but 1:9.8.1.dfsg.P1-4ubuntu0.2 is to be installed
         Depends: bind9utils (= 1:9.8.1.dfsg.P1-4ubuntu0.1) but 1:9.8.1.dfsg.P1-4ubuntu0.2 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

When I try sudo apt-get -f install :

dpkg: dependency problems prevent configuration of bind9:
 bind9 depends on libbind9-80 (= 1:9.8.1.dfsg.P1-4ubuntu0.1); however:
  Version of libbind9-80 on system is 1:9.8.1.dfsg.P1-4ubuntu0.2.
 bind9 depends on libdns81 (= 1:9.8.1.dfsg.P1-4ubuntu0.1); however:
  Version of libdns81 on system is 1:9.8.1.dfsg.P1-4ubuntu0.2.
 bind9 depends on libisc83 (= 1:9.8.1.dfsg.P1-4ubuntu0.1); however:
  Version of libisc83 on system is 1:9.8.1.dfsg.P1-4ubuntu0.2.
 bind9 depends on libisccc80 (= 1:9.8.1.dfsg.P1-4ubuntu0.1); however:
  Version of libisccc80 on system is 1:9.8.1.dfsg.P1-4ubuntu0.2.
 bind9 depends on libisccfg82 (= 1:9.8.1.dfsg.P1-4ubuntu0.1); however:
  Version of libisccfg82 on system is 1:9.8.1.dfsg.P1-4ubuntu0.2.
 bind9 depends on liblwres80 (= 1:9.8.1.dfsg.P1-4ubuntu0.1); however:
  Version of liblwres80 on system is 1:9.8.1.dfsg.P1-4ubuntu0.2.
 bind9 depends on bind9utils (= 1:9.8.1.dfsg.P1-4ubuntu0.1); however:
  Version of bind9utils on system is 1:9.8.1.dfsg.P1-4ubuntu0.2.
dpkg: error processing bind9 (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 bind9
E: Sub-process /usr/bin/dpkg returned an error code (1)

So, how do I find out what the previous error was?  What's wrong with my current installation that I can installl anything?  This is a server install of Ubuntu without the graphical interface.  

When i do a software-properties-gtk I get a message that it's not installed which I think is due to the fact that I don't have the graphical interface installed.

---

