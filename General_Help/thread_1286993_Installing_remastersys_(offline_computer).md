---
title: "Installing remastersys (offline computer)"
date: 2009-10-09
forum: General Help
---

### Post by dv3500ea on 2009-10-09
As some friends have been impressed with what they have seen of Ubuntu on my laptop,  I would like to be able to give them a remastered version with lots of the software I use on it. I have heard of remastersys and this sounds like a perfect tool for my purpose. Tutorials, however have assumed an internet connection which I have not got. They say to paste ```
deb http://www.geekconnection.org/remastersys/repository ubuntu/
``` into software sources then install from synaptic but I can't do this without an internet connection. I use keryx package manager to download software but I can't find remastersys in it anywhere, even if I add ```
deb http://www.geekconnection.org/remastersys/repository ubuntu/
```to its sources list. I therefore have had to resort to downloading the .deb from the repository site. It has a string of unsatisfied dependencies which I have installed one by one as the deb installer only shows one of the missing dependencies. I have come stuck on the ubiquity dependency which I downloaded with no problems from keryx. Ubiquity won't install as there is a dependency of ubiquity-frontend which can't be found on keryx (although a similar ubiquity-frontend-gtk can but doesn't help). Can anyone help? A pointer to a .deb for ubiquity-frontend or a list of dependencies for remastersys would be useful.

---

### Post by EXCiD3 on 2009-10-09
Here are the dependencies for Remastersys:
> coreutils, dialog, mkisofs | genisoimage, findutils, grub, bash, passwd, sed, squashfs-tools, casper, rsync, mount, eject, libdebian-installer4, os-prober, ubiquity, user-setup, discover1 | discover, laptop-detect, syslinux, xterm, util-linux, xresprobe

You can go through keryx and download each of these dependencies. If you added it to the sources.list, make sure that you selected "yes" to download the latest lists as that is the only way keryx can know about the new package.

We're still working on keryx a lot and dependency calculation is a bit off at the moment, but improving considerably. Give us a bit of time and we will have it working 100% for you.

---

### Post by dv3500ea on 2009-10-09
Thanks alot! It has now installed without issues. I installed all the packages that you listed and every ubiquity related package i could find. Quite a few of these failed to install with ```
sudo dpkg -i *.deb
``` but after running ```
apt-get install -f
``` I could simply double click on the .deb file.

---

