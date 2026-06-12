---
title: "Some Doubts Abiut installation"
date: 2009-08-20
forum: General Help
---

### Post by sububtu on 2009-08-20
How can i install applications in ubuntu(with a single click),, like tat we installs apps in windows frm a setup file,which is the setup file tat used in ubuntu(if any), i saw some .deb , .dsc , .diff.gz, & tar.gz files, im littlebit confused with these extensios :(

---

### Post by SoftwareExplorer on 2009-08-20
Go to Application->Add/Remove and search for what you want. When you find it, check the checkbox by it and hit apply. Hope that helps.

---

### Post by coldReactive on 2009-08-20
**For The Extensions Listed**

DEB Files will install like Windows Apps in Ubuntu, but you must have the dependencies satisfied for it to work like that (it will tell you what dependencies must be satisfied or if another application conflicts with it.)

Anything else you have to manually make/run through terminal.

---

### Post by SoftwareExplorer on 2009-08-20
Ubuntu uses .debs by default, but you don't have to worry about that because the method I told you automatically downloads what needs to be downloaded.

---

### Post by utnubuuser on 2009-08-20
Install software from >>System>>Administration>>Synaptic Package Manager

.tar, tar.gz, tar.bz2 etc are source-code and unless you know what you're doing....

---

### Post by ptsubin on 2009-08-20
Installation of packages depends on the type of it. Usually .deb (Debian Binaries) packages are precompiled binaries, that you can install by double clicking on them. .tar.gz, .tar.bz2 files may be source codes they come with a configuration script and many things. hey can be installed by using 
./configure
make
make install commands. Some softwares comes as self extracting shell scripts, in that case you just needs to run then (like crossover office). Again some archives comes with an INSTALL.sh , that you just need to run. If you download firefox, flock etc, there is no need of installation, you can run the executable files directly. 
For security reasons it is always preferred that you install packages from the official repositories using a package management tool like apt. You can also use Add/Remove programs in the main menu, which would make software installation even easier than in windows. If you don't have a working internet connection, you can download the packages from elsewhere and can use AptonCD to make an apt compatible package CD image, that you can use to install packages on any number of systems.

---

### Post by sububtu on 2009-08-20
installing frm add/remove is pretty eazy!

but if  i want to dwnload particular application , and install it manually what will i do?
my previous attempt to do so ended up here -- [https://launchpad.net/~c-korn/+archive/vlc](https://launchpad.net/~c-korn/+archive/vlc)   
im confused to see those list of files , and dnt know which one to dwnld- mine - i386 architecture, 

**please help me Im a beginner!**

---

### Post by ptsubin on 2009-08-20
You got in to the page. Ok. If you are downloading the packages from another system runnin gon Ubuntu, then follow the instruction on the top of the page without blindly searching for a download link. vlc is having many dependancies and you need to download them all. Better you download it form packages.ubuntu.com and search under jaunty for vlc.

---

### Post by sububtu on 2009-08-20
YES!!!! it better Idea!, Thanks for the effort...:guitar:

---

