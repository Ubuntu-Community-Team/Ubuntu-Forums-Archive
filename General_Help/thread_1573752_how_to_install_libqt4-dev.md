---
title: "how to install libqt4-dev"
date: 2010-09-13
forum: General Help
---

### Post by ari197 on 2010-09-13
I need to install libqt4-dev from the ppa-beta repositories, but everytime I try to do apt-get install libqt4-dev the system gave me these errors :


  libqt4-dev: Depends: libqt4-dbus (= 4:4.6.2-0ubuntu5) but 4:4.7.0~beta2-0ubuntu1~lucid1~ppa1 is to be installed
              Depends: libqt4-qt3support (= 4:4.6.2-0ubuntu5) but 4:4.7.0~beta2-0ubuntu1~lucid1~ppa1 is to be installed
              Depends: libqt4-xml (= 4:4.6.2-0ubuntu5) but 4:4.7.0~beta2-0ubuntu1~lucid1~ppa1 is to be installed
              Depends: libqtcore4 (= 4:4.6.2-0ubuntu5) but 4:4.7.0~beta2-0ubuntu1~lucid1~ppa1 is to be installed
              Depends: libqtgui4 (= 4:4.6.2-0ubuntu5) but 4:4.7.0~beta2-0ubuntu1~lucid1~ppa1 is to be installed
              Depends: libqt4-network (= 4:4.6.2-0ubuntu5) but 4:4.7.0~beta2-0ubuntu1~lucid1~ppa1 is to be installed
              Depends: libqt4-svg (= 4:4.6.2-0ubuntu5) but 4:4.7.0~beta2-0ubuntu1~lucid1~ppa1 is to be installed
              Depends: libqt4-webkit (= 4:4.6.2-0ubuntu5) but 4:4.7.0~beta1+git20100706-0ubuntu1~lucid1~ppa1 is to be installed
              Depends: libqt4-sql (= 4:4.6.2-0ubuntu5) but 4:4.7.0~beta2-0ubuntu1~lucid1~ppa1 is to be installed
              Depends: libqt4-script (= 4:4.6.2-0ubuntu5) but 4:4.7.0~beta2-0ubuntu1~lucid1~ppa1 is to be installed
              Depends: libqt4-scripttools (= 4:4.6.2-0ubuntu5) but 4:4.7.0~beta2-0ubuntu1~lucid1~ppa1 is to be installed
              Depends: libqt4-xmlpatterns (= 4:4.6.2-0ubuntu5) but 4:4.7.0~beta2-0ubuntu1~lucid1~ppa1 is to be installed
              Depends: libqt4-designer (= 4:4.6.2-0ubuntu5) but 4:4.7.0~beta2-0ubuntu1~lucid1~ppa1 is to be installed
              Depends: libqt4-help (= 4:4.6.2-0ubuntu5) but 4:4.7.0~beta2-0ubuntu1~lucid1~ppa1 is to be installed
              Depends: libqt4-assistant (= 4:4.6.2-0ubuntu5) but it is not going to be installed
              Depends: libqt4-test (= 4:4.6.2-0ubuntu5) but 4:4.7.0~beta2-0ubuntu1~lucid1~ppa1 is to be installed
              Depends: libqt4-multimedia (= 4:4.6.2-0ubuntu5) but it is not going to be installed
              Depends: qt4-qmake (= 4:4.6.2-0ubuntu5) but 4:4.6.3-0ubuntu1 is to be installed
              Recommends: libqt4-opengl-dev (= 4:4.6.2-0ubuntu5) but it is not going to be installed

I already have the ppa repo on the source.list;

root@athena:~# cat /etc/apt/sources.list | grep ppa
deb [http://ppa.launchpad.net/kubuntu-ppa/beta/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/beta/ubuntu) lucid main multiverse universe restricted

It would seems that the system is trying to install the package from the standard repo not the ppa-beta one.

any ideas how to fix this? Or can I just download the .deb file for the package so that I could install it manually?

---

### Post by yeats on 2010-09-13
Assuming you added the PPA repo correctly and have already done an ```
sudo apt-get update
``` before trying to install, you might try ```
sudo apt-get -f install
```, which will attempt to fix the situation automatically.  This is the beauty of APT's architecture - it knows which packages you need to keep a stable system running and will not let you break it (without really trying).  I would not recommend installing the .deb directly, especially since it will almost certainly give you the same error.

You can find out which versions of a package the system can install by doing ```
apt-cache policy *packagename*
```.  Doing so for each of these dependencies may help you understand your problem better.

---

### Post by ari197 on 2010-09-13
> **ari197 said:**
> 

It would seems that the system is trying to install the package from the standard repo not the ppa-beta one.



hmm it would seems the kubuntu ppa-beta repo has a problem .. when I browse manually to the repo site, I could only see packages from amarok ..

---

### Post by mc4man on 2010-09-13
Maybe they're no longer 'beta'
see here (click on 'view package details' - expand qt4-x11, all are rc
[https://launchpad.net/~kubuntu-ppa/+archive/backports/+packages](https://launchpad.net/~kubuntu-ppa/+archive/backports/+packages)

---

### Post by ari197 on 2010-09-13
> **mc4man said:**
> Maybe they're no longer 'beta'
see here (click on 'view package details' - expand qt4-x11, all are rc
[https://launchpad.net/~kubuntu-ppa/+archive/backports/+packages](https://launchpad.net/~kubuntu-ppa/+archive/backports/+packages)

:D

got it .. upgrading now :)

thanks a lot

---

