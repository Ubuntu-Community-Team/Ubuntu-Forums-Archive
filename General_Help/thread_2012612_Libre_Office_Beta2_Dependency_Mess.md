---
title: "Libre Office Beta2 Dependency Mess"
date: 2012-06-29
forum: General Help
---

### Post by neu5eeCh on 2012-06-29
So... I wanted to try the latest Beta of Libre Office.

I disabled the stable repository and installed the libreoffice-prereleases PPA. Now, for one reason or other, I've gotten into a snarled up tangle of dependency issues:

If I **sudo apt-get -f install**, I get:

> The following package was automatically installed and is no longer required:
  libcmis-0.2-0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libreoffice-core
The following packages will be upgraded:
  libreoffice-core
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


**Then**:

> dpkg: dependency problems prevent configuration of libreoffice-core:
 libreoffice-common (1:3.6.0~beta2-0ubuntu1~ppa3~precise1) breaks libreoffice-core (<< 1:3.6~) and is installed.
  Version of libreoffice-core to be configured is 1:3.5.5~rc2-0ubuntu1~ppa1.
dpkg: error processing libreoffice-core (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                   dpkg: dependency problems prevent configuration of libreoffice-base-core:
 libreoffice-base-core depends on libreoffice-core (= 1:3.6.0~beta2-0ubuntu1~ppa3~precise1); however:
  Version of libreoffice-core on system is 1:3.5.5~rc2-0ubuntu1~ppa1.
dpkg: error processing libreoffice-base-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-writer:
 libreoffice-writer depends on libreoffice-core (= 1:3.6.0~beta2-0ubuntu1~ppa3~precise1); however:
  Version of libreoffice-core on system is 1:3.5.5~rc2-0ubuntu1~ppa1.
No apport report written because the error message indicates its a followup error from a previous failure.
                    libreoffice-writer depends on libreoffice-base-core (= 1:3.6.0~beta2-0ubuntu1~ppa3~precise1); however:
  Package libreoffice-base-core is not configured yet.
dpkg: error processing libreoffice-writer (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                   dpkg: dependency problems prevent configuration of libreoffice-calc:
 libreoffice-calc depends on libreoffice-core (= 1:3.6.0~beta2-0ubuntu1~ppa3~precise1); however:
  Version of libreoffice-core on system is 1:3.5.5~rc2-0ubuntu1~ppa1.
 libreoffice-calc depends on libreoffice-base-core (= 1:3.6.0~beta2-0ubuntu1~ppa3~precise1); however:
  Package libreoffice-base-core is not configured yet.
dpkg: error processing libreoffice-calc (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libreoffice-draw:
 libreoffice-draw depends on libreoffice-core (= 1:3.6.0~beta2-0ubuntu1~ppa3~precise1); however:
  Version of libreoffice-core on system is 1:3.5.5~rc2-0ubuntu1~ppa1.
dpkg: error processing libreoffice-draw (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libreoffice-impress:
 libreoffice-impress depends on libreoffice-core (= 1:3.6.0~beta2-0ubuntu1~ppa3~precise1); however:
  Version of libreoffice-core on system is 1:3.5.5~rc2-0ubuntu1~ppa1.
 libreoffice-impress depends on libreoffice-draw (= 1:3.6.0~beta2-0ubuntu1~ppa3~precise1); however:
  Package libreoffice-draw is not configured yet.
dpkg: error processing libreoffice-impress (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libreoffice-math:
 libreoffice-math depends on libreoffice-core (= 1:3.6.0~beta2-0ubuntu1~ppa3~precise1); however:
  Version of libreoffice-core on system is 1:3.5.5~rc2-0ubuntu1~ppa1.
dpkg: error processing libreoffice-math (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libreoffice-base:
 libreoffice-base depends on libreoffice-core (= 1:3.6.0~beta2-0ubuntu1~ppa3~precise1); however:
  Version of libreoffice-core on system is 1:3.5.5~rc2-0ubuntu1~ppa1.
 libreoffice-base depends on libreoffice-base-core (= 1:3.6.0~beta2-0ubuntu1~ppa3~precise1); however:
  Package libreoffice-base-core is not configured yet.
dpkg: error processing libreoffice-base (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libreoffice-report-builder-bin:
 libreoffice-report-builder-bin depends on libreoffice-core; however:
  Package libreoffice-core is not configured yet.
 libreoffice-report-builder-bin depends on libreoffice-base; however:
  Package libreoffice-base is not configured yet.
dpkg: error processing libreoffice-report-builder-bin (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libreoffice:
 libreoffice depends on libreoffice-core (= 1:3.6.0~beta2-0ubuntu1~ppa3~precise1); however:
  Version of libreoffice-core on system is 1:3.5.5~rc2-0ubuntu1~ppa1.
 libreoffice depends on libreoffice-writer; however:
  Package libreoffice-writer is not configured yet.
 libreoffice depends on libreoffice-calc; however:
  Package libreoffice-calc is not configured yet.
 libreoffice depends on libreoffice-impress; however:
  Package libreoffice-impress is not configured yet.
 libreoffice depends on libreoffice-draw; however:
  Package libreoffice-draw is not configured yet.
 libreoffice depends on libreoffice-math; however:
  Package libreoffice-math is not configured yet.
 libreoffice depends on libreoffice-base; however:
  Package libreoffice-base is not configured yet.
 libreoffice depends on libreoffice-report-builder-bin; however:
  Package libreoffice-report-builder-bin is not configured yet.
dpkg: error processing libreoffice (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libreoffice-gtk:
 libreoffice-gtk depends on libreoffice-core (= 1:3.6.0~beta2-0ubuntu1~ppa3~precise1); however:
  Version of libreoffice-core on system is 1:3.5.5~rc2-0ubuntu1~ppa1.
dpkg: error processing libreoffice-gtk (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libreoffice-gnome:
 libreoffice-gnome depends on libreoffice-core (= 1:3.6.0~beta2-0ubuntu1~ppa3~precise1); however:
  Version of libreoffice-core on system is 1:3.5.5~rc2-0ubuntu1~ppa1.
 libreoffice-gnome depends on libreoffice-gtk; however:
  Package libreoffice-gtk is not configured yet.
dpkg: error processing libreoffice-gnome (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libreoffice-help-en-us:
 libreoffice-help-en-us depends on libreoffice-writer | language-support-translations-en; however:
  Package libreoffice-writer is not configured yet.
  Package language-support-translations-en is not installed.
dpkg: error processing libreoffice-help-en-us (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of python-uno:
 python-uno depends on libreoffice-core (= 1:3.6.0~beta2-0ubuntu1~ppa3~precise1); however:
  Version of libreoffice-core on system is 1:3.5.5~rc2-0ubuntu1~ppa1.
dpkg: error processing python-uno (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 libreoffice-core
 libreoffice-base-core
 libreoffice-writer
 libreoffice-calc
 libreoffice-draw
 libreoffice-impress
 libreoffice-math
 libreoffice-base
 libreoffice-report-builder-bin
 libreoffice
 libreoffice-gtk
 libreoffice-gnome
 libreoffice-help-en-us
 python-uno
E: Sub-process /usr/bin/dpkg returned an error code (1)


If I then try **sudo apt-get autoremove**, I get a recommendation to try (**-f install**). Round and round I go.

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libreoffice : Depends: libreoffice-core (= 1:3.6.0~beta2-0ubuntu1~ppa3~precise1) but 1:3.5.5~rc2-0ubuntu1~ppa1 is installed
 libreoffice-base : Depends: libreoffice-core (= 1:3.6.0~beta2-0ubuntu1~ppa3~precise1) but 1:3.5.5~rc2-0ubuntu1~ppa1 is installed
 libreoffice-base-core : Depends: libreoffice-core (= 1:3.6.0~beta2-0ubuntu1~ppa3~precise1) but 1:3.5.5~rc2-0ubuntu1~ppa1 is installed
 libreoffice-calc : Depends: libreoffice-core (= 1:3.6.0~beta2-0ubuntu1~ppa3~precise1) but 1:3.5.5~rc2-0ubuntu1~ppa1 is installed
 libreoffice-common : Breaks: libreoffice-core (< 1:3.6~) but 1:3.5.5~rc2-0ubuntu1~ppa1 is installed
 libreoffice-draw : Depends: libreoffice-core (= 1:3.6.0~beta2-0ubuntu1~ppa3~precise1) but 1:3.5.5~rc2-0ubuntu1~ppa1 is installed
 libreoffice-gnome : Depends: libreoffice-core (= 1:3.6.0~beta2-0ubuntu1~ppa3~precise1) but 1:3.5.5~rc2-0ubuntu1~ppa1 is installed
 libreoffice-gtk : Depends: libreoffice-core (= 1:3.6.0~beta2-0ubuntu1~ppa3~precise1) but 1:3.5.5~rc2-0ubuntu1~ppa1 is installed
 libreoffice-impress : Depends: libreoffice-core (= 1:3.6.0~beta2-0ubuntu1~ppa3~precise1) but 1:3.5.5~rc2-0ubuntu1~ppa1 is installed
 libreoffice-math : Depends: libreoffice-core (= 1:3.6.0~beta2-0ubuntu1~ppa3~precise1) but 1:3.5.5~rc2-0ubuntu1~ppa1 is installed
 libreoffice-writer : Depends: libreoffice-core (= 1:3.6.0~beta2-0ubuntu1~ppa3~precise1) but 1:3.5.5~rc2-0ubuntu1~ppa1 is installed
 python-uno : Depends: libreoffice-core (= 1:3.6.0~beta2-0ubuntu1~ppa3~precise1) but 1:3.5.5~rc2-0ubuntu1~ppa1 is installed
E: Unmet dependencies. Try using -f.


Did I jump the gun? Or is there a way out of this?

---

### Post by neu5eeCh on 2012-06-29
Ah! Got it. Yes, it really was **that** simple.

I downloaded libreoffice-core_3.6.0~beta2-0ubuntu1~ppa3~precise1_i386.deb from here:

[https://launchpad.net/~bjoern-michaelsen/+archive/libreoffice-quantaltest-20120601/+build/3612170/+files/libreoffice-core_3.6.0%7Ebeta2-0ubuntu1%7Eppa3%7Eprecise1_i386.deb](https://launchpad.net/~bjoern-michaelsen/+archive/libreoffice-quantaltest-20120601/+build/3612170/+files/libreoffice-core_3.6.0%7Ebeta2-0ubuntu1%7Eppa3%7Eprecise1_i386.deb)

sudo dpkg -i libreoffice*.deb, and all is well. I now get a word-count in the status bar. Whatever pain this Beta causes me, the word-count is _worth it_ by gad!:popcorn:

---

