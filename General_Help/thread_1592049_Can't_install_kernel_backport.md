---
title: "Can't install kernel backport"
date: 2010-10-10
forum: General Help
---

### Post by hensan on 2010-10-10
I'm trying to install a maverick kernel backport on my 10.04 installation but I'm getting just get this:

```
hensan@mediabox:~$ sudo apt-get install linux-generic-lts-backport-maverick linux-headers-generic-lts-backport-maverick linux-image-generic-lts-backport-maverick
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  linux-headers-generic-lts-backport-maverick: Depends: linux-headers-2.6.35-22-generic but it is not installable
  linux-image-generic-lts-backport-maverick: Depends: linux-image-2.6.35-22-generic but it is not installable
E: Broken packages
```

I have followed the instructions on the Ubuntu Kernel PPA page, I added the kernel-ppa/ppa repository and ran an apt-get update. What's going on here?

---

