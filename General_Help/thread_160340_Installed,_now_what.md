---
title: "Installed, now what??"
date: 2006-04-14
forum: General Help
---

### Post by pr0-t31n on 2006-04-14
Thanks to pple on these forums Ive installed something, Limewire! [http://www.limewire.com/LimeWireSoftLinux]("http://www.limewire.com/LimeWireSoftLinux")
I learned how to install the rpm file with alien from the guide one person had posted.
Now, under Applications>Internet> I have Limewire, but when I click on it there is no action watsoever.  Thanks guys and have a wonderful day!
Im begging to take a shine to Linux, maybe I can get it down before college!

---

### Post by pr0-t31n on 2006-04-14
btw is this correct???

[QUOTE=ME @ TERMINAL]pr0t31n@2wire:~$ sudo apt-get update
Password:
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Sources
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release [27.0kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Sources
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages [45.6kB]
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages [4458B]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources [14.4kB]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources [960B]
Fetched 92.7kB in 2s (45.0kB/s)
Reading package lists... Done
pr0t31n@2wire:~$ sudo apt-get install alien
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  binutils debconf-utils debhelper dpkg-dev gettext html2text intltool-debian
  librpm4 make po-debconf rpm
Suggested packages:
  lsb-rpm lintian binutils-doc dh-make debian-keyring cvs gettext-doc
Recommended packages:
  gcc c-compiler curl libmail-sendmail-perl libcompress-zlib-perl
The following NEW packages will be installed:
  alien binutils debconf-utils debhelper dpkg-dev gettext html2text
  intltool-debian librpm4 make po-debconf rpm
0 upgraded, 12 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/5150kB of archives.
After unpacking 18.5MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Media change: please insert the disc labeled
 'Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)'
in the drive '/cdrom/' and press enter

Media change: please insert the disc labeled
 'Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)'
in the drive '/cdrom/' and press enter

Media change: please insert the disc labeled
 'Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)'
in the drive '/cdrom/' and press enter


Preconfiguring packages ...
Selecting previously deselected package make.
(Reading database ... 61574 files and directories currently installed.)
Unpacking make (from .../m/make/make_3.80-9_i386.deb) ...
Selecting previously deselected package binutils.
Unpacking binutils (from .../binutils_2.16.1-2ubuntu6_i386.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.13.10ubuntu4_all.deb) ...
Selecting previously deselected package html2text.
Unpacking html2text (from .../html2text_1.3.2a-2build1_i386.deb) ...
Selecting previously deselected package debconf-utils.
Unpacking debconf-utils (from .../debconf-utils_1.4.56ubuntu2_all.deb) ...
Selecting previously deselected package gettext.
Unpacking gettext (from .../gettext_0.14.5-2ubuntu2_i386.deb) ...
Selecting previously deselected package intltool-debian.
Unpacking intltool-debian (from .../intltool-debian_0.30+20040213_all.deb) ...
Selecting previously deselected package po-debconf.
Unpacking po-debconf (from .../po-debconf_0.8.23_all.deb) ...
Selecting previously deselected package debhelper.
Unpacking debhelper (from .../debhelper_4.9.5ubuntu1_all.deb) ...
Selecting previously deselected package librpm4.
Unpacking librpm4 (from .../librpm4_4.0.4-31ubuntu1.1_i386.deb) ...
Selecting previously deselected package rpm.
Unpacking rpm (from .../rpm_4.0.4-31ubuntu1.1_i386.deb) ...
Selecting previously deselected package alien.
Unpacking alien (from .../a/alien/alien_8.53_all.deb) ...
Setting up make (3.80-9) ...

Setting up binutils (2.16.1-2ubuntu6) ...

Setting up dpkg-dev (1.13.10ubuntu4) ...
Setting up html2text (1.3.2a-2build1) ...

Setting up debconf-utils (1.4.56ubuntu2) ...

Setting up gettext (0.14.5-2ubuntu2) ...

Setting up intltool-debian (0.30+20040213) ...
Setting up po-debconf (0.8.23) ...
Setting up debhelper (4.9.5ubuntu1) ...
Setting up librpm4 (4.0.4-31ubuntu1.1) ...

Setting up rpm (4.0.4-31ubuntu1.1) ...

Setting up alien (8.53) ...
pr0t31n@2wire:~$ cd desktop
bash: cd: desktop: No such file or directory
pr0t31n@2wire:~$ cd Desktop
pr0t31n@2wire:~/Desktop$ sudo alien -i LimeWireLinux.rpm[/QUOTE]

---

### Post by r4ik on 2006-04-14
Have you got Java installed ?
If not you can find it here  (7.3)

[http://easylinux.info/wiki/Ubuntu](http://easylinux.info/wiki/Ubuntu)

Good luck !

---

### Post by pr0-t31n on 2006-04-15
YAY! I did it!! but now when I try to open my downloaded mp3 file; (LEGALLL!) i have an error in all music players [QUOTE=RHYTHMBOX MUSIC PLAYER]the file is not an audio stream[/QUOTE]

---

