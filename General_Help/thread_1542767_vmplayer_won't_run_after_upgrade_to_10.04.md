---
title: "vmplayer won't run after upgrade to 10.04"
date: 2010-07-31
forum: General Help
---

### Post by ubnewbie2 on 2010-07-31
It tries to recompile, but fails, and all the setup log has in it is

Jul 31 16:12:08.784: app| Log for VMware Workstation pid=3521 version=6.5.2 build=build-156735 option=Release
Jul 31 16:12:08.785: app| Host codepage=UTF-8 encoding=UTF-8
Jul 31 16:12:08.785: app| Logging to /tmp/vmware-root/setup-3521.log
Jul 31 16:12:09.606: app| Extracting the sources of the vmmon module.
Jul 31 16:12:09.620: app| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmmon-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.32-24-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.3

---

### Post by luigi_mb on 2010-07-31
> **ubnewbie2 said:**
> It tries to recompile, but fails, and all the setup log has in it is

Jul 31 16:12:08.784: app| Log for VMware Workstation pid=3521 version=6.5.2 build=build-156735 option=Release
Jul 31 16:12:08.785: app| Host codepage=UTF-8 encoding=UTF-8
Jul 31 16:12:08.785: app| Logging to /tmp/vmware-root/setup-3521.log
Jul 31 16:12:09.606: app| Extracting the sources of the vmmon module.
Jul 31 16:12:09.620: app| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmmon-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.32-24-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.3

Have you installed "dkms" (Synaptic) ?

/luigi

---

### Post by ubnewbie2 on 2010-07-31
> **luigi_mb said:**
> Have you installed "dkms" (Synaptic) ?

/luigi

Don't know what dkms is, but I just solved the problem by installing the latest vmplayer software. I think the version I had was incompatible with 10.04.  Thanks.

---

