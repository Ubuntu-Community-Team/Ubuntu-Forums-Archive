---
title: "package system broken"
date: 2012-01-18
forum: General Help
---

### Post by beo42 on 2012-01-18
Hi. Thank you all for the many many wiki-sites and posts in this forum. They helped me a lot since I'm happily using ubuntu.
I did something stupid :-) I added a debian sid-repository a while ago. Today, I installed some packages for development: 
```
sudo apt-get install libssl-dev libssh-dev libidn11-dev libpcre3-dev libgtk2.0-dev libmysqlclient-dev libpq-dev libsvn-dev firebird2.1-dev libncp-dev
```And now I'm having problems with the package system.
apt get update works (disabled all custom reps)
apt-get upgrade: 
```

jeanny% sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 cryptsetup : Depends: plymouth but it is not installed
 mountall : Depends: plymouth but it is not installed
 plymouth-drm : Depends: plymouth (= 0.8.3-20) but it is not installed
                Recommends: plymouth-themes-all but it is not installable
 plymouth-theme-ubuntu-text : Depends: plymouth but it is not installed
 plymouth-x11 : Depends: plymouth but it is not installed
E: Unmet dependencies. Try using -f.

```apt-get install -f:
```
jeanny% sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
 cryptsetup : Depends: plymouth but it is not installed
 mountall : Depends: plymouth but it is not installed
 plymouth-drm : Depends: plymouth (= 0.8.3-20) but it is not installed
                Recommends: plymouth-themes-all but it is not installable
 plymouth-theme-ubuntu-text : Depends: plymouth but it is not installed
 plymouth-x11 : Depends: plymouth but it is not installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

```apt-get install plymouth
```

jeanny% sudo apt-get install plymouth
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libpango1.0-0 : Breaks: plymouth (< 0.8.3-19) but 0.8.2-2ubuntu28 is to be installed
 plymouth-drm : Depends: plymouth (= 0.8.3-20) but 0.8.2-2ubuntu28 is to be installed
                Recommends: plymouth-themes-all but it is not installable
                Conflicts: plymouth (< 0.8.3-10) but 0.8.2-2ubuntu28 is to be installed
 plymouth-x11 : Conflicts: plymouth (< 0.8.3-10) but 0.8.2-2ubuntu28 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


```the update manager says:
```
The following packages have unmet dependencies:

cryptsetup: Depends: libdevmapper1.02.1 (>= 2:1.02.36) but 2:1.02.48-4ubuntu3 is installed
            Depends: upstart-job but it is a virtual package
            Depends: plymouth but it is not installed
mountall: Depends: plymouth but it is not installed
          Depends: coreutils (>= 7.1) but 8.5-1ubuntu6 is installed
          Depends: libudev0 (>= 151) but 173-0ubuntu4 is installed
plymouth-drm: Depends: libc6 (>= 2.3.6-6~) but 2.13-20ubuntu5 is installed
              Depends: libcairo2 (>= 1.2.4) but 1.10.2-6.2 is installed
              Depends: libdrm-intel1 (>= 2.4.9) but 2.4.26-1ubuntu1 is installed
              Depends: libdrm-nouveau1a (>= 2.4.23) but 2.4.26-1ubuntu1 is installed
              Depends: libdrm-radeon1 (>= 2.4.17) but 2.4.26-1ubuntu1 is installed
              Depends: libdrm2 (>= 2.4.3) but 2.4.26-1ubuntu1 is installed
              Depends: libglib2.0-0 (>= 2.12.0) but 2.30.0-0ubuntu4 is installed
              Depends: libpango1.0-0 (>= 1.14.0) but 1.29.4-2 is installed
              Depends: libpng12-0 (>= 1.2.13-4) but 1.2.46-3ubuntu1 is installed
              Depends: plymouth (= 0.8.3-20) but it is not installed
plymouth-theme-ubuntu-text: Depends: libc6 (>= 2.1.3) but 2.13-20ubuntu5 is installed
                            Depends: plymouth but it is not installed
plymouth-x11: Depends: libatk1.0-0 (>= 1.12.4) but 2.2.0-2 is installed
              Depends: libc6 (>= 2.3.6-6~) but 2.13-20ubuntu5 is installed
              Depends: libcairo2 (>= 1.2.4) but 1.10.2-6.2 is installed
              Depends: libfontconfig1 (>= 2.8.0) but 2.8.0-3ubuntu2 is installed
              Depends: libfreetype6 (>= 2.2.1) but 2.4.4-2ubuntu1.1 is installed
              Depends: libgdk-pixbuf2.0-0 (>= 2.22.0) but 2.24.0-2 is installed
              Depends: libglib2.0-0 (>= 2.16.0) but 2.30.0-0ubuntu4 is installed
              Depends: libgtk2.0-0 (>= 2.10.0) but 2.24.8-2 is installed
              Depends: libpango1.0-0 (>= 1.14.0) but 1.29.4-2 is installed
              Depends: plymouth but it is not installed
              Depends: plymouth-drm (= 0.8.3-20) but 0.8.3-20 is installed

```I removed the debian sid repository, tried apt-get -f again, but it didn't work out. If I try to reinstall one of the packages cryptsetup, mountall or plymouth-theme-ubuntu-text, the package manager wants to delete nearly half of the system, including vital stuff like gnome-shell, so I would sweat a bit if I'd have to try this out.
Same if i try to remove plymouth-drm or plymouth-x11. I can't reinstall these last two packages.
I use full disk encryption and when I start the machine, I don't get the usual screen for entering the password. I have to hit ALT + F7 to see a text-screen where I can enter the password. gnome 3 looks weird too, some icons are not shown, although I can click them and the program starts.
Do you have any idea what is going on and how I can fix this?  thanks in advance

release: ubuntu 11.10 32bit

---

### Post by cariboo on 2012-01-18
This may be a silly question, but did you run

```
 apt-get update
``` 

after removing the debian repository, and before running

```
apt-get install -f
```

---

### Post by beo42 on 2012-01-18
Yes, I did. Also switched from the us server to main. No difference.

---

### Post by beo42 on 2012-01-19
I was able to fix this (at 1 am or so, classic ;-) ) by just aptitude install the packages with the correct ubuntu-version:
```

sudo aptitude install libpango1.0-0=1.29.3+git20110916-0ubuntu1 plymouth-x11=0.8.2-2ubuntu28 libpango1.0-dev=1.29.3+git20110916-0ubuntu1 gir1.2-pango-1.0=1.29.3+git20110916-0ubuntu1

```
libpango broke plymouth, and without plymouth all hell breaks loose if I want some eye-candy.
After this command, aptitude removed one package (plymouth-drm which I wasn't able to find in any ubuntu rep), downgraded the selected, installed plymouth and updated a bunch of others. the password-screen for the disk encryption is still ugly but the rest is fine so I'm very happy.
Turns out that aptitude is my new hero, it is way more helpful than apt-get especially with broken packages.

---

