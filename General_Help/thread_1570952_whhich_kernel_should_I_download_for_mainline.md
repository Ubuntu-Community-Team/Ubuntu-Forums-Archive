---
title: "whhich kernel should I download for mainline?"
date: 2010-09-08
forum: General Help
---

### Post by sf_basilix on 2010-09-08
I'm looking for some guidance on how to install a mainline kernel. I opened a ticket for a problem I'm having here:
[https://bugs.launchpad.net/ubuntu/+bug/628986](https://bugs.launchpad.net/ubuntu/+bug/628986)

It was suggested to me that I go here for instructions on how to install the mainline kernels:
[https://wiki.ubuntu.com/KernelMainlineBuilds](https://wiki.ubuntu.com/KernelMainlineBuilds)

However, when I go there, it explains what to download if you have 32 bit intel (i386) or AMD 64 bit (amd64), but does anyone know what I should download if I need an x86_64 (64bit 10.04 lucid) kernel? Is it i386? Wouldn't that just be 32 bits?  I have a Dell e6510 laptop running 64 bit lucid (10.04 - kernel 2.6.32-23) on an Intel Core i5.  My laptop stopped working when the 2.6.32-24 kernel was downloaded and installed through the update manager.

Looking for some advice - thanks!

---

### Post by harrismh777 on 2010-09-08
The upgrade probably added the new kernel to the grub menu list, and left the previous kernel alone. 

When you boot can you select the next (older) kernel from the list and bootup?

---

### Post by inameiname on 2010-09-08
If you want a mainline kernel, as in one without any modification on the part of Ubuntu, just download the debs here. They are the original thing, but thrown into deb format for easy installation.

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by sf_basilix on 2010-09-09
> **harrismh777 said:**
> The upgrade probably added the new kernel to the grub menu list, and left the previous kernel alone. 

When you boot can you select the next (older) kernel from the list and bootup?

Yes, I had to do this when my screen went black. I held the shift key in and selected an older kernel and now I'm back in, but I would like to install a newer kernel for the bug team to help diagnose what the problem is.

---

### Post by sf_basilix on 2010-09-09
> **inameiname said:**
> If you want a mainline kernel, as in one without any modification on the part of Ubuntu, just download the debs here. They are the original thing, but thrown into deb format for easy installation.

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

thanks, however my question is in regards to that link. Should I be downloading the *_i386.deb or the *_amd64.deb? The reason I ask is because I'm running 64 bit lucid on an Intel Core i5 (x86_64), however I do not see any downloadable kernels with x86_64, so which one should I choose?

as an example, look here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35-rc1-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35-rc1-lucid/)

Thanks

---

### Post by inameiname on 2010-09-09
Install the amd64 debs. Seems since AMD started the 64-bit craze, they are allowed to call 64-bit processors in general amd64. Well, from what I got here, in this thread about this very thing:

[http://ubuntuforums.org/showthread.php?p=8928951](http://ubuntuforums.org/showthread.php?p=8928951)

---

### Post by sf_basilix on 2010-09-09
Thanks!  This makes me very nervous as uname -a gives me x86_64, not amd64, but I'll give it a shot.


UPDATE: the amd64 files were indeed the correct ones for the x86_64 kernel (for intel 64 bit) - thanks!

---

