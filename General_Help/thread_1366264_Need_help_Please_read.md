---
title: "Need help: Please read"
date: 2009-12-28
forum: General Help
---

### Post by bobbykleinveld on 2009-12-28
Hello,

Whenever I want to install or uninstall programs I get the following error message:

Error! DKMS tree already contains: rt2870-linux-sta-2.1.2.0 
You cannot add the same module/version combo more than once. 
ERROR: dkms add failed. 
dpkg: error processing rt2870-linux-sta (--configure): 
 subprocess installed post-installation script returned error exit status 1 
Errors were encountered while processing: 
 rt2870-linux-sta

I tried searching for "rt2870-linux-sta" info but can't find anything about it? Don't even know what it means... Can anyone please help me with this problem? What should I do?

Thanks
B

---

### Post by mgol on 2009-12-28
Try:
```
sudo dpkg --configure -a
```

---

### Post by bobbykleinveld on 2009-12-28
Thanks Mgol,

I tried it but I still get this error:

Error! DKMS tree already contains: rt2870-linux-sta-2.1.2.0
You cannot add the same module/version combo more than once.
ERROR: dkms add failed.
dpkg: error processing rt2870-linux-sta (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 rt2870-linux-sta

Is there anything else I can try?

B

---

### Post by mgol on 2009-12-28
This package must come from a non-standard repository - from which one? Please give the output of the following:
```

apt-cache policy rt2870-linux-sta
dkms status
uname -a

```

---

### Post by john newbuntu on 2009-12-28
remove the dkms package and see if that helps:
sudo apt-get remove dkms

---

### Post by mgol on 2009-12-28
> **john newbuntu said:**
> remove the dkms package and see if that helps:
sudo apt-get remove dkms
It is kind of a solution, but some packages need dkms to correctly build their modules after kernel updates. Dkms removal forces users to do this rebuild manually which can be annoying. I'd rather advise to check modules dkms takes care of by invoking:
```
dkms status
```

For example, for me output is the following:
```

$ dkms status
bcmwl, 5.10.91.9+bdcom, 2.6.31-15-generic, x86_64: installed 
bcmwl, 5.10.91.9+bdcom, 2.6.31-16-generic, x86_64: installed 
bcmwl, 5.10.91.9+bdcom, 2.6.31-14-generic, x86_64: built 
vboxnetflt, 3.1.2, 2.6.31-16-generic, x86_64: installed 
vboxnetadp, 3.1.2, 2.6.31-16-generic, x86_64: installed 
vboxdrv, 3.1.2, 2.6.31-16-generic, x86_64: installed 

```
Dkms removal would mean I have to rebuild WiFi and VirtualBox modules. I would be careful about that.

---

### Post by bobbykleinveld on 2009-12-28
Mgol,

Regarding the repository I get the following:

bobby@bobby-desktop:~$ apt-cache policy rt2870-linux-sta
rt2870-linux-sta:
  Installed: 2.1.2.0-0ubuntu2
  Candidate: 2.1.2.0-0ubuntu2
  Version table:
 *** 2.1.2.0-0ubuntu2 0
        100 /var/lib/dpkg/status
bobby@bobby-desktop:~$ dkms status
rt2870-linux-sta, 2.1.2.0: added 
bobby@bobby-desktop:~$ uname -a
Linux bobby-desktop 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009 i686 GNU/Linux

I'm now going to try remove the dkms... I'll post what terminal tells me once that is done...

Thanks

---

### Post by bobbykleinveld on 2009-12-28
Mgol,

I first did the dkms status and got this:

bobby@bobby-desktop:~$ dkms status
rt2870-linux-sta, 2.1.2.0: added 

I'll wait for your reply before removing... 

B

---

### Post by mgol on 2009-12-28
> **bobbykleinveld said:**
> 

Regarding the repository I get the following:

bobby@bobby-desktop:~$ apt-cache policy rt2870-linux-sta
rt2870-linux-sta:
  Installed: 2.1.2.0-0ubuntu2
  Candidate: 2.1.2.0-0ubuntu2
  Version table:
 *** 2.1.2.0-0ubuntu2 0
        100 /var/lib/dpkg/status

It means You installed it manually, not from a regular repository. Do You know what is the purpose of this package? You can check it by:
```
apt-cache show rt2870-linux-sta
```
If You don't need this package, remove it:
```
sudo apt-get purge rt2870-linux-sta
```
and try to update system again.

---

### Post by bobbykleinveld on 2009-12-28
Mgol,

I get the following message:

bobby@bobby-desktop:~$ apt-cache show rt2870-linux-sta
Package: rt2870-linux-sta
Status: install ok half-configured
Priority: optional
Section: misc
Installed-Size: 3352
Maintainer: Ubuntu MOTU <ubuntu-motu@lists.ubuntu.com>
Architecture: all
Version: 2.1.2.0-0ubuntu2
Depends: build-essential, dkms
Conffiles:
 /etc/Wireless/RT2870STA 930b4a230b65f962146c2c56988a9034
Description: RALink Tech. RT2870 Wireless LAN Linux Driver
 These are RALink's own GPLed Linux drivers to support any Wireless LAN
 device using the RT2870 chipset.
 .
 This package uses DKMS to compile the drivers from source. The kernel
 module will be built for your current kernel and will automatically
 re-build itself should you update your kernel.
 .
 They are provided since no working alternatives exists at the time.
 At some point it is expected that the RALink 2x00 WLAN driver,
 which is included in the Linux 2.6 kernel, will support this chipset
 and that will effectively mean these manufacturer supplied drivers are no
 longer necessary.
 .
 These drivers are known to work on the following hardware:
 .
 D-Link DWA-140 USB
 Sitecom 300N WL-302
Homepage: [http://www.ralinktech.com](http://www.ralinktech.com)
Original-Maintainer: Henrik Stokseth <henrik@hw0.org>

I had to install this because of my Sitecome WL-302 wireless USB. If you have any solution that I can do so that I still have wireless internet and not get this error message whenever I want to install or uninstall a program I will be very thankfull!

What can I do?

Thanks
B

---

### Post by mgol on 2009-12-28
> **bobbykleinveld said:**
> 
I had to install this because of my Sitecome WL-302 wireless USB.
Try to download the newest drivers, remove current rt2870-linux-sta package and install the new one. If You had any further problems You should look for people with similar hardware as there obviously is some problem with Your version of this package. You can also try older versions if the newest one fails.

This by the way proves that uninstalling dkms is not a solution as Your package depends on it. You may try to reinstall it:
```
sudo aptitude reinstall dkms
```
but I doubt it'll help.

Or just try to reinstall current rt2870-linux-sta package. Dkms reports some software wants to re-add this package to maintained list but it's not possible as it's already there...

If You use Ubuntu Jaunty (9.04), You can also try to uninstall rt2870-linux-sta package, add this PPA repository:
[https://launchpad.net/~henrik-hw0/+archive/ppa](https://launchpad.net/~henrik-hw0/+archive/ppa)
and install it from repositories:
```

sudo apt-get update
sudo apt-get install rt2870-linux-sta

```

---

### Post by bobbykleinveld on 2009-12-28
Mgol,

Thanks for you help. I removed the file and until now everything seems to be working the way it should. I still have wireless internet. I rebooted the system and everything till now is running smooth again... Also installing and uninstalling applications...

Anyway, thanks a million for your help! Happy New Year, I'm a bit early but it's the least I can do...

Greets
Bobby

---

