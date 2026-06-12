---
title: "i cant install updates from synaptic."
date: 2010-02-05
forum: General Help
---

### Post by SpatzST on 2010-02-05
I havent updated in awhile and i think theres like 120 updates or something i download, after they download it says running dpkg and then this is the first thing that pops up

reading database 20%dpkg: unrecoverable fatal error. aborting.

it also says somewhere "files list for package "wine1.2" I/O error

package failed to install
------------------------

i'd copy paste the whole thing but i dont know how :D

so any ideas? just to clarify, nothing installs, as soon as this happens it stops and makes me restart the install process, but then fails again so.

---

### Post by MelDJ on 2010-02-05
in terminal try typing: 
```
sudo dpkg --configure -a
```

---

### Post by SpatzST on 2010-02-05
Ok so i entered that into the terminal and tried again, same problem.
i restarted and tried again, same problem.

I had a friend whos familiar with linux help me, and he tried to manually uninstall Wine1.2 from the terminal, and it failed.

this is the terminal text:

sudo apt-get remove wine1.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libopenal1 libclucene0ldbl libqt4-opengl libxvidcore4
  kdebase-runtime-data-common mplayer-skins libsvga1 kdebase-runtime
  libqt4-sql-mysql kdelibs5 libqt4-qt3support mplayer
  kdemultimedia-kio-plugins libknotificationitem1 kde-icons-oxygen libexiv2-5
  mencoder libkcddb4 ttf-tahoma-replacement liblzma0 ttf-liberation
  libsoprano4 libqtscript4-core kdebase-runtime-bin-kde4 libqt4-webkit
  kdelibs5-data libqtscript4-gui libqt4-sql-sqlite libqtscript4-uitools
  ttf-mscorefonts-installer libqt4-sql libqt4-svg cabextract
  ttf-symbol-replacement libstreamanalyzer0 wine1.2-gecko libplasma3
  libqtscript4-sql phonon-backend-xine libqt4-designer kdelibs-bin
  libqtscript4-xml libqt4-phonon khelpcenter4 libmpg123-0 libstreams0 exiv2
  libtag-extras1 winbind liblastfm0 libqt4-script mplayer-nogui soprano-daemon
  kdebase-runtime-data libqtscript4-network libfaac0
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  wine1.2
0 upgraded, 0 newly installed, 1 to remove and 100 not upgraded.
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory
-----

so i dont know what to make of this, but we couldnt uninstall Wine through synaptic (it would crash everytime we even highlighted it) and manually uninstalling doesnt work either.  i dont know what to do!!!

-chris

---

### Post by MelDJ on 2010-02-06
try the following: 
```
pkill apt
```

---

### Post by SpatzST on 2010-02-09
pkill: 2125 - Operation not permitted.

---

### Post by rnerwein on 2010-02-09
hi
you must be super user to run pkill for apt:
try: sudo pkill apt
ciao

---

