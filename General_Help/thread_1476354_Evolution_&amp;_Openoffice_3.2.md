---
title: "Evolution &amp; Openoffice 3.2"
date: 2010-05-07
forum: General Help
---

### Post by mschraier on 2010-05-07
I was looking through Synaptic and noticed an openoffice with evolution.  i installed it.  i didnt realize that it would remove my OOO 3.2.  SO I removed it and reinstalled OOO.  When I tired to do the desktop-integration this is what i got:

marty@marty-laptop:~/Downloads/OOO320_m12_native_packed-1_en-US.9483/DEBS/desktop-integration$ sudo dpkg -i *.deb
dpkg: regarding openoffice.org3.2-debian-menus_3.2-9472_all.deb containing openoffice.org-debian-menus:
 openoffice.org-debian-menus conflicts with openoffice.org-bundled
  openoffice.org-core provides openoffice.org-bundled and is present and installed.
dpkg: error processing openoffice.org3.2-debian-menus_3.2-9472_all.deb (--install):
 conflicting packages - not installing openoffice.org-debian-menus
Errors were encountered while processing:
 openoffice.org3.2-debian-menus_3.2-9472_all.deb
marty@marty-laptop:~/Downloads/OOO320_m12_native_packed-1_en-US.9483/DEBS/desktop-integration$

how can i fix this so i can get my OOO menu reinstated?

---

### Post by Hagar Delest on 2010-05-08
The Ubuntu and the Sun versions are not compatible. So you've to remove all the OOo packages coming from the Ubuntu repositories. Use Synaptic and remove all the OOo packages with the 'ubuntu' string in the version number.

---

