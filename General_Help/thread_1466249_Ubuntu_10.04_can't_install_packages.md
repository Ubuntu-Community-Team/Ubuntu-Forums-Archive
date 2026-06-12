---
title: "Ubuntu 10.04 can't install packages"
date: 2010-04-30
forum: General Help
---

### Post by Vannak on 2010-04-30
So I can't install packages and I found this out when trying to run the new Gwibber deal, and upon failing trying to run DotA through wine to feel better about it. Anyways, deal is that apparently, "The Package System Is Broken", or so says Ubuntu Software center upon trying to install, uninstall, or modify any program. It suggests running apt-get install -f, which I do. I get this out:
```

mike@VKbot:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libfreebob0 libavahi-qt3-1 kdelibs4c2a libxml++2.6-2 libgda-4.0-common
  nspluginwrapper libdmraid1.0.0.rc15 libdmraid1.0.0.rc16 libgda-4.0-4
  python-alsaaudio liblualib50 libass3 python-gda python-gdl python2.5 libawn0
  kpartx sdparm libx264-67 python-gksu2 libgdl-1-common libcelt0
  openoffice.org-hyphenation-en-us libgoffice-0-8-common python-sqlalchemy
  libffado1 kdebase-workspace-libs4+5 python-eggtrayicon libksignalplotter4
  libdb4.6 libqt3-mt liblsofui4 dmraid kdelibs-data liblua50
  openoffice.org-thesaurus-en-au sqlite3 python-xlib libopenjpeg2
  openoffice.org-thesaurus-en-us openoffice.org-hyphenation libgdl-1-3
  libboo2.0-cil libawn-extras0 python-numeric libfaad0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  wine1.2
The following NEW packages will be installed:
  wine1.2
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B/9,648kB of archives.
After this operation, 81.6MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
dpkg: regarding .../wine1.2_1.1.42-0ubuntu4_amd64.deb containing wine1.2:
 wine1.2 conflicts with wine (<< 1.2)
  wine (version 1.1.42-0ubuntu4) is present and unpacked but not configured.
dpkg: error processing /var/cache/apt/archives/wine1.2_1.1.42-0ubuntu4_amd64.deb (--unpack):
 conflicting packages - not installing wine1.2
Errors were encountered while processing:
 /var/cache/apt/archives/wine1.2_1.1.42-0ubuntu4_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```So I can neither uninstall wine nor update it, and I am kind of stuck here. Anyone have any advice?

---

### Post by P4man on 2010-04-30
you could try synaptic package manager in system > adminstration
Then click edit > fix broken packages

---

### Post by double_tap on 2010-05-06
> **P4man said:**
> you could try synaptic package manager in system > adminstration
Then click edit > fix broken packages

This worked for me.  Thanks!

---

### Post by cbecker78 on 2010-05-06
edit: oops... it thought the op had reported success... I see now that's not the case, so i deleted my comment on how to mark thread as solved. Sorry!

):P

---

