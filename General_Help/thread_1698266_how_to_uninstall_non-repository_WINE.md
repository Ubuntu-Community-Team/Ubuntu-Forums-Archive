---
title: "how to uninstall non-repository WINE?"
date: 2011-03-02
forum: General Help
---

### Post by yuler on 2011-03-02
Currently, WINE stable is v1.22.  Several months ago, I installed WINE 1.01 from the command line while following a forgotten instruction online.  It does not show up in Ubuntu Software Center, so it did not update through the repositories.   I've since [added WINE to the repositories]("http://www.winehq.org/download/deb"), but when I try to install v1.22, the installer finds v1.01, says it could be a problem, but only allows "cancel" and "install anyway" as options.

How do uninstall the old (v1.01) WINE from Ubuntu?
Is it as easy as deleting the .wine folder from my home folder?
How do I remove WINE from the Application menu?

---

### Post by vivek.pandey on 2011-03-02
try to find the package in synaptic and can uninstall from there
else sudo apt-get purge winev
here v is your wine version

---

### Post by gandaran on 2011-03-02
> **yuler said:**
> Currently, WINE stable is v1.22.  Several months ago, I installed WINE 1.01 from the command line while following a forgotten instruction online.  It does not show up in Ubuntu Software Center, so it did not update through the repositories.   I've since [added WINE to the repositories]("http://www.winehq.org/download/deb"), but when I try to install v1.22, the installer finds v1.01, says it could be a problem, but only allows "cancel" and "install anyway" as options.

How do uninstall the old (v1.01) WINE from Ubuntu?
Is it as easy as deleting the .wine folder from my home folder?
How do I remove WINE from the Application menu?
that depends on what package you used to install wine, if it was a .deb package then you can find it in synaptic package manager and uninstall from there, if it was something else then maybe you need a uninstall script to run, some packages include a uninstall script, you just have to look for it in the installed 'app' system folders.
deleting only the user .wine folder and the applications menu launcher doesn't remove wine completely, you will have to delete every wine installed folder/file in root file system if you cant find another way to remove wine.

---

### Post by ankspo71 on 2011-03-02
> **yuler said:**
> 
How do uninstall the old (v1.01) WINE from Ubuntu?
Is it as easy as deleting the .wine folder from my home folder?
How do I remove WINE from the Application menu?
Hi,
I don't recommend deleting the wine entries from the start menu because those wine entries will not come back as easily when you install wine again. Try uninstalling wine or wine1.0 with Synaptic Package Manager. If you are using Ubuntu 10.10 (maverick), wine 1.2.2 is also in the repositories (from maverick updates repo). It is called wine1.2 . Search for that in Synaptic Package Manager then install it.

Note: If you are using Ubuntu 10.04 (Lucid), wine1.2 is not wine 1.2.2, it is version 1.1.42 :confused:

Hope this helps.

---

### Post by yuler on 2011-03-04
Thanks, everyone.  The old WINE was checked off in the Synaptic database, so I unchecked it and selected the latest (1.22?).  I was surprised to see two versions of WINE in the list.

---

