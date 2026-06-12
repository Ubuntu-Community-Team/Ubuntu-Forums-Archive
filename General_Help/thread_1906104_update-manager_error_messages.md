---
title: "update-manager error messages"
date: 2012-01-08
forum: General Help
---

### Post by Oldhacker on 2012-01-08
The last few days, my update-manager has been telling me that I have updates, but it spews out a page of error messages:

installArchives() failed: Selecting previously deselected package libsigsegv2.
(Reading database ... 
(Reading database ... 5%%
(Reading database ... 10%%
(Reading database ... 15%%
(Reading database ... 20%%
(Reading database ... 25%%
(Reading database ... 30%%
(Reading database ... 35%%
(Reading database ... 40%%
(Reading database ... 45%%
(Reading database ... 50%%
(Reading database ... 55%%
(Reading database ... 60%%
(Reading database ... 65%%
(Reading database ... 70%%
(Reading database ... 75%%
(Reading database ... 80%%
(Reading database ... 85%%
(Reading database ... 90%%
(Reading database ... 95%%
(Reading database ... 100%%
(Reading database ... 241208 files and directories currently installed.)
Unpacking libsigsegv2 (from .../libsigsegv2_2.9-4ubuntu2_amd64.deb) ...
Setting up libsigsegv2 (2.9-4ubuntu2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Selecting previously deselected package gawk.
(Reading database ... 
(Reading database ... 5%%
(Reading database ... 10%%
(Reading database ... 15%%
(Reading database ... 20%%
(Reading database ... 25%%
(Reading database ... 30%%
(Reading database ... 35%%
(Reading database ... 40%%
(Reading database ... 45%%
(Reading database ... 50%%
(Reading database ... 55%%
(Reading database ... 60%%
(Reading database ... 65%%
(Reading database ... 70%%
(Reading database ... 75%%
(Reading database ... 80%%
(Reading database ... 85%%
(Reading database ... 90%%
(Reading database ... 95%%
(Reading database ... 100%%
(Reading database ... 241216 files and directories currently installed.)
Unpacking gawk (from .../gawk_1%%3a3.1.8+dfsg-0.1build1_amd64.deb) ...
Selecting previously deselected package boot-sav.
Unpacking boot-sav (from .../boot-sav_3.04-0ppa2~oneiric_all.deb) ...
Selecting previously deselected package boot-sav-gui.
Unpacking boot-sav-gui (from .../boot-sav-gui_3.04-0ppa6~oneiric_all.deb) ...
dpkg: error processing /var/cache/apt/archives/boot-sav-gui_3.04-0ppa6~oneiric_all.deb (--unpack):
 trying to overwrite '/usr/share/locale/hi/LC_MESSAGES/cleancommon-translations.mo', which is also in package clean-gui 3.02-0ppa33~oneiric
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Preparing to replace boot-repair 3.02-0ppa23~oneiric (using .../boot-repair_3.04-0ppa3~oneiric_all.deb) ...
Unpacking replacement boot-repair ...
Preparing to replace clean-gui 3.02-0ppa33~oneiric (using .../clean-gui_3.04-0ppa1~oneiric_all.deb) ...
Unpacking replacement clean-gui ...
Selecting previously deselected package gtk2-engines-pixbuf.
Unpacking gtk2-engines-pixbuf (from .../gtk2-engines-pixbuf_2.24.6-0ubuntu5_amd64.deb) ...
Selecting previously deselected package mbr.
Unpacking mbr (from .../mbr_1.1.11-4_amd64.deb) ...
Selecting previously deselected package python-configobj.
Unpacking python-configobj (from .../python-configobj_4.7.2+ds-3_all.deb) ...
Selecting previously deselected package pastebinit.
Unpacking pastebinit (from .../pastebinit_1.2-2_all.deb) ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for hicolor-icon-theme ...
Processing triggers for doc-base ...
Processing 1 added doc-base file...
Registering documents with scrollkeeper...
Errors were encountered while processing:
 /var/cache/apt/archives/boot-sav-gui_3.04-0ppa6~oneiric_all.deb
Error in function: 
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1)
Setting up python-configobj (4.7.2+ds-3) ...
Setting up mbr (1.1.11-4) ...
Setting up gawk (1:3.1.8+dfsg-0.1build1) ...
Setting up boot-sav (3.04-0ppa2~oneiric) ...
Setting up gtk2-engines-pixbuf (2.24.6-0ubuntu5) ...
dpkg: dependency problems prevent configuration of boot-repair:
 boot-repair depends on boot-sav-gui; however:
  Package boot-sav-gui is not installed.
dpkg: error processing boot-repair (--configure):
 dependency problems - leaving unconfigured
Setting up clean-gui (3.04-0ppa1~oneiric) ...
Setting up pastebinit (1.2-2) ...
Errors were encountered while processing:
 boot-repair

What is causing this, and what do I do to get rid of it and return to normal operation?

---

### Post by kublaykan on 2012-01-09
HI, I have the same problem here. All was Ok in my last Update, but from few days ago I can t update.

Please help us

---

### Post by uligraf on 2012-01-10
Hi,

same problem here in the first update just after a new install. Please help!

---

### Post by jerrrys on 2012-01-10
I think you should post in a YannUbuntu thread.

[http://ubuntuforums.org/showthread.php?t=1831869](http://ubuntuforums.org/showthread.php?t=1831869)

also have a look

[https://bugs.launchpad.net/~yannubuntu/+affectingbugs?direction=backwards&start=225](https://bugs.launchpad.net/~yannubuntu/+affectingbugs?direction=backwards&start=225)

---

