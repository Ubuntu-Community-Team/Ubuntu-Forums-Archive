---
title: "VMware can't compile modules"
date: 2011-10-02
forum: General Help
---

### Post by nikhilbhardwaj on 2011-10-02
I installed vmware player, upon running it it asks for compiling modules.
That step fails, here's the output of the log file.
 I'm running 11.10 beta2

Here's my log file```

Oct 02 19:39:23.409: app-140027678226208| Building module vmmon.
Oct 02 19:39:23.409: app-140027678226208| Extracting the sources of the vmmon module.
Oct 02 19:39:23.425: app-140027678226208| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmmon-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/3.0.0-11-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.6.1
Oct 02 19:39:24.511: app-140027678226208| Failed to compile module vmmon!
Oct 02 19:39:28.088: app-140027678226208| Trying to find a suitable PBM set for kernel 3.0.0-11-generic.
Oct 02 19:39:28.092: app-140027678226208| Trying to find a suitable PBM set for kernel 3.0.0-11-generic.
Oct 02 19:39:28.096: app-140027678226208| Trying to find a suitable PBM set for kernel 3.0.0-11-generic.
Oct 02 19:39:28.099: app-140027678226208| Trying to find a suitable PBM set for kernel 3.0.0-11-generic.
Oct 02 19:39:28.101: app-140027678226208| Trying to find a suitable PBM set for kernel 3.0.0-11-generic.
Oct 02 19:39:28.106: app-140027678226208| Your GCC version: 4.6
Oct 02 19:39:28.117: app-140027678226208| Your GCC version: 4.6
Oct 02 19:39:28.175: app-140027678226208| Trying to find a suitable PBM set for kernel 3.0.0-11-generic.
Oct 02 19:39:28.178: app-140027678226208| Trying to find a suitable PBM set for kernel 3.0.0-11-generic.
Oct 02 19:39:28.180: app-140027678226208| Trying to find a suitable PBM set for kernel 3.0.0-11-generic.
Oct 02 19:39:28.182: app-140027678226208| Trying to find a suitable PBM set for kernel 3.0.0-11-generic.
Oct 02 19:39:28.184: app-140027678226208| Trying to find a suitable PBM set for kernel 3.0.0-11-generic.
Oct 02 19:39:28.665: app-140027678226208| Trying to find a suitable PBM set for kernel 3.0.0-11-generic.
Oct 02 19:39:28.666: app-140027678226208| Building module vmmon.
Oct 02 19:39:28.666: app-140027678226208| Extracting the sources of the vmmon module.
Oct 02 19:39:28.686: app-140027678226208| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmmon-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/3.0.0-11-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.6.1
Oct 02 19:39:29.800: app-140027678226208| Failed to compile module vmmon!
```

---

### Post by dcstar on 2011-10-03
> **nikhilbhardwaj said:**
> I installed vmware player, upon running it it asks for compiling modules.
That step fails, here's the output of the log file.
 **I'm running 11.10 beta2**
..........

[LIST=1]
[*]You are using pre-relase software, there is no support in these forums for pre-release software.
[*]Post all VM issues in the Virtualization forum.
[*]VMware's products are obviously not yet supporting unreleased software.
[/LIST]

---

