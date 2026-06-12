---
title: "Ubuntu"
date: 2006-06-01
forum: General Help
---

### Post by Meads on 2006-06-01
When installed does it have GCC, CPP, MAKE etc pre configured unlike Xubuntu which i recently installed and tried installing gcc, g++, cpp and make yet i only managed to get make installed out of those due to it giving me mas amount error due to dependancies etc so i have given up.

I want to install ubuntu but only if i dont have to go through what i did with xubuntu :)

---

### Post by bruce89 on 2006-06-01
No, they are not included by default.

---

### Post by ubuntu_demon on 2006-06-01
$sudo apt-get install build-essential

Will install things like make which everybody needs when compiling.

$apt-cache show cpp 

gives :

```

The GNU C preprocessor (cpp)
 The GNU C preprocessor is a macro processor that is used automatically
 by the GNU C compiler to transform programs before actual compilation.
 .
 This package has been separated from gcc for the benefit of those who
 require the preprocessor but not the compiler.
 .
 This is a dependency package providing the default GNU C preprocessor.

```

if you need that too just :

$sudo apt-get install cpp

---

### Post by aysiu on 2006-06-01
I believe if you use the alternate installer CD (not the desktop CD), then the *build-essential* package is on the CD, even though it doesn't get installed during installation.

---

### Post by StonePiano on 2006-06-01
[QUOTE=Meads]When installed does it have GCC, CPP, MAKE etc pre configured unlike Xubuntu which i recently installed and tried installing gcc, g++, cpp and make yet i only managed to get make installed out of those due to it giving me mas amount error due to dependancies etc so i have given up.

I want to install ubuntu but only if i dont have to go through what i did with xubuntu :)[/QUOTE]

I used the Synaptic Package Manager to install compilers (and everything else I installed for that matter).  So installing the above files was as easy as ticking the options in a list.

The Synaptic Package Manager takes care of dependencies and keeps your system very clean.

In my opinion, if you never install any software other than using the SPM, then you can save yourself a lot of trouble.

Of course, some people enjoy messing around with manual installations, and sometimes you may find you have no choice.  Nevertheless, my recommendation is to always check the SPM repositories first, and keep manual installations to a minimum.

StonePiano

---

### Post by Meads on 2006-06-01
I need to be able to intall these package without an internet connection as i need them to run a script to get my modem working ...

When i try intalling the packages from this list: [http://packages.ubuntu.com/breezy/devel/build-essential](http://packages.ubuntu.com/breezy/devel/build-essential) it goes on about gcc-4.0 not being installed... Even when running trying the gcc package?

Anyone have any ideas ive been at this 2 days and im just getting error after error. If someone could list each and every package i need to install (correct full name) that would be great.. speedtouchconf.sourceforge.net is what i need these packages for (make & gcc

---

### Post by aysiu on 2006-06-01
Do you have the alternate installer CD or the desktop CD? If you have the alternate installer CD, you can install *build-essential* off that CD--no internet connection required. Just pop the CD in your drive and ```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential
```

Otherwise, [this](http://www.ubuntuforums.org/showpost.php?p=913191&postcount=12) should help you.

---

### Post by Meads on 2006-06-01
Thank, i downloaded those files well mot of them i cant find some.

gcc_4%3a4.0.1-3_i386.deb
g++_4%3a4.0.1-3_i385.deb

Were can i get these?

---

### Post by aysiu on 2006-06-01
[gcc_4%3a4.0.1-3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-defaults/gcc_4.0.1-3_i386.deb)
[g++_4%3a4.0.1-3_i385.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-defaults/g++_4.0.1-3_i386.deb)

By the way, the link I referred you to before was for Breezy, and I just realized you're posting in the Dapper section. I don't know if that'll make a difference. I guess once you get your internet connection, you can get more up-to-date versions of those packages.

---

### Post by Meads on 2006-06-01
Errors were encountered while processing:
 libc6-dev
 build-essential

I got that error after running the sudo -i *.deb command, but the script i needed to use to install my modem worked fine, i am now posting from within Xubuntu :)

---

### Post by aysiu on 2006-06-01
It's probably because you're Breezy .debs with a Dapper installation.

You can download the Dapper .debs from [http://packages.ubuntu.com](http://packages.ubuntu.com)

---

### Post by az on 2006-06-01
[QUOTE=aysiu]I believe if you use the alternate installer CD (not the desktop CD), then the *build-essential* package is on the CD, even though it doesn't get installed during installation.[/QUOTE]
It is on both the Desktop cd and the alternate cd.

If you installed using the Desktop cd, reboot into your new system and insert the cd again (after you are at the desktop)  A window will pop up asking if you want to add the packages on the cd to your repos.  Say yes, and you shall be able to install build-essential, the linux headers and a bunch of other packages that you may need to compile stuff to get online.  There is a small repo on that cd (added there about ten days ago) that you can not access from the live session.

If you installed using the old alternate cd, the packages are already part of synaptic, just install them using it.

---

### Post by garyng on 2006-06-01
apt-get build-dep <package you want>

this would pull in all the necessary stuff to build the given package which can ease the build process a lot, even if you want to build from upstream source instead of debian package

---

