---
title: "upgrading an installed package with a .deb file"
date: 2009-12-13
forum: General Help
---

### Post by afselby1 on 2009-12-13
i am migrating from fedora - this is about using dpkg
The rpm package manager supports an "upgrade", from a downloaded package file:
  
 rpm {-U|--upgrade} [-options] PACKAGE_FILE ...
     upgrades  the package currently installed to a newer version

how do I upgrade with a downloaded .deb file?

thnx

---

### Post by 3Miro on 2009-12-13
If you click on the file, what do you get. Do you get options install/upgrade or what?

---

### Post by afselby1 on 2009-12-13
3Miro,
as i said, i have a fedora background - and I am a command line user.

when you say "click on the file",  I assume you are using some GUI interface?

I  am trying to use "dpkg -??SOME_OPTION(s) DownLoadedPackage.deb"
which replies with something like "older version of DownLoadedPackage installed"

how do I upgrade from a downloaded .deb file?

thnx

---

### Post by Sin@Sin-Sacrifice on 2009-12-13
Just use the -i flag... it will replace the old files. You may be able to use ```
sudo apt-get upgrade
``` to get the same results though... unless it's a package not in the repositories.

---

### Post by afselby1 on 2009-12-14
12/14/2009 13:25EDT
Sin@Sin-Sacrifice
  The dpkg -i is the command that resulted in the error "NEWPACKAGE confliicts with INSTALLED"

I downloaded the .deb because it does not appear to be in a repository recognized by my
kubuntu

FYI, I just came across another post in this forum "[B]virtualbox not installing...." 
[/B]with the same problem.

how do I upgrade from a downloaded .deb file?

thnx
[FONT=Arial][B]
[/B][/FONT]

---

### Post by snowpine on 2009-12-14
Please follow the instructions on this page (under "Debian-Based Linux Distributions") to get the latest Virtualbox: 

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

You want to add the repository to your sources, so you'll automatically get updates and bug fixes.

(ps if you've already installed virtualbox-ose from the repositories, you'll want to uninstall that first)

---

