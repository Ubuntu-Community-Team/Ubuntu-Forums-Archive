---
title: "Need help with an error.."
date: 2011-12-11
forum: General Help
---

### Post by zMeow on 2011-12-11
Sorry if this is the wrong section, or whatever..
Well, any time I try to install a program, I get an error. Normally I get a "Wrong architecture 'i386'" error when I try to install any .deb files. My computer is 32 bit, and whenever I try to install the 32 version of the file, I get that architecture error. If I try to install the 64 bit version, I get a "Dependency is not satisfiable: libkipi8 (>= 4:4.5.80)" error.
I am running Ubuntu 10.10, with Macbuntu installed.
This happens to any program I try to install, Teamviewer, Google Chrome, KSnapshot, anything. Anything that is already in Ubuntu Software Center, installs fine though such as aMSN, Skype, Filezilla, ect. This stuff was happening even before installing Macbuntu. I installed all updates, installed new drivers, restarted my PC many times, i've tried everything.
Screenshots below.

Trying to install Teamviewer 6 32bit:
[ATTACH]208975[/ATTACH]


Trying to install Google Chrome 32bit:
[ATTACH]208977[/ATTACH]

Trying to install KSnapshot 64bit:
[ATTACH]208976[/ATTACH]
-zMeow

---

### Post by oldos2er on 2011-12-12
Can you run ```
uname -a
``` in a terminal, and post the output here?

---

### Post by zMeow on 2011-12-12
> **oldos2er said:**
> Can you run ```
uname -a
``` in a terminal, and post the output here?
Here you go:
[img]http://img7.imagebanana.com/img/02za0c8k/Selection_001.png[/img]

---

### Post by RealityMaster on 2011-12-12
> **zMeow said:**
> Here you go:
[img]http://img7.imagebanana.com/img/02za0c8k/Selection_001.png[/img]

Your running a 64bit kernel.

TeamViewer rocks btw!)

---

### Post by zMeow on 2011-12-12
> **RealityMaster said:**
> Your running a 64bit kernel.

TeamViewer rocks btw!)
Well that would explain the errors, but why would I still get errors from trying the 64 bit version of these programs?

EDIT: Teamviewer 64bit version is working for me :D So I guess the problem is pretty much solved, except that other programs aren't working whether 64 bit or 32 bit :3 Thanks everybody for all the help :D

---

### Post by RealityMaster on 2011-12-12
For the 64 bit app I would try

```
apt-get update
apt-get upgrade
```

Then retry the install.

---

### Post by oldos2er on 2011-12-12
> **zMeow said:**
> Well that would explain the errors, but why would I still get errors from trying the 64 bit version of these programs?

EDIT: Teamviewer 64bit version is working for me :D So I guess the problem is pretty much solved, except that other programs aren't working whether 64 bit or 32 bit :3 Thanks everybody for all the help :D

You need to install ia32-libs to run 32-bit applications on a 64-bit system. Which version of Ubuntu did you install?

---

