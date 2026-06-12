---
title: "Problem installing brother printer"
date: 2011-01-25
forum: General Help
---

### Post by Skeleton1Man on 2011-01-25
After having my Brother MFC-235c hooked up to another computer I tried installing it on another machine which has Ubuntu 10.04

I have used Brothers website: [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn3.html#dpkg1](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn3.html#dpkg1)

I am having this problem.

skeleton@skeleton-desktop:~$ sudo dpkg -i --force-all --force-architecture mfc235clpr-1.0.1-1.i386.deb
dpkg: error processing mfc235clpr-1.0.1-1.i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 mfc235clpr-1.0.1-1.i386.deb

Would appreciate some help. Thanks

---

### Post by mikewhatever on 2011-01-25
Make sure the downloaded mfc235clpr-1.0.1-1.i386.deb file is in the home folder, or go to where it is with the cd command. For example, it it's on the desktop:

cd Desktop
sudo dpkg -i --force-all --force-architecture mfc235clpr-1.0.1-1.i386.deb

---

### Post by plucky on 2011-01-26
The drivers for your Brother printer is already packaged in Ubuntu.

See [Here](https://wiki.ubuntu.com/BrotherDriverPackaging)

Open Synaptic Package Manager and search for MFC-235c and it will find the "brother-cups-wrapper-extra" and brother-lpr-drivers-extra".Install both,although I think if you select the cupswrapper it will install both.

If you printer has a scanner,then you will still need to download the scanner files from the Brother website.

Good Luck

---

