---
title: "Libreoffice/openoffice"
date: 2011-07-23
forum: General Help
---

### Post by LegacyOpaque on 2011-07-23
can anyone help? i Was attempting to install Openoffice on my system and i think at some point i messed something up while removing the Libreoffice. I no longer can access the Ubuntu software store as it says my package catalog needs to be repaired, when attempting to repair i get the following errors 

Reading database ... 139924 files and directories currently installed.) 
Unpacking libreoffice-common (from .../libreoffice-common_1%3a3.3.2-1ubuntu5_all.deb) ... 
dpkg: error processing /var/cache/apt/archives/libreoffice-common_1%3a3.3.2-1ubuntu5_all.deb (--unpack): 
 trying to overwrite '/usr/share/mime/packages/openoffice.org.xml', which is also in package openoffice.org-debian-menus 3.3-9556 
No apport report written because MaxReports is reached already
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)

and

rrors were encountered while processing: 
 /var/cache/apt/archives/libreoffice-common_1%3a3.3.2-1ubuntu5_all.deb 
dpkg: dependency problems prevent configuration of libreoffice-java-common: 
 libreoffice-java-common depends on libreoffice-common; however: 
  Package libreoffice-common is not installed. 
dpkg: error processing libreoffice-java-common (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libreoffice-filter-mobiledev: 
 libreoffice-filter-mobiledev depends on libreoffice-java-common; however: 
  Package libreoffice-java-common is not configured yet. 
dpkg: error processing libreoffice-filter-mobiledev (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libreoffice-base: 
 libreoffice-base depends on libreoffice-java-common (>= 1:3.3.2~); however: 
  Package libreoffice-java-common is not configured yet. 
dpkg: error processing libreoffice-base (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libreoffice-report-builder-bin: 
 libreoffice-report-builder-bin depends on libreoffice-base; however: 
  Package libreoffice-base is not configured yet. 
dpkg: error processing libreoffice-report-builder-bin (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libreoffice-core: 
 libreoffice-core depends on libreoffice-common (>> 1:3.3.2); however: 
  Package libreoffice-common is not installed. 
dpkg: error processing libreoffice-core (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libreoffice-style-human: 
 libreoffice-style-human depends on libreoffice-core; however: 
  Package libreoffice-core is not configured yet. 
dpkg: error processing libreoffice-style-human (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libreoffice-math: 
 libreoffice-math depends on libreoffice-core (= 1:3.3.2-1ubuntu5); however: 
  Package libreoffice-core is not configured yet. 
dpkg: error processing libreoffice-math (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libreoffice-impress: 
 libreoffice-impress depends on libreoffice-core (= 1:3.3.2-1ubuntu5); however: 
  Package libreoffice-core is not configured yet. 
dpkg: error processing libreoffice-impress (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libreoffice: 
 libreoffice depends on libreoffice-core (= 1:3.3.2-1ubuntu5); however: 
  Package libreoffice-core is not configured yet. 
 libreoffice depends on libreoffice-impress; however: 
  Package libreoffice-impress is not configured yet. 
 libreoffice depends on libreoffice-math; however: 
  Package libreoffice-math is not configured yet. 
 libreoffice depends on libreoffice-base; however: 
  Package libreoffice-base is not configured yet. 
 libreoffice depends on libreoffice-report-builder-bin; however: 
  Package libreoffice-report-builder-bin is not configured yet. 
 libreoffice depends on libreoffice-filter-mobiledev; however: 
  Package libreoffice-filter-mobiledev is not configured yet. 
 libreoffice depends on libreoffice-java-common (>= 1:3.3.2~); however: 
  Package libreoffice-java-common is not configured yet. 
dpkg: error processing libreoffice (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libreoffice-writer: 
 libreoffice-writer depends on libreoffice-core (= 1:3.3.2-1ubuntu5); however: 
  Package libreoffice-core is not configured yet. 
dpkg: error processing libreoffice-writer (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libreoffice-base-core: 
 libreoffice-base-core depends on libreoffice-core (= 1:3.3.2-1ubuntu5); however: 
  Package libreoffice-core is not configured yet. 
dpkg: error processing libreoffice-base-core (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libreoffice-emailmerge: 
 libreoffice-emailmerge depends on libreoffice-core; however: 
  Package libreoffice-core is not configured yet. 
dpkg: error processing libreoffice-emailmerge (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of python-uno: 
 python-uno depends on libreoffice-core (= 1:3.3.2-1ubuntu5); however: 
  Package libreoffice-core is not configured yet. 
dpkg: error processing python-uno (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libreoffice-draw: 
 libreoffice-draw depends on libreoffice-core (= 1:3.3.2-1ubuntu5); however: 
  Package libreoffice-core is not configured yet. 
dpkg: error processing libreoffice-draw (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libreoffice-calc: 
 libreoffice-calc depends on libreoffice-core (= 1:3.3.2-1ubuntu5); however: 
  Package libreoffice-core is not configured yet. 
 libreoffice-calc depends on libreoffice-base-core (= 1:3.3.2-1ubuntu5); however: 
  Package libreoffice-base-core is not configured yet. 
dpkg: error processing libreoffice-calc (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of openoffice.org: 
 openoffice.org depends on libreoffice; however: 
  Package libreoffice is not configured yet. 
dpkg: error processing openoffice.org (--configure): 
 dependency problems - leaving unconfigured 

Pretend like im fairly New to all this and thanks to anyone who can help!

---

### Post by Hagar Delest on 2011-07-25
Try to run Synaptic and see if you can repair it.

Then for OOo and LibO, better use the vanilla version IMHO: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68) This process applies to both.

---

