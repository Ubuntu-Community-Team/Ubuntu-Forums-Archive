---
title: "My ubuntu isn't on the latest kernel"
date: 2009-07-29
forum: General Help
---

### Post by pedro3005 on 2009-07-29
[www.kernel.org](www.kernel.org) shows the latest kernel to be "2.6.30.3" but I'm still on "2.6.28.14". How can I update it? Update manager doesn't offer it.

---

### Post by HappyFeet on 2009-07-29
That's because Jaunty will always be on the current kernel until end of life. It's set up that way. Although I have not done it, I'm sure there is a way to get the latest kernel. Is there a reason you need it? You can always enable backports if you need the latest and greatest apps, or just download the PPA versions of apps.

If you could just update kernels on a whim, there would be little reason to have releases in the first place. Plus, some people have success with one kernel (release) yet not another.

---

### Post by pedro3005 on 2009-07-30
But then why do sometimes there are kernel updates avaliable through update manager?

---

### Post by rob1408 on 2009-07-30
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

Choose your Kernel from here.

1)Download and install the Linux-header all deb 
2)Download and install the Linux-header for your architecture (amd64 or i386)
3)Download and install the Linux-image deb for your architecture (amd64 or i386)
4)reboot.

---

### Post by CatKiller on 2009-07-30
> **pedro3005 said:**
> But then why do sometimes there are kernel updates avaliable through update manager?

Security fixes. It's the same with all of the packages installed through the repositories (with a limited number of exceptions); you get security fixes and bug fixes. New releases for new features come with the next release. Ubuntu has always been this way.

The kernels have the same version number, but a different point release to show that they've been updated.

The new versions of packages are currently being tested by the kind people that have been Alpha testing Karmic for the last three months.

---

### Post by thezood on 2009-07-31
> **pedro3005 said:**
> [www.kernel.org](www.kernel.org) shows the latest kernel to be "2.6.30.3" but I'm still on "2.6.28.14". How can I update it? Update manager doesn't offer it.

If you don't have a problem with your current kernel, don't update. However, if you're unlucky and have hardware that's not supported by Jaunty's kernel or are having performance issues, it could be worth giving it a try. I, for instance, have an Intel graphics chipset and gained about an 150% increase in graphics performance with the 2.6.31 kernel. Since it's not a final release, it has some issues, though, as it hasn't been tested properly. 

Also, keep in mind that if you decide to manually upgrade, you'll have to keep track of security/stability updates to the kernel yourself since you'll no longer be using the software repositories.

---

