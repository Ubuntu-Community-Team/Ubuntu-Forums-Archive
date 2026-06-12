---
title: "Upgrading kernel"
date: 2006-03-03
forum: General Help
---

### Post by dsjas297 on 2006-03-03
How can I upgrade my kernel? I do not have internet access on my Ubuntu system, so I am unable to upgrade it using Synaptic package manager.

---

### Post by Q4U on 2006-03-03
1. Download the packages from a machine that has internet, and put them
 on a flash USB. You need the packages called "kernel" and "restricted modules".
2. Create a repository on your hard disk (search this forum to find out how to do it) and load the packages using Synaptic.
3. Done!

Q4U

---

### Post by towsonu2003 on 2006-03-03
Another alternative would be to search the packages (packages.ubuntu.com) you want (in this case: linux-headers-newkernelversion ; linux-image-newkernelversion ; linux-restricted-modules-newkernelversion -> make sure newkernelversion is the same for all). Download them to your desktop.

Than 
```

cd
cd Desktop
sudo dpkg -i linux-image-newkernelversion linux-restricted-modules-newkernelversion linux-headers-newkernelversion 
```
while hoping that there are no unmet dependencies. If there are, go back to packages.ubuntu.com, download them, dpkg -i (install) them, and I belive sudo dpkg-reconfigure linux-image-newkernelversion linux-restricted-modules-newkernelversion linux-headers-newkernelversion

I think this is the way

PS. linux-headers is required if you need to compile stuff..

---

