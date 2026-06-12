---
title: "Lots of incompletely installed packages messing up dpkg-repack"
date: 2012-06-07
forum: General Help
---

### Post by Stonecold1995 on 2012-06-07
I'm trying to move all my programs from one computer to another so I have to generate all the packages as .deb files, copy them to my new computer, and install them with "sudo dpkg -i *.deb".  I'm using the program dpkg-repack to do that.  However, every time it comes across an incompletely installed package it stops and I have to manually remove the offending package with "sudo apt-get purge badpackage".  Although this works, I have to restart dpkg-repack all over again, and then it works for a few hours until it hits ANOTHER incompletely installed package.

```
dpkg-deb: building package `libcairo-perl' in `./libcairo-perl_1.081-1build2_amd64.deb'.
dpkg-deb: warning: './dpkg-repack-32491/DEBIAN/control' contains user-defined field 'Original-Maintainer'
dpkg-deb: warning: ignoring 1 warning about the control file(s)

dpkg-deb: building package `libcairo-script-interpreter2' in `./libcairo-script-interpreter2_1.10.2-6.1ubuntu3_amd64.deb'.
dpkg-deb: warning: './dpkg-repack-32491/DEBIAN/control' contains user-defined field 'Original-Maintainer'
dpkg-deb: warning: ignoring 1 warning about the control file(s)

dpkg-deb: building package `libcairo2' in `./libcairo2_1.10.2-6.1ubuntu3_amd64.deb'.
dpkg-repack: Fatal Error: Package libcairo2:i386 not fully installed

alex@kubuntu:~/dpkg-repack$ sudo apt-get purge libcairo2:i386
[sudo] password for alex: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libcairo2:i386*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? 
(Reading database ... 455910 files and directories currently installed.)
Removing libcairo2:i386 ...
Purging configuration files for libcairo2:i386 ...
alex@kubuntu:~/dpkg-repack$ fakeroot -u dpkg-repack `dpkg --get-selections | grep install | cut -f1`

dpkg-deb: warning: './dpkg-repack-32693/DEBIAN/control' contains user-defined field 'Original-Maintainer'
dpkg-deb: warning: ignoring 1 warning about the control file(s)

dpkg-deb: building package `accountsservice' in `./accountsservice_0.6.15-2ubuntu9_amd64.deb'.
dpkg-deb: warning: './dpkg-repack-32693/DEBIAN/control' contains user-defined field 'Original-Maintainer'
dpkg-deb: warning: ignoring 1 warning about the control file(s)

dpkg-deb: building package `acl' in `./acl_2.2.51-5ubuntu1_amd64.deb'.
dpkg-deb: warning: './dpkg-repack-32693/DEBIAN/control' contains user-defined field 'Original-Maintainer'
dpkg-deb: warning: ignoring 1 warning about the control file(s)
```

So dpkg-repack is going down alphabetically.  In the beginning of packages that start with "l" it came across an incomplete package (libcairo2:i386) with a size of 0 bytes.  I have to manually delete it, then start dpkg-repack again, but it starts with the "a" packages!  So then I have to wait hours for it to come across the NEXT broken package, etc.  So how do I speed this up?  Is there a command I could use to automatically remove packages with a size of 0?  I tried "sudo apt-get autoremove" and "sudo apt-get -f install" but none of them worked (or even detected the half-installed packages).

---

### Post by gardengxc on 2013-01-14
Bump
Having the same problem.

---

### Post by tgalati4 on 2013-01-14
Although in theory you can do this, in practice it breaks things.  Some packages require configuration.  Depending on the machine, the configuration will change.  Simply moving deb packages over will not reconfigure packages properly.  Also package dependency becomes an issue.  Some packages need to be installed before others to satisfy dependency.  Simply moving a massive block of deb packages will cause problems.

Can't you just image the drive to another hard drive and plug it into the new system?  Then deal with the breakage one application at a time.

In the meantime, make a list of packages installed:

```
dpkg --get-selections > installed-software.txt
```

---

### Post by gardengxc on 2013-01-15
I'm assuming tgalai4 is gooing off [this]("http://ubuntuforums.org/showthread.php?t=819396") and is or was planning to use sudo dpkg -i *.deb. I know I am. 

Further I note your solution still includes uninstalled programs that were never quite removed.

Edit: actually have you used APTonCD tgalai4?

---

### Post by tgalati4 on 2013-01-15
My fault, I misread the OP.  This is not a package problem but an aptoncd parsing problem.  Is the source code to aptoncd available?  Has anyone looked at it to see why it behaves this way?  Has anyone filed a bug against aptoncd for this behavior?

My apologies if I confused you, because I was confused myself.

---

