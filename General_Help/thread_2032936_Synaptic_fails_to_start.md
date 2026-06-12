---
title: "Synaptic fails to start"
date: 2012-07-25
forum: General Help
---

### Post by OldAlgis on 2012-07-25
This morning I wanted to see what Java I've got in my installation of kubuntu 12.04 LTS (precise), i386 version.  So I started Synaptic GUI with a happy click and got the following message:

> E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.


I am sorry, but I got no idea what to report and how to report this. The error is fatal as the Synaptic closes on cliking the OK key.  I would think that apt will not work either.  Is anyone else experiencing this problem?

Any suggestions?

PS: The following is listing of the file in /var/lib/apt/lists/x, pointed to by the error message:
> 
The following is the contents of a file in /var/lib/apt/lists/x  
where x == 
security.ubuntu.com_ubuntu_dists_precise-security_multiverse_binary-i386_Packages
=======================================
Package: flashplugin-downloader
Priority: optional
Section: multiverse/web
Installed-Size: 41
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Bart Martens <bartm@knars.be>
Architecture: i386
Source: flashplugin-nonfree
Version: 11.2.202.236ubuntu0.12.04.1
Depends: flashplugin-installer (>= 11.1.102.55ubuntu3)
Filename: pool/multiverse/f/flashplugin-nonfree/flashplugin-downloader_11.2.202.236ubuntu0.12.04.1_i386.deb
Size: 1836
MD5sum: 63fbdb54db9288a64605ebeceefa67e7
SHA1: 1101af739af27063f70f23785dc937f2dc8fc867
SHA256: 38f43933ed93b5fc066e6f7d788570fc373f5183532e3a0a2a7b154474294f67
Description: Adobe Flash Player plugin installer (transitional package)
Multi-Arch: foreign
Homepage: [http://www.adobe.com/products/flashplayer.html](http://www.adobe.com/products/flashplayer.html)
Description-md5: 66ea91f4e504085408ea841953dc65d0
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Origin: Ubuntu

Package: flashplugin-installer
Priority: optional
Section: multiverse/web
Installed-Size: 136
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Bart Martens <bartm@knars.be>
Architecture: i386
Source: flashplugin-nonfree
Version: 11.2.202.236ubuntu0.12.04.1
Replaces: flashplugin (<< 6), flashplugin-downloader (<< 11.1.102.55ubuntu3), flashplugin-nonfree (<< 11.0.1.152ubuntu1)
Provides: flashplugin-nonfree
Depends: debconf (>= 0.5) | debconf-2.0, wget, libgtk2.0-0, fontconfig, libxt6, libxext6, libatk1.0-0, libc6, libcairo2, libexpat1, libfontconfig1, libfreetype6, libglib2.0-0, libice6, libpango1.0-0, libpng12-0, libsm6, libx11-6, libxau6, libxcursor1, libxdmcp6, libxfixes3, libxi6, libxinerama1, libxrandr2, libxrender1, zlib1g, libnss3-1d, libnspr4-0d, libcurl3 | libcurl3-gnutls, libasound2, update-notifier-common (>= 0.119ubuntu2)
Recommends: libasound2-plugins (>= 1.0.16)
Suggests: firefox, x-ttcidfont-conf, ttf-mscorefonts-installer, ttf-bitstream-vera | ttf-dejavu, ttf-xfree86-nonfree, xfs
Conflicts: flashplayer-mozilla, flashplugin (<< 6), flashplugin-nonfree (<< 11.0.1.152ubuntu1), libflashsupport
Breaks: flashplugin-downloader (<< 11.1.102.55ubuntu3)
Filename: pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_11.2.202.236ubuntu0.12.04.1_i386.deb
Size: 8296
MD5sum: c5a6d68629f62765b30e5963d4315447
SHA1: 5356a868bf86e3d7b4633c0f0ff230b25e3b5011
SHA256: 1da985378c6b6a46c16de4bcb960603b6ddf3b987dd04122d96e8f9afb63cd76
Description: Adobe Flash Player plugin installer
Multi-Arch: foreign
Homepage: [http://www.adobe.com/products/flashplayer.html](http://www.adobe.com/products/flashplayer.html)
Npp-Applications: ec8030f7-c20a-464f-9b0e-13a3a9e97384, 92650c4d-4b8e-4d2a-b7eb-24ecf4f6b63a, aa5ca914-c309-495d-91cf-3141bbb04115
Npp-Description: Adobe Flash SWF Player ([http://www.adobe.com](http://www.adobe.com))
Npp-File: libflashplayer.so
Npp-Mimetype: application/x-shockwave-flash
Npp-Name: Adobe Flash Player (installer)
Description-md5: a03e9ebc20ce82c05567d088e79bf750
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Origin: Ubuntu


---

### Post by oldos2er on 2012-07-25
```
sudo rm /var/lib/apt/lists/* -vf

sudo apt-get update

```

---

### Post by OldAlgis on 2012-07-26
> **oldos2er said:**
> ```
sudo rm /var/lib/apt/lists/* -vf

sudo apt-get update

```

Hi, thanks for the receipe to regenerate the lists! As a precaution against "skies falling in", I kept a copy of the contents of "lists" directory so did the following
```

~$ mkdir apt-lists
sudo mv /var/lib/apt/lists/* ~/apt-lists/
sudo apt-get update

```
The skies did not fall in. I wonder what information I lost in regenerating the apt list?

Thanks again for the great suggestion. I marked this thread as SOLVED!

---

