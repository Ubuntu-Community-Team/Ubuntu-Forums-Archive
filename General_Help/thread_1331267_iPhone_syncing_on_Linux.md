---
title: "iPhone syncing on Linux"
date: 2009-11-19
forum: General Help
---

### Post by satimis on 2009-11-19
Hi folks,

IPhone 3GS
iTune 9
KVM - Virtualization software
Host - Debian 5.0
VM - Utunto 9.04


Since iTune 9 can't work properly on wine.  I'm prepared to make IPhone communicating with Linux according to following document;

iPhone syncing on Linux
[http://marcansoft.com/blog/2009/10/iphone-syncing-on-linux/#more-104](http://marcansoft.com/blog/2009/10/iphone-syncing-on-linux/#more-104)

It requires following packages;

libusb
usbmuxd
libiphone
iFuse
gvfs-backend-afc


I'll install above packages on VM.  However I can't find them on repo.  Please advise where can I download their binary package?  Otherwise I have to download their compressed tarballs.

Is there any way to convert tar.bz2 to rpm/deb so that I can install the later with dpkg?

Another question is if they are running on VM(client, NOT host), can IPhone be detected via USB connection

TIA

B.R.
satimis

---

### Post by eakinc on 2009-12-15
It works great had to have newest ifuse from ppa
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
Can now browse.
Won't unmount from rt-click desktop, must be root
$sudo umount /media/ipod

---

### Post by satimis on 2009-12-15
> **eakinc said:**
> It works great had to have newest ifuse from ppa
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
Can now browse.
Won't unmount from rt-click desktop, must be root
$sudo umount /media/ipod

Hi eakinc,

Lot of thanks for your detail advice.

About 2 weeks ago I followed;
[http://www.ubuntugeek.com/how-to-connect-iphoneipod-touch-using-usbin-karmicjauntyintrepidhardy.html](http://www.ubuntugeek.com/how-to-connect-iphoneipod-touch-using-usbin-karmicjauntyintrepidhardy.html)

to install iFuse and other related packages on Ubuntu9.04 running as VM.  It worked.  I can upload music files to ipod and remove them from ipod as well.  However the music files upload can't be viewed on IPhone.  I suppose it has been encrypted.

Please advise can the music files upload work on IPhone?  TIA


B.R.
satimis

---

### Post by manuw2009 on 2009-12-16
Hi guys, 
I own an ipod touch 3G.
Managed to find a simple solution under karmic (submitted a tutorial on this yesterday).

Found the following ppa of great help :
[https://launchpad.net/~pmcenery/+archive/ppa?field.series_filter=karmic]("https://launchpad.net/%7Epmcenery/+archive/ppa?field.series_filter=karmic")

this provides with both the latest libiphone & libgpod, usbmuxd & ifuse and with gvfs 1.5, which enables to mount the ipod/iphone under rhythmbox (without gvfs, you'll have to manually ifuse mount/unmount).

transfer rates are still slow but it's a huge step from the WinXP-virtualbox solution.
gtkpod can be used too (especially for video transfers & file deletion, as rhythmbox is not deleting music properly).

Still waiting for an amarok 2.2.2 detection of the ipod to perform every task with the same software (video, music, deletion), can'tbfigure it out (there's the following bug though : [https://bugs.kde.org/show_bug.cgi?id=182831](https://bugs.kde.org/show_bug.cgi?id=182831))
Hope this helps
Manu

---

### Post by BadSeqtor on 2009-12-21
Automounting is not working for me since upgrade to Karmic 9.10.
Worked on 9.04.

If I run usbmuxd in console mode, I can manually mount with iFuse - so I guess my problem is usbmuxd not running correctly.

Anyone have any ideas? I have tried all sorts of reinstalls etc.

---

