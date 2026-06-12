---
title: "trouble using apt-rdepends"
date: 2010-07-22
forum: General Help
---

### Post by NotALamer on 2010-07-22
I've been trying to use apt-rdepends to find all the dependencies and sub-dependencies and whatnot for ubuntu-standard and ubuntu-minimal but I'm having some issues. By default it doesn't follow Recommends, but when I give it --follow=Depends,PreDepends,Recommends it doesn't appear to be recursive any more. Am I doing something wrong, or is it broken? Here's the output I get:

```
apt-rdepends --follow=Depends,PreDepends,Recommends ubuntu-standard
Reading package lists... Done
Building dependency tree
Reading state information... Done
ubuntu-standard
  Depends: aptitude
  Depends: at
  Depends: busybox-static
  Depends: cpio
  Depends: cron
  Depends: dmidecode
  Depends: dnsutils
  Depends: dosfstools
  Depends: ed
  Depends: file
  Depends: ftp
  Depends: hdparm
  Depends: info
  Depends: iptables
  Depends: language-selector-common
  Depends: logrotate
  Depends: lshw
  Depends: lsof
  Depends: ltrace
  Depends: man-db
  Depends: memtest86+
  Depends: mime-support
  Depends: parted
  Depends: pciutils
  Depends: popularity-contest
  Depends: psmisc
  Depends: rsync
  Depends: strace
  Depends: time
  Depends: usbutils
  Depends: wget
```

---

