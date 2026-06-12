---
title: "Nvidia Issues After Updates"
date: 2009-12-05
forum: General Help
---

### Post by SergeantOreo on 2009-12-05
Hello, 

After getting updates from update manager today, my system completely messed up in regard to Nvidia drivers.

I have managed to get it to a working state by purging the existing drivers
(ubuntu-glx-185), and using Envyng to install 185.18.36-0ubuntu9; but, even after a successful installation, Compiz and desktop effects are not working.

After a little more research, I found that I do not have linux-restricted-modules installed, so I ran>  sudo apt-get install linux-restricted-modules-`uname -r` and got > Couldn't find package linux-restricted-modules-2.6.31-16-generic

Apparently this package is necessary for the proper function of Nvidia drivers.. but, how can I install the package when it is not in the repositories?

Thanks. ;)

---

### Post by Meskarune on 2009-12-05
Download: [https://launchpad.net/ubuntu/+archive/primary/+files/linux-restricted-modules-2.6.15_2.6.15.11.orig.tar.gz](https://launchpad.net/ubuntu/+archive/primary/+files/linux-restricted-modules-2.6.15_2.6.15.11.orig.tar.gz)

then un-tar the file

then open the terminal in the file you just un-tared

type:

```
./configure
make
sudo make install
```

---

### Post by SergeantOreo on 2009-12-05
> **Meskarune said:**
> Download: [https://launchpad.net/ubuntu/+archive/primary/+files/linux-restricted-modules-2.6.15_2.6.15.11.orig.tar.gz](https://launchpad.net/ubuntu/+archive/primary/+files/linux-restricted-modules-2.6.15_2.6.15.11.orig.tar.gz)

then un-tar the file

then open the terminal in the file you just un-tared

type:

```
./configure
make
sudo make install
```

My brother just helped me add a repository for Nvidia driver 190.42, and that fixed it.

Thanks anyway mate! ;)

---

### Post by ibuclaw on 2009-12-05
> **SergeantOreo said:**
> My brother just helped me add a repository for Nvidia driver 190.42, and that fixed it.

Thanks anyway mate! ;)

FYI. Restricted Modules is deprecated and no longer used in favour of [DKMS]("https://help.ubuntu.com/community/DKMS")
You were probably relying on old documentation there...

---

### Post by SergeantOreo on 2009-12-05
> **tinivole said:**
> FYI. Restricted Modules is deprecated and no longer used in favour of [DKMS]("https://help.ubuntu.com/community/DKMS")
You were probably relying on old documentation there...

I don't really get what you mean by this, perhaps you could give a little more information?

---

### Post by ibuclaw on 2009-12-06
> **SergeantOreo said:**
> I don't really get what you mean by this, perhaps you could give a little more information?

All third party modules that are linked into dkms are compiled on your client machine against the new kernel automatically whenever an upgrade occurs.

This saves the hassle of how it used to be in previous versions of Ubuntu (we are talking years ago) - where you'd upgrade the kernel - then have to wait for the restricted modules to come through (which was sometimes days) before you could use your wireless card / graphics card.

Regards
Iain

---

