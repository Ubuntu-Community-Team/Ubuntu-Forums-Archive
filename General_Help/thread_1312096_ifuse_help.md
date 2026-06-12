---
title: "ifuse help"
date: 2009-11-02
forum: General Help
---

### Post by mjfuenza on 2009-11-02
I am trying to moaunt my ipod touch 3.1 using iFuse but i am having trouble with the installation step "sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com F0876AC9 " where I get the following output:
```
$ sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com F0876AC9 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com F0876AC9
gpg: requesting key F0876AC9 from hkp server keyserver.ubuntu.com
gpg: key F0876AC9: "Launchpad PPA for Jonathan Beck" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1

```

I dont know if this output is normal but i cant find any documentation about this

---

### Post by unamanic on 2009-11-02
It's saying that you already have the key installed and it hasn't changed since the last time you downloaded it.  You should be able to proceed on to the next step.  Although without a link to the instuctions I don't know what the next step is.  (probably sudo apt-get install something)

---

### Post by CanadianBac0n77 on 2009-12-12
> **unamanic said:**
> It's saying that you already have the key installed and it hasn't changed since the last time you downloaded it.  You should be able to proceed on to the next step.  Although without a link to the instuctions I don't know what the next step is.  (probably sudo apt-get install something)

The link: [html]http://www.ubuntugeek.com/how-to-connect-iphoneipod-touch-using-usbin-karmicjauntyintrepidhardy.html[/html]I did all of this and still nothing...

---

### Post by eakinc on 2009-12-15
It works great with newest ifuse from ppa
[https://launchpad.net/~gilir/+archive/unstable](https://launchpad.net/~gilir/+archive/unstable)
A) Grab ifuse - you'll need to add the following sources to your /etc/apt/sources.list (you can do this through your preferred package management software as well):
-------------------------------------------
deb [http://ppa.launchpad.net/gilir/unstable/ubuntu](http://ppa.launchpad.net/gilir/unstable/ubuntu) karmic main 
deb-src [http://ppa.launchpad.net/gilir/unstable/ubuntu](http://ppa.launchpad.net/gilir/unstable/ubuntu) karmic main 

Signing key:
    1024R/2207789D 
$sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2207789D

$sudo apt-get install ifuse
$sudo apt-get install usbmuxd
need 

Package: ifuse
Source: ifuse
Priority: optional
Section: utils
Installed-Size: 60
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Version: 0.9.5-0ubuntu1~ppa1
Depends: libc6 (>= 2.3.6-6~), libfuse2 (>= 2.6), libglib2.0-0 (>= 2.14.1), libgnutls26 (>= 2.7.14-0), libiphone0, libplist0, libtasn1-3 (>= 1.6-0), libusb-1.0-0 (>= 2:1.0.3), libusbmuxd1, libxml2 (>= 2.6.27)
Filename: pool/main/i/ifuse/ifuse_0.9.5-0ubuntu1~ppa1_i386.deb
Size: 10702
MD5sum: 956051951426b4b1e277f7cc2f4ed67c
SHA1: eb17bd55f59b5041970ced0253836f77bb8cea51
Description: FUSE module for iPhone and iPod Touch devices
 iFuse is a FUSE filesystem driver which uses libiphone to connect to iPhone
 and iPod Touch devices without needing to "jailbreak" them. iFuse uses the
 native Apple AFC protocol over a normal USB cable in order to access the
 device's media files.
 .
 Although iFuse is now in a working state it is still under heavy
 development and should be considered experimental.

Package: usbmuxd
Source: usbmuxd
Priority: optional
Section: utils
Installed-Size: 132
Maintainer: Julien Lavergne <gilir@ubuntu.com>
Architecture: i386
Version: 1.0.0~rc2-0ubuntu1~ppa2
Depends: libc6 (>= 2.4), libusb-1.0-0 (>= 2:1.0.3), libusbmuxd1
Filename: pool/main/u/usbmuxd/usbmuxd_1.0.0~rc2-0ubuntu1~ppa2_i386.deb
Size: 25948
MD5sum: 1de0524a4479fc26641287c7751b7113
SHA1: 5f3de3fe697783a98aee39c286a5a22e42b2b6e3
Description: Socket daemon to multiplex connections from and to the iPhone
 A socket daemon to multiplex connections from and to the iPhone.

to mount
$ifuse /media/ipod
won't unmout from rt-click desktop, must be root
$sudo umount /media/ipod

-------------------------------------------
Which should install the ifuse package

---

