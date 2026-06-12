---
title: "Unable to install Google Chrome"
date: 2009-11-27
forum: General Help
---

### Post by Lockheed on 2009-11-27
I added it in sources but when I try to install from Synaptic or command line, I get this:

```
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  chromium-browser: Depends: libgtk2.0-0 (>= 2.18.0) but 2.16.1-0ubuntu2 is to be installed
                    Depends: libstdc++6 (>= 4.4.0) but 4.3.3-5ubuntu4 is to be installed
                    Depends: libxml2 (>= 2.7.4) but 2.6.32.dfsg-5ubuntu4.2 is to be installed
E: Broken packages

```

I tried running **apt-get build-dep chromium-browser** but apart from installing 50mb of useless crap, it did nothing to fix it.

---

### Post by aysiu on 2009-11-27
Can you post your /etc/apt/sources.list here?

---

### Post by Lockheed on 2009-11-27
```
# Salimane Adjao Moustapha's Ubuntu Jaunty Jackalope 9.04 Sources list
#
# Repository List based on standard Jaunty with many extra packages
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number):
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -
#
# If you have a gpg key URL use (replace URL with the key address):
#
# wget -q http://lut1n.ifrance.com/repo_key.asc -O- | sudo apt-key add -
#
# If you have a gpg key file use (replace FILE with the key file):
#
# sudo apt-key add FILE
# Ubuntu supported packages
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty main restricted multiverse universe
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted multiverse universe
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty-security main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu jaunty-proposed main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty main restricted multiverse universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted multiverse universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu jaunty-proposed main restricted universe multiverse
#Canonical Commercial Repository
deb http://archive.canonical.com/ubuntu jaunty partner
deb http://archive.canonical.com/ubuntu jaunty-backports partner
deb http://archive.canonical.com/ubuntu jaunty-updates partner
deb http://archive.canonical.com/ubuntu jaunty-security partner
deb http://archive.canonical.com/ubuntu jaunty-proposed partner
deb-src http://archive.canonical.com/ubuntu jaunty partner
deb-src http://archive.canonical.com/ubuntu jaunty-backports partner
deb-src http://archive.canonical.com/ubuntu jaunty-updates partner
deb-src http://archive.canonical.com/ubuntu jaunty-security partner
deb-src http://archive.canonical.com/ubuntu jaunty-proposed partner
#gnome-globalmenu
deb http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu jaunty main
#opera
deb http://deb.opera.com/opera/ lenny non-free
#skype
deb http://download.skype.com/linux/repos/debian stable non-free
#firefox
deb http://ppa.launchpad.net/fta/ubuntu jaunty main
#gnome-do
deb http://ppa.launchpad.net/do-core/ubuntu jaunty main
#compiz-fusion
deb http://ppa.launchpad.net/compiz/ubuntu jaunty main
#google
deb http://dl.google.com/linux/deb/ stable non-free
#medibuntu
deb http://packages.medibuntu.org/ jaunty free non-free
# MySQL Workbench
deb ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/ binary/
deb-src ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/ source/
# Ubuntu tweak
deb http://ppa.launchpad.net/tualatrix/ubuntu jaunty main
deb-src http://ppa.launchpad.net/tualatrix/ubuntu jaunty main
##Themes du ZgegBlog: Project Bisigi
deb http://ppa.launchpad.net/bisigi/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/bisigi/ppa/ubuntu jaunty main

deb http://ppa.launchpad.net/awn-testing/ubuntu jaunty main
deb-src http://ppa.launchpad.net/awn-testing/ubuntu jaunty main
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty-proposed restricted main multiverse universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty-proposed restricted main multiverse universe
deb http://getswiftfox.com/builds/debian unstable non-free

deb http://download.virtualbox.org/virtualbox/debian jaunty non-free
deb http://ppa.launchpad.net/amule-releases/ppa/ubuntu jaunty main
deb http://ppa.launchpad.net/themuso/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/themuso/ppa/ubuntu jaunty main
deb http://wine.budgetdedicated.com/apt jaunty main #WineHQ - Ubuntu 9.04 "Jaunty Jackalope"

deb http://cafelinux.org/Downloads/oz-os tinwoodman main
deb http://ppa.launchpad.net/exaile-devel/ubuntu jaunty main

deb http://repository.cairo-dock.org/ubuntu karmic cairo-dock # For Ubuntu 9.10

deb http://repository.cairo-dock.org/ubuntu jaunty cairo-dock # For Ubuntu 9.04

deb http://repository.cairo-dock.org/ubuntu intrepid cairo-dock # For Ubuntu 8.10

deb http://repository.cairo-dock.org/ubuntu hardy cairo-dock # For ubuntu 8.04

deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/chromium-daily/ppa/ubuntu jaunty main
deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/chromium-daily/ppa/ubuntu karmic main

deb http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates universe

```

---

### Post by aysiu on 2009-11-27
Your repositories list is a mess, with a mix of both Karmic and Jaunty sources. No wonder you're running into conflicts.

Which are you using--Karmic (Ubuntu 9.10) or Jaunty (Ubuntu 9.04)?

---

### Post by Lockheed on 2009-11-27
Jaunty 9.04 64bit

---

### Post by NoaHall on 2009-11-27
Then it should be -

```
# Salimane Adjao Moustapha's Ubuntu Jaunty Jackalope 9.04 Sources list
#
# Repository List based on standard Jaunty with many extra packages
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number):
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -
#
# If you have a gpg key URL use (replace URL with the key address):
#
# wget -q http://lut1n.ifrance.com/repo_key.asc -O- | sudo apt-key add -
#
# If you have a gpg key file use (replace FILE with the key file):
#
# sudo apt-key add FILE
# Ubuntu supported packages
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty main restricted multiverse universe
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted multiverse universe
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty-security main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu jaunty-proposed main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty main restricted multiverse universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted multiverse universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu jaunty-proposed main restricted universe multiverse
#Canonical Commercial Repository
deb http://archive.canonical.com/ubuntu jaunty partner
deb http://archive.canonical.com/ubuntu jaunty-backports partner
deb http://archive.canonical.com/ubuntu jaunty-updates partner
deb http://archive.canonical.com/ubuntu jaunty-security partner
deb http://archive.canonical.com/ubuntu jaunty-proposed partner
deb-src http://archive.canonical.com/ubuntu jaunty partner
deb-src http://archive.canonical.com/ubuntu jaunty-backports partner
deb-src http://archive.canonical.com/ubuntu jaunty-updates partner
deb-src http://archive.canonical.com/ubuntu jaunty-security partner
deb-src http://archive.canonical.com/ubuntu jaunty-proposed partner
#gnome-globalmenu
deb http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu jaunty main
#opera
deb http://deb.opera.com/opera/ lenny non-free
#skype
deb http://download.skype.com/linux/repos/debian stable non-free
#firefox
deb http://ppa.launchpad.net/fta/ubuntu jaunty main
#gnome-do
deb http://ppa.launchpad.net/do-core/ubuntu jaunty main
#compiz-fusion
deb http://ppa.launchpad.net/compiz/ubuntu jaunty main
#google
deb http://dl.google.com/linux/deb/ stable non-free
#medibuntu
deb http://packages.medibuntu.org/ jaunty free non-free
# MySQL Workbench
deb ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/ binary/
deb-src ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/ source/
# Ubuntu tweak
deb http://ppa.launchpad.net/tualatrix/ubuntu jaunty main
deb-src http://ppa.launchpad.net/tualatrix/ubuntu jaunty main
##Themes du ZgegBlog: Project Bisigi
deb http://ppa.launchpad.net/bisigi/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/bisigi/ppa/ubuntu jaunty main

deb http://ppa.launchpad.net/awn-testing/ubuntu jaunty main
deb-src http://ppa.launchpad.net/awn-testing/ubuntu jaunty main
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty-proposed restricted main multiverse universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty-proposed restricted main multiverse universe
deb http://getswiftfox.com/builds/debian unstable non-free

deb http://download.virtualbox.org/virtualbox/debian jaunty non-free
deb http://ppa.launchpad.net/amule-releases/ppa/ubuntu jaunty main
deb http://ppa.launchpad.net/themuso/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/themuso/ppa/ubuntu jaunty main
deb http://wine.budgetdedicated.com/apt jaunty main #WineHQ - Ubuntu 9.04 "Jaunty Jackalope"

#deb http://cafelinux.org/Downloads/oz-os tinwoodman main?? tinwood? 
deb http://ppa.launchpad.net/exaile-devel/ubuntu jaunty main

deb http://repository.cairo-dock.org/ubuntu jaunty cairo-dock # For Ubuntu 9.04


deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/chromium-daily/ppa/ubuntu jaunty main

deb http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates universe
```

---

### Post by Lockheed on 2009-11-27
It worked. Thanks.

---

### Post by rajhanschinmay on 2009-12-17
I have same problem.
my OS is Karmic 9.10 32/64bit.
I have one PC with 32 bit and other with 64 bit. So please tell me solution for both in case it is different.






> **Lockheed said:**
> I added it in sources but when I try to install from Synaptic or command line, I get this:

```
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  chromium-browser: Depends: libgtk2.0-0 (>= 2.18.0) but 2.16.1-0ubuntu2 is to be installed
                    Depends: libstdc++6 (>= 4.4.0) but 4.3.3-5ubuntu4 is to be installed
                    Depends: libxml2 (>= 2.7.4) but 2.6.32.dfsg-5ubuntu4.2 is to be installed
E: Broken packages

```

I tried running **apt-get build-dep chromium-browser** but apart from installing 50mb of useless crap, it did nothing to fix it.

---

