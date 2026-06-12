---
title: "Unmet Dependencies"
date: 2011-12-20
forum: General Help
---

### Post by loele on 2011-12-20
Hi everyone,    (i'm new - forgive my mistakes)
[all new updates installed yesterday- didn't notice problem until now]
I just did a clean install from cd of 11.10 and it worked fine for a few days until just now when I tried to revert back to the traditional gnome menu and I got this message. 

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 chromium-browser-l10n : Depends: chromium-browser (= 15.0.874.106~r107270-0ubuntu0.11.10.1) but it is not going to be installed
 chromium-codecs-ffmpeg : Depends: chromium-browser (>= 4.0.203.0~) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
I remember trying to install chromium but some error came and I just forgot about it and continued with firefox. Searching around has led me to believe the source list is important in this case:

> # deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ oneiric main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
I've still not found how to deal with this after an hour or two of searching so I'd appreciate all the help I can get.

Thank you

---

### Post by wildmanne39 on 2011-12-20
Hi, try:
```
sudo apt-get -f install
```
Thanks

---

### Post by loele on 2011-12-21
thanks for your reply,
unfortunately it didn't work but resulted in this error:

> Do you want to continue [Y/n]? y
(Reading database ... 153593 files and directories currently installed.)
Unpacking chromium-browser (from .../chromium-browser_15.0.874.106~r107270-0ubuntu0.11.10.1_i386.deb) ...
xz: (stdin): Compressed data is corrupt
dpkg-deb: error: subprocess <decompress> returned error exit status 1
dpkg: error processing /var/cache/apt/archives/chromium-browser_15.0.874.106~r107270-0ubuntu0.11.10.1_i386.deb (--unpack):
 short read on buffer copy for backend dpkg-deb during `./usr/lib/chromium-browser/chromium-browser'
Errors were encountered while processing:
 /var/cache/apt/archives/chromium-browser_15.0.874.106~r107270-0ubuntu0.11.10.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

any idea what's up?  
thanks

---

### Post by loele on 2011-12-21
SOLVED!
I cleaned all the cache and the programs I desired to be installed were done so correctly.
Thanks

---

### Post by wildmanne39 on 2011-12-21
Hi, that is good, and that was the next step.
Enjoy

---

