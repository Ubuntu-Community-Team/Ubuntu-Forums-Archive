---
title: "Is it wrong to clean ubuntu this way? by remove all these libraries/dependencies?"
date: 2010-07-16
forum: General Help
---

### Post by dioxholster on 2010-07-16
I installed a KDE software that installed with it 74 objects, so i logged what got installed. after using the KDE thing i realised it was useless and i didnt like the fact that the OS now is part ubuntu and part kubuntu, like a freak show. so i opened synaptic, first removed the KDE software, but i realised that it doesnt uninstall all its 74 dependenices with it only 4 of them. thats mainly because these dependencies got dependencies of their own and so on. its rather complex. so i just searched for each file in synaptic and marked it for complete removal. btw, synaptic or other only listed 4 orphaned dependencies, but since i installed it and logged what was installed automatically, i knew there was more that needed removing. all this happened in mere hours so i didnt do any changes to the system, after installation.

here is the list i deleted:

 

> 
Completely removed the following packages:
akonadi-server
exiv2
gdebi-kde
hal
hal-info
icoutils
install-package
kdebase-runtime
kdebase-runtime-data
kdelibs-bin
kdelibs5
kdelibs5-data
kdepim-runtime
kdepimlibs-data
kdepimlibs5
kdesudo
kpackagekit
kubuntu-debug-installer
libakonadiprivate1
libattica0
libboost-program-options1.40.0
libclucene0ldbl
libdbusmenu-qt2
libexiv2-6
libiodbc2
libmysqlclient16
libpackagekit-glib2-12
libpackagekit-qt-12
libplasma3
libpolkit-qt-1-0
libqca2
libqt4-assistant
libqt4-help
libqt4-opengl
libqt4-qt3support
libqt4-scripttools
libqt4-sql
libqt4-sql-mysql
libqt4-svg
libqt4-test
libsoprano4
libssh-4
libstreamanalyzer0
libstreams0
libxcb-shape0
libxcb-shm0
libxcb-xv0
libxine1
libxine1-bin
libxine1-console
libxine1-misc-plugins
libxine1-x
mysql-client-core-5.1
mysql-common
mysql-server-core-5.1
oxygen-icon-theme
packagekit
packagekit-backend-apt
phonon
phonon-backend-xine
plasma-scriptengine-javascript
polkit-kde-1
python-kde4
python-packagekit
python-qt4
python-sip
shared-desktop-ontologies
smartdimmer
software-properties-kde
soprano-daemon
ttf-dejavu
ttf-dejavu-extra
update-manager-kde
virtuoso-nepomuk


----

74 objects all removed now. what worries me is whether they are needed by the OS or if they integrated themselves to the OS in such a way that it will cause problems if removed.

---

### Post by SnickerSnack on 2010-07-16
The proper way to remove the things that were installed only because they were required by something that you now want to remove is:

```
sudo apt-get purge [program]
```

This will uninstall the program and *everything that it alone needed*.

Now that you've done it manually, but want to ensure that it's done cleanly, you could reinstall the program and then purge it.

What you did is probably fine, but in the future, the purge command is faster and easier.

---

### Post by techunit on 2010-07-16
> **SnickerSnack said:**
> The proper way to remove the things that were installed only because they were required by something that you now want to remove is:

```
sudo apt-get purge [program]
```This will uninstall the program and *everything that it alone needed*.

Now that you've done it manually, but want to ensure that it's done cleanly, you could reinstall the program and then purge it.

What you did is probably fine, but in the future, the purge command is faster and easier.

Actually he needs to reinstall the KDE portion so he can get all of it. I would try what he recomended but you might have to reinstall the packages you deleted first. Then use the code

```
sudo apt-get purge [program]
```

---

### Post by dioxholster on 2010-07-16
i tried this first "sudo apt-get purge [program]" but without pressing Y so i can see what it was removing. and it was only removing 4 files along with the KDE software (Kjots) a very small portion of what was installed along with the Kjots. so that why i did what i did. i dont understand though how will reinstalling all that help? i will just end up removing them again the same way. "sudo apt-get purge" [program] does not take care of all 74 files installed. 

im new to linux so i find it difficult to analyse the OS to see if its functioning properly. in windows, all its files are important for the most part but here its like a sandbox of stuff.

---

### Post by marshmallow1304 on 2010-07-16
```
sudo apt-get --purge autoremove
```

will remove orphaned dependencies.

---

### Post by dioxholster on 2010-07-16
> **marshmallow1304 said:**
> ```
sudo apt-get --purge autoremove
```

will remove orphaned dependencies.

in my case it only wanted to remove these:


> kdepim-runtime 
linux-headers-2.6.32-21 
mysql-client-core-5.1 
mysql-server-core-5.1 
linux-headers-2.6.32-21-generic
akonadi-server

---

