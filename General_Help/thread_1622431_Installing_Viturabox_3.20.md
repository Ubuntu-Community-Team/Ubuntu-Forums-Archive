---
title: "Installing Viturabox 3.20"
date: 2010-11-15
forum: General Help
---

### Post by daldude on 2010-11-15
I downloaded Virtuabox 3.20 but can't install it. The readme file says to do this

[B]After extracting the contents of the tar.gz file perform the following steps:

1. Login as root using the "su" command.

2. Install the VirtualBox package:

      pkgadd -d VirtualBox-3.2.10-SunOS-r66523.pkg

[/B]Assuming that login as root useing the su command means sodu I typed

**sudo pkgadd -d VirtualBox-3.2.10-SunOS-r66523.pkg **

and got this error

**sudo: pkgadd: command not found**

I figured there was a typo so I typed this 

**package -d VirtualBox-3.2.10-SunOS-r66523.pkg**

and got this error

[B]package: can't open config file /home/dal/.mailagent

[/B]
so what do I need to do to  install virtuabox? 

Thanks

---

### Post by sikander3786 on 2010-11-15
Isn't the same version available in the repositories?

Try searching Software Center for Virtualbox and you'll see the open source edition.

If you want the proprietary version of Virtualbox (supports USB devices), there is a package for Ubuntu on their website (.deb package). Download that one and it will be as easy as double click and go.

Edit: Here's the link. Select your Ubuntu version and architecture and download the appropriate package.

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

---

