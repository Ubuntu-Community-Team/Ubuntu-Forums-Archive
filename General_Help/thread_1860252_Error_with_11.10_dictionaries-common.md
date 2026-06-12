---
title: "Error with 11.10 dictionaries-common"
date: 2011-10-14
forum: General Help
---

### Post by ikonitas on 2011-10-14
Hi,

I have just upgraded from 11.04 to 11.10 and I am having this issue with dictionaries-common, can somebody please help me on this one, as its really annoying as I cant install any packages ...


ed@ubu:~$ sudo dpkg --configure -a
Setting up dictionaries-common (1.11.5ubuntu1) ...
update-default-ispell: Question empty but elements installed for class "ispell"
  dictionaries-common/default-ispell: return code: "0", value: ""
  Choices: , Manual symlink setting
  shared/packages-ispell: return code: "10" owners/error: "shared/packages-ispell doesn't exist"
  Installed elements: american (American English)

  Please see "/usr/share/doc/dictionaries-common/README.problems", section
  "Debconf database corruption" for recovery info.

update-default-ispell: Selected ispell dictionary "" 
does not correspond to any installed package in the system
and no alternative ispell dictionary could be selected.
dpkg: error processing dictionaries-common (--configure):
 subprocess installed post-installation script returned error exit status 255
dpkg: dependency problems prevent configuration of myspell-en-za:
 myspell-en-za depends on dictionaries-common (>= 0.10) | openoffice.org-updatedicts; however:
  Package dictionaries-common is not configured yet.
  Package openoffice.org-updatedicts is not installed.
  Package dictionaries-common which provides openoffice.org-updatedicts is not configured yet.
dpkg: error processing myspell-en-za (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ienglish-common:
 ienglish-common depends on dictionaries-common (>= 1.10.6~); however:
  Package dictionaries-common is not configured yet.
dpkg: error processing ienglish-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of iamerican:
 iamerican depends on dictionaries-common; however:
  Package dictionaries-common is not configured yet.
 iamerican depends on ienglish-common (= 3.3.02-5); however:
  Package ienglish-common is not configured yet.
dpkg: error processing iamerican (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ispell:
 ispell depends on dictionaries-common; however:
  Package dictionaries-common is not configured yet.
dpkg: error processing ispell (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hunspell-en-ca:
 hunspell-en-ca depends on dictionaries-common (>= 0.10) | openoffice.org-updatedicts; however:
  Package dictionaries-common is not configured yet.
  Package openoffice.org-updatedicts is not installed.
  Package dictionaries-common which provides openoffice.org-updatedicts is not configured yet.
dpkg: error processing hunspell-en-ca (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of myspell-en-au:
 myspell-en-au depends on dictionaries-common (>= 1.0); however:
  Package dictionaries-common is not configured yet.
dpkg: error processing myspell-en-au (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of myspell-en-gb:
 myspell-en-gb depends on dictionaries-common (>= 0.10) | openoffice.org-updatedicts; however:
  Package dictionaries-common is not configured yet.
  Package openoffice.org-updatedicts is not installed.
  Package dictionaries-common which provides openoffice.org-updatedicts is not configured yet.
dpkg: error processing myspell-en-gb (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hunspell-en-us:
 hunspell-en-us depends on dictionaries-common (>= 0.10); however:
  Package dictionaries-common is not configured yet.
dpkg: error processing hunspell-en-us (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of aspell-en:
 aspell-en depends on dictionaries-common (>= 0.49.2); however:
  Package dictionaries-common is not configured yet.
dpkg: error processing aspell-en (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythes-en-us:
 mythes-en-us depends on dictionaries-common (>= 0.10) | openoffice.org-updatedicts; however:
  Package dictionaries-common is not configured yet.
  Package openoffice.org-updatedicts is not installed.
  Package dictionaries-common which provides openoffice.org-updatedicts is not configured yet.
dpkg: error processing mythes-en-us (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 dictionaries-common
 myspell-en-za
 ienglish-common
 iamerican
 ispell
 hunspell-en-ca
 myspell-en-au
 myspell-en-gb
 hunspell-en-us
 aspell-en
 mythes-en-us

---

### Post by awam66 on 2011-10-15
This is marked as solved but no explanation of the solution.
I have the same on a friend's machine. How did you fix it???

---

### Post by ChiaGod on 2011-10-15
Also curious as to how this was resolved.  Running into the same issue since upgrading to 11.10.  Haven't been able to succesfully boot into the gui since the 11.10 upgrade.

---

### Post by awam66 on 2011-10-16
I have asked the question on Installations and Upgrades as I thought I might get an answer there but no replies so far. Shouldn't really ask on two forums but as I didn't ask this one first the other forum is a more appropriate!

---

### Post by Nimlar on 2011-10-17
I just

```
sudo apt-get remove dictionaries-common
```
(it will remove this an the other language packages)

then reinstall them, not sure if I have all the spell checking packages, but system is updated. And no more apt-get errors.

---

