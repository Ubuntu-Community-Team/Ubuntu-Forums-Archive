---
title: "vlc 1.1 unmet dependancies"
date: 2010-07-08
forum: General Help
---

### Post by blur xc on 2010-07-08
I installed hte ppa for vlc1.1 a bit ago, and after a recent update it's now broken.  Apparently vlc-nox is missing, along w/ a few other dependancies.  apt-get -f install doesn't fix it either.

What's my best bet?  Do a ppa purge on the vlc 1.1 repository and go back ot the old version?

Terminal junk-
```
sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  vlc vlc-nox
Suggested packages:
  videolan-doc
The following packages will be upgraded:
  vlc vlc-nox
2 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
85 not fully installed or removed.
Need to get 0B/5,178kB of archives.
After this operation, 217kB of additional disk space will be used.
Do you want to continue [Y/n]? 
(Reading database ... 126688 files and directories currently installed.)
Preparing to replace vlc 1.1.0-1~ppa1 (using .../vlc_1.1.0-2~ppa1_amd64.deb) ...
Unpacking replacement vlc ...
dpkg: error processing /var/cache/apt/archives/vlc_1.1.0-2~ppa1_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/vlc/plugins/misc/libxdg_screensaver_plugin.so', which is also in package vlc-nox 0:1.1.0-1~ppa1
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Preparing to replace vlc-nox 1.1.0-1~ppa1 (using .../vlc-nox_1.1.0-2~ppa1_amd64.deb) ...
Unpacking replacement vlc-nox ...
dpkg: error processing /var/cache/apt/archives/vlc-nox_1.1.0-2~ppa1_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/vlc/lua/extensions/allocine-fr.luac', which is also in package vlc 0:1.1.0-1~ppa1
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for man-db ...
Processing triggers for python-support ...
Errors were encountered while processing:
 /var/cache/apt/archives/vlc_1.1.0-2~ppa1_amd64.deb
 /var/cache/apt/archives/vlc-nox_1.1.0-2~ppa1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
Thanks,
BM

---

### Post by mikewhatever on 2010-07-08
It looks like you are installing the 64bit version of vlc over the 32bit version. Is that the intention? Do you have a 64bit operating system?

---

### Post by blur xc on 2010-07-08
Running 64bit 10.04 both at home and at work in VBox, and have the same problem at home and here at work.  If I install directly from the repsoitories, shouldn't it be pulling the right files for my 64 bit system automatically?

Thanks,
BM

---

### Post by mikewhatever on 2010-07-08
It should, and it does pull the correct 64 bit version. There seems to be a problem with installing the new packages, but vlc-nox is clearly not missing.

---

### Post by Leihca on 2010-07-10
Had the same problem, solved it by removing vlc completely and reinstalling it. (didn't change any of the ppa sources)

Seems it has problems upgrading from 1.1.0-1~ppa1 to 1.1.0-2~ppa1.

---

### Post by blur xc on 2010-07-12
> **Leihca said:**
> Had the same problem, solved it by removing vlc completely and reinstalling it. (didn't change any of the ppa sources)

Seems it has problems upgrading from 1.1.0-1~ppa1 to 1.1.0-2~ppa1.

Yeah- thanks, I thinks this worked for me as well.

BM

---

### Post by FrancoNero on 2010-07-17
jep that did it. nice

---

