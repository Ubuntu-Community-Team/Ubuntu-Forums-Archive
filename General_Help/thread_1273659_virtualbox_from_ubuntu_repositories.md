---
title: "virtualbox from ubuntu repositories?"
date: 2009-09-23
forum: General Help
---

### Post by rplantz on 2009-09-23
The HowTos for installing virtualbox say to get a .deb file from [www.virtualbox.org](www.virtualbox.org). The karmic repositories (I'm running alpha) have the latest version of virtualbox, 3.06. Is there any advantage to getting it from virtualbox.org?

If I install from the karmic repositories, are the following packages a good selection to start with (y=yes, n=no)?

n -- virtualbox-guest-additions
y -- virtualbox-ose
n -- virtualbox-ose-dbg
n -- virtualbox-ose-guest-source
n -- virtualbox-ose-guest-utils
y -- virtualbox-ose-guest-x11
n -- virtualbox-ose-guest-qt
n -- virtualbox-ose-source

My goal is to be able to install OpenSolaris and FreeBSD for occasional use. I currently have OpenSolaris on another disk as dual boot, but several people have pointed out that virtualbox would be an easier way to play with other systems.

---

### Post by Chronon on 2009-09-23
The feature set tends to lag behind a bit in the OSE version (no USB support, etc.).  It depends on what you need to do with the virtual machine.  If you won't use any features that distinguish them then go ahead and use the OSE version.

---

