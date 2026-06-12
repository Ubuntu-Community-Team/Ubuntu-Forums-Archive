---
title: "I think I messed up the updates"
date: 2009-10-04
forum: General Help
---

### Post by Mr. Hibba on 2009-10-04
Hi all, 

While trying to update my system's software with the normal package manager, it got stuck trying to install, so I ended up force-quitting the installer. Maybe that wasn't such a good idea, though, because now I have some broken packages. I've bee instructed to use dpkg --configure -a (with sudo) and apt-get -f install (also with sudo). Neither of which worked, after a variety of tries. What else can I do now? 

Here is a list of what shows up in the terminal: 
sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of openoffice.org-gnome:
 openoffice.org-gnome depends on openoffice.org-core (= 1:3.0.1-9ubuntu3.1); however:
  Version of openoffice.org-core on system is 1:3.0.1-9ubuntu3.
dpkg: error processing openoffice.org-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-impress:
 openoffice.org-impress depends on openoffice.org-core (= 1:3.0.1-9ubuntu3.1); however:
  Version of openoffice.org-core on system is 1:3.0.1-9ubuntu3.
dpkg: error processing openoffice.org-impress (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-math:
 openoffice.org-math depends on openoffice.org-core (= 1:3.0.1-9ubuntu3.1); however:
  Version of openoffice.org-core on system is 1:3.0.1-9ubuntu3.
dpkg: error processing openoffice.org-math (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-draw:
 openoffice.org-draw depends on openoffice.org-core (= 1:3.0.1-9ubuntu3.1); however:
  Version of openoffice.org-core on system is 1:3.0.1-9ubuntu3.
dpkg: error processing openoffice.org-draw (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-gtk:
 openoffice.org-gtk depends on openoffice.org-core (= 1:3.0.1-9ubuntu3.1); however:
  Version of openoffice.org-core on system is 1:3.0.1-9ubuntu3.
dpkg: error processing openoffice.org-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-base-core:
 openoffice.org-base-core depends on openoffice.org-core (= 1:3.0.1-9ubuntu3.1); however:
  Version of openoffice.org-core on system is 1:3.0.1-9ubuntu3.
dpkg: error processing openoffice.org-base-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-kde:
 openoffice.org-kde depends on openoffice.org-core (= 1:3.0.1-9ubuntu3.1); however:
  Version of openoffice.org-core on system is 1:3.0.1-9ubuntu3.
dpkg: error processing openoffice.org-kde (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-writer:
 openoffice.org-writer depends on openoffice.org-core (= 1:3.0.1-9ubuntu3.1); however:
  Version of openoffice.org-core on system is 1:3.0.1-9ubuntu3.
 openoffice.org-writer depends on openoffice.org-base-core (= 1:3.0.1-9ubuntu3.1); however:
  Package openoffice.org-base-core is not configured yet.
dpkg: error processing openoffice.org-writer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-uno:
 python-uno depends on openoffice.org-core (= 1:3.0.1-9ubuntu3.1); however:
  Version of openoffice.org-core on system is 1:3.0.1-9ubuntu3.
dpkg: error processing python-uno (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 openoffice.org-gnome
 openoffice.org-impress
 openoffice.org-math
 openoffice.org-draw
 openoffice.org-gtk
 openoffice.org-base-core
 openoffice.org-kde
 openoffice.org-writer
 python-uno

Thanks in advance. :-)

Hibba.

---

### Post by oboedad55 on 2009-10-04
In Synaptic you can go, on the left, to custom filters, and pick "broken" and see what's up that way.

---

### Post by Mr. Hibba on 2009-10-04
> **oboedad55 said:**
> In Synaptic you can go, on the left, to custom filters, and pick "broken" and see what's up that way.

Thanks, I was able to remove the broken packages and redownload them... now I'm only having a few issue where it would get stuck during the install with "Adding extension /usr/lib/openoffice/basis3.0/program/mailmerge.py..." and "Adding extension /usr/lib/openoffice/share/extension/install/writer2latex.uno.pkg..." . Maybe I'll have to try removing and redownloading them and see if that helps.

---

### Post by oboedad55 on 2009-10-04
> **Mr. Hibba said:**
> Thanks, I was able to remove the broken packages and redownload them... now I'm only having a few issue where it would get stuck during the install with "Adding extension /usr/lib/openoffice/basis3.0/program/mailmerge.py..." and "Adding extension /usr/lib/openoffice/share/extension/install/writer2latex.uno.pkg..." . Maybe I'll have to try removing and redownloading them and see if that helps.

If you're thinking of just removing those files I don't believe I'd do that. You can try reinstalling openoffice but beyond that I have no other ideas. Perhaps someone else will chime in.

---

