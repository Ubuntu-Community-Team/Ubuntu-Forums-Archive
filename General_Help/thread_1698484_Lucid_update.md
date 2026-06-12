---
title: "Lucid update"
date: 2011-03-02
forum: General Help
---

### Post by Otto-C on 2011-03-02
Using Lucid 2.6.32-28-generic #55-Ubuntu SMP Mon Jan 10 ...
Update manager presents 7 items for update having to do with headers an example reads 'Linux-headers-2.6.32-29-generic (new install)'.
I have previously done all updates and I think one crashed and I blocked the above Linux-headers type items. Then installed the items. This has appeared again today. Why the 'new install' attached to the items. The initial install was done in November 2010.

tia
otto-c

---

### Post by Frogs Hair on 2011-03-02
When the kernel updates it comes with new headers for the kernel. Kernel updates include security updates an sometimes driver updates. Kernels may update many times during the life of a release .
 
It is up to you if you want to update or not but the option to do so will be offered each time you open the update manager unless turn off check for updates ( not recommended )
 
Also a kenel version may update more than once new install may indicate the first install of the 29 kernel.

---

### Post by mikewhatever on 2011-03-02
It's a new install, because newer kernels do not replace the older ones. If the OS was installed in November, it has likely accumulated quite a few of those kernels, and now you are being offered another one. Run the following command to check how many kernels are currently installed:
```
dpkg -l | grep linux-image
```

---

### Post by philinux on 2011-03-02
New kernels also usually include bug fixes, some security fixes and improved hardware support.

---

