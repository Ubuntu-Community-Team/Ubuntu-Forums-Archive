---
title: "How to update kernel module for Nvidia drivers?"
date: 2009-08-17
forum: General Help
---

### Post by imjustsomeguy72 on 2009-08-17
Hey all,

I've recently updated my 8.04 system to 8.10 (32-bit), and I've run into some problems driver wise.

Initially, the X server would crash on startup, and I would have to run in low-res mode.

I found that the 177 version of the Nvidia driver was activated in Hardware Drivers, but there were two other Nvidia drivers (one newer, and one older) that were also displayed. If I try to alter the configuration at all, I get an error telling me I'm not authorized to make those changes.

Anyway, to try and get around this problem, I've attempted to update my driver manually. I downloaded the package, executed it, and followed the installer through to completion. I did have to attempt to build a new kernel module.

However, this did not solve my problem; everything is exactly the same as it was before. Running 'dmesg' gave me an output saying:

> NVRM: API mismatch: the client has the version 185.18.31, but this kernel module has the version 177.82. Please make sure this kernel module and all NVIDIA driver components have the same version

This seems fairly self explanatory, and indicates either the installer compiled the wrong kernel module, or failed to overwrite the old one.

In any case, I have no clue as to how I'd go about installing the correct version module. Any ideas?

Cheers!

---

### Post by hrafninn on 2009-08-18
> In any case, I have no clue as to how I'd go about installing the correct version module. Any ideas?

I had the exact same problem and had been spending hours to try to fix it.  The "dmesg" output is the key.

In my case, the client had version 185.18.31 but the kernel module had version 180.44.  I went to [http://www.nvidia.com/object/unix.html]("http://www.nvidia.com/object/unix.html"), selected the "Archive" link under the "Linux IA32" heading and downloaded the package with the correct version (i.e. 180.44).

Then I executed it (as root in a login shell), followed the installer through to completion (a new kernel module was built), and bingo, the NVIDIA driver works!

---

### Post by imjustsomeguy72 on 2009-08-22
Hey,

I actually managed to solve the problem another way, in the end.

I removed a couple of packages via Synaptic, including linux-restricted-modules and several variants, and then reinstalled the Nvidia drivers. Everything works!

I assume for some reason the Synaptic modules took precedence over ones downloaded from random places, which would explain why the older modules kept getting loaded.

But thanks for your solution hrafninn! It probably would have saved me a lot of mucking about in Synaptic ;)

---

