---
title: "gcc 3.4 on ubuntu 9.10"
date: 2009-11-08
forum: General Help
---

### Post by kuantum_fizax on 2009-11-08
I it possible to install gcc-3.4 on ubuntu 9.10? I think there used to be a gcc-3.4 package.

Specifically, I'm trying to install a CERN laboratory software kit called athena. It requires gcc-3.4. The installation instructions for ubuntu are posted on their wiki, but its for an earlier verison of ubuntu. When I try to add gcc-3.4 the way they say at:
[https://twiki.cern.ch/twiki/bin/view/Atlas/DistKitOnUbuntu#GCC_3_4_Setup]("https://twiki.cern.ch/twiki/bin/view/Atlas/DistKitOnUbuntu#GCC_3_4_Setup")

I get the following error:

sudo apt-get install gcc-3.4 g++-3.4    
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gcc-3.4

Thanks for any help or clarification. Is there a repository I need to add?

---

### Post by kuantum_fizax on 2009-11-18
No one knows how to get gcc 3.4?

---

### Post by Temposs on 2009-11-18
gcc 3.4 is not in the repositories in Karmic anymore, so you will not be able to get it like that. Probably the best way to get gcc 3.4 is to install it from Ubuntu's package archives:

[http://packages.ubuntu.com/jaunty/devel/](http://packages.ubuntu.com/jaunty/devel/)

There's the archive for Jaunty, which has gcc 3.4 in it. Then you click on gcc-3.4 to go here:

[http://packages.ubuntu.com/jaunty/devel/gcc-3.4](http://packages.ubuntu.com/jaunty/devel/gcc-3.4)

Then go down to "Download gcc-3.4" and click on your architecture. Then choose the mirror you want to download from, and the download should start. It's a deb, so you just run the file and it will try to install. Since gcc is a complex package, it has some dependencies, so it will tell you that it needs another package before it can install. You need to repeat these steps for every package you need to install, and eventually everything will install.

---

### Post by Zoot7 on 2009-11-18
Karmic by default comes with gcc 4.4.1.

---

### Post by kuantum_fizax on 2009-11-18
> **Temposs said:**
> gcc 3.4 is not in the repositories in Karmic anymore, so you will not be able to get it like that. Probably the best way to get gcc 3.4 is to install it from Ubuntu's package archives:

[http://packages.ubuntu.com/jaunty/devel/](http://packages.ubuntu.com/jaunty/devel/)

There's the archive for Jaunty, which has gcc 3.4 in it. Then you click on gcc-3.4 to go here:

[http://packages.ubuntu.com/jaunty/devel/gcc-3.4](http://packages.ubuntu.com/jaunty/devel/gcc-3.4)

Then go down to "Download gcc-3.4" and click on your architecture. Then choose the mirror you want to download from, and the download should start. It's a deb, so you just run the file and it will try to install. Since gcc is a complex package, it has some dependencies, so it will tell you that it needs another package before it can install. You need to repeat these steps for every package you need to install, and eventually everything will install.

Thanks,

I assume its a bad idea for me to add the jaunty repository in and install it that way? Would that screw up my ubuntu installation?

Also, should I uninstall gcc-4 first? Alternatively, is there any easy way to switch which is the default if both are installed? 

Thanks,
Caleb

---

### Post by olawlor on 2010-08-13
I just got gcc 3.4 to work on ubuntu 10.04 by downloading just three packages: [gcc-3.4-base]("http://packages.ubuntu.com/jaunty/amd64/gcc-3.4-base/download"), [cpp-3.4]("http://packages.ubuntu.com/jaunty/amd64/cpp-3.4/download"), and [gcc-3.4]("http://packages.ubuntu.com/jaunty/amd64/gcc-3.4/download").  (Links are for 64-bit versions; for 32-bit hopefully just grab [gcc-3.4-base]("http://packages.ubuntu.com/jaunty/i386/gcc-3.4-base/download"), [cpp-3.4]("http://packages.ubuntu.com/jaunty/i386/cpp-3.4/download"), and [gcc-3.4]("http://packages.ubuntu.com/jaunty/i386/gcc-3.4/download").) 

You can cleanly "dpkg -i" each package after it's downloaded.  You run the new compiler like "gcc-3.4 foo.c", or more typically "./configure CC=gcc-3.4", and it seems to work for me in compiling qemu-0.9.0. 

Your already installed compiler is still the default gcc, so the old and new compilers coexist side by side.  Nice!

---

### Post by imrankhan1984 on 2010-09-30
> **olawlor said:**
> I just got gcc 3.4 to work on ubuntu 10.04 by downloading just three packages: [gcc-3.4-base]("http://packages.ubuntu.com/jaunty/amd64/gcc-3.4-base/download"), [cpp-3.4]("http://packages.ubuntu.com/jaunty/amd64/cpp-3.4/download"), and [gcc-3.4]("http://packages.ubuntu.com/jaunty/amd64/gcc-3.4/download").  (Links are for 64-bit versions; for 32-bit hopefully just grab [gcc-3.4-base]("http://packages.ubuntu.com/jaunty/i386/gcc-3.4-base/download"), [cpp-3.4]("http://packages.ubuntu.com/jaunty/i386/cpp-3.4/download"), and [gcc-3.4]("http://packages.ubuntu.com/jaunty/i386/gcc-3.4/download").) 

You can cleanly "dpkg -i" each package after it's downloaded.  You run the new compiler like "gcc-3.4 foo.c", or more typically "./configure CC=gcc-3.4", and it seems to work for me in compiling qemu-0.9.0. 

Your already installed compiler is still the default gcc, so the old and new compilers coexist side by side.  Nice!


Hello,

I need to install g++-3.4 in my ubuntu 10.04. I installed gcc-3.4 using your instructions above but when I run ./configure I get the following error 

checking for gcc... gcc34
checking whether the C compiler works... no
configure: error: in `/home/imran/Documents/sumo-r5499':
configure: error: C compiler cannot create executables


I've spent past 4 hours looking for solution, but to no avail.

I even tried to manually install g++-3.4 from the same pages as gcc-3.4 but when I try to install they give weired errors about dependencies.

At the moment it seems that only possibility is to get rid of current gcc, g++ and everything and install previous versions manually, one by one.

---

### Post by mc4man on 2010-09-30
> At the moment it seems that only possibility is to get rid of current gcc, g++ and everything and install previous versions manually, one by one.
I think you'll find that to be a rather poor idea.
There's no reason you can't install g++ 3.4, just get it's deps that you can't meet and install. (probably all you need is the proper libstdc++5 and libstdc++5 dev packages.

(best sometimes to gather **all the outside packages**, put in a folder, cd to that folder and install as a group w/
sudo dpkg -i *.deb
Ex
On maverick needed gcc 3.3 - screen shows it and g++ installed

---

