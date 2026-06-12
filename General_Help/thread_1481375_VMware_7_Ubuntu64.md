---
title: "VMware 7 Ubuntu64"
date: 2010-05-12
forum: General Help
---

### Post by H0lyGanGs7eR on 2010-05-12
Hello I installed corectly the program, but when I start it, it starts to integrate to the kernel, I got error and this  is the log. HELP PLEASE!
```
May 12 16:04:07.612: app-139838623995648| Log for VMware Workstation pid=25181 version=7.0.0 build=build-203739 option=Release
May 12 16:04:07.612: app-139838623995648| The process is 64-bit.
May 12 16:04:07.612: app-139838623995648| Host codepage=UTF-8 encoding=UTF-8
May 12 16:04:07.612: app-139838623995648| Logging to /tmp/vmware-root/setup-25181.log
May 12 16:04:07.905: app-139838623995648| modconf query interface initialized
May 12 16:04:07.905: app-139838623995648| modconf library initialized
May 12 16:04:07.949: app-139838623995648| Your GCC version: 4.4
May 12 16:04:07.959: app-139838623995648| Your GCC version: 4.4
May 12 16:04:07.974: app-139838623995648| Your GCC version: 4.4
May 12 16:04:07.993: app-139838623995648| Your GCC version: 4.4
May 12 16:04:08.011: app-139838623995648| Your GCC version: 4.4
May 12 16:04:08.058: app-139838623995648| Trying to find a suitable PBM set for kernel 2.6.32-22-generic.
May 12 16:04:08.061: app-139838623995648| Trying to find a suitable PBM set for kernel 2.6.32-22-generic.
May 12 16:04:08.064: app-139838623995648| Trying to find a suitable PBM set for kernel 2.6.32-22-generic.
May 12 16:04:08.067: app-139838623995648| Trying to find a suitable PBM set for kernel 2.6.32-22-generic.
May 12 16:04:08.070: app-139838623995648| Trying to find a suitable PBM set for kernel 2.6.32-22-generic.
May 12 16:04:08.097: app-139838623995648| Trying to find a suitable PBM set for kernel 2.6.32-22-generic.
May 12 16:04:08.099: app-139838623995648| Trying to find a suitable PBM set for kernel 2.6.32-22-generic.
May 12 16:04:08.102: app-139838623995648| Trying to find a suitable PBM set for kernel 2.6.32-22-generic.
May 12 16:04:08.104: app-139838623995648| Trying to find a suitable PBM set for kernel 2.6.32-22-generic.
May 12 16:04:08.107: app-139838623995648| Trying to find a suitable PBM set for kernel 2.6.32-22-generic.
May 12 16:04:08.115: app-139838623995648| Your GCC version: 4.4
May 12 16:04:08.130: app-139838623995648| Your GCC version: 4.4
May 12 16:04:08.176: app-139838623995648| Trying to find a suitable PBM set for kernel 2.6.32-22-generic.
May 12 16:04:08.179: app-139838623995648| Trying to find a suitable PBM set for kernel 2.6.32-22-generic.
May 12 16:04:08.181: app-139838623995648| Trying to find a suitable PBM set for kernel 2.6.32-22-generic.
May 12 16:04:08.184: app-139838623995648| Trying to find a suitable PBM set for kernel 2.6.32-22-generic.
May 12 16:04:08.186: app-139838623995648| Trying to find a suitable PBM set for kernel 2.6.32-22-generic.
May 12 16:04:08.194: app-139838623995648| Your GCC version: 4.4
May 12 16:04:08.209: app-139838623995648| Your GCC version: 4.4
May 12 16:04:08.279: app-139838623995648| Trying to find a suitable PBM set for kernel 2.6.32-22-generic.
May 12 16:04:08.282: app-139838623995648| Trying to find a suitable PBM set for kernel 2.6.32-22-generic.
May 12 16:04:08.285: app-139838623995648| Trying to find a suitable PBM set for kernel 2.6.32-22-generic.
May 12 16:04:08.287: app-139838623995648| Trying to find a suitable PBM set for kernel 2.6.32-22-generic.
May 12 16:04:08.290: app-139838623995648| Trying to find a suitable PBM set for kernel 2.6.32-22-generic.
May 12 16:04:08.517: app-139838623995648| Trying to find a suitable PBM set for kernel 2.6.32-22-generic.
May 12 16:04:08.518: app-139838623995648| Building module vmmon.
May 12 16:04:08.518: app-139838623995648| Extracting the sources of the vmmon module.
May 12 16:04:08.564: app-139838623995648| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmmon-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.32-22-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.3
May 12 16:04:16.608: app-139838623995648| Installing module vmmon from /tmp/vmware-root/modules/vmmon.o.
May 12 16:04:16.609: app-139838623995648| Registering file: /usr/lib/vmware-installer/1.1/vmware-installer --register-file vmware-player-app regular /lib/modules/2.6.32-22-generic/misc/vmmon.o
May 12 16:04:17.425: app-139838623995648| Registering file: /usr/lib/vmware-installer/1.1/vmware-installer --register-file vmware-player-app regular /lib/modules/2.6.32-22-generic/misc/vmmon.ko
May 12 16:04:19.130: app-139838623995648| Trying to find a suitable PBM set for kernel 2.6.32-22-generic.
May 12 16:04:19.131: app-139838623995648| Building module vmnet.
May 12 16:04:19.131: app-139838623995648| Extracting the sources of the vmnet module.
May 12 16:04:19.148: app-139838623995648| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmnet-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.32-22-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.3
May 12 16:04:27.361: app-139838623995648| Failed to compile module vmnet!
May 12 16:04:27.367: app-139838623995648| Trying to find a suitable PBM set for kernel 2.6.32-22-generic.
May 12 16:04:27.368: app-139838623995648| Building module vmblock.
May 12 16:04:27.368: app-139838623995648| Extracting the sources of the vmblock module.
May 12 16:04:27.389: app-139838623995648| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmblock-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.32-22-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.3
May 12 16:04:33.422: app-139838623995648| Installing module vmblock from /tmp/vmware-root/modules/vmblock.o.
May 12 16:04:33.422: app-139838623995648| Registering file: /usr/lib/vmware-installer/1.1/vmware-installer --register-file vmware-player-app regular /lib/modules/2.6.32-22-generic/misc/vmblock.o
May 12 16:04:34.277: app-139838623995648| Registering file: /usr/lib/vmware-installer/1.1/vmware-installer --register-file vmware-player-app regular /lib/modules/2.6.32-22-generic/misc/vmblock.ko
May 12 16:04:36.059: app-139838623995648| Trying to find a suitable PBM set for kernel 2.6.32-22-generic.
May 12 16:04:36.059: app-139838623995648| Building module vmci.
May 12 16:04:36.059: app-139838623995648| Extracting the sources of the vmci module.
May 12 16:04:36.094: app-139838623995648| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmci-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.32-22-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.3
May 12 16:04:38.024: app-139838623995648| Failed to compile module vmci!
May 12 16:04:38.033: app-139838623995648| Trying to find a suitable PBM set for kernel 2.6.32-22-generic.
May 12 16:04:38.033: app-139838623995648| Building module vmci.
May 12 16:04:38.033: app-139838623995648| Extracting the sources of the vmci module.
May 12 16:04:38.051: app-139838623995648| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmci-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.32-22-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.3
May 12 16:04:38.962: app-139838623995648| Failed to compile module vmci!
```

---

### Post by H0lyGanGs7eR on 2010-05-12
Answer please!

---

### Post by cdenley on 2010-05-12
Use search function please!
[http://ubuntuforums.org/showthread.php?t=1382304](http://ubuntuforums.org/showthread.php?t=1382304)

---

### Post by hokage on 2010-05-27
As For workstation 7.1 and kernel package 2.6.32-22-generic there is a problem: the utsversion.h contains a wrong value. you need to change it to what vmware expects : 2.6.32-22.

sudo vi /lib/modules/2.6.32-22-generic/build/include/linux/utsrelease.h

should contain 

#define UTS_RELEASE "2.6.32-22-generic"

This is a bug in the ubuntu kernel headers package methink.

---

### Post by eris23 on 2010-06-04
Is there a way to get the modules to build with 2.6.35-020635rc1-generic from kernel-ppa?

---

### Post by tommytomtom on 2010-06-08
What I did to get it to work with kernel 2.6.35-rc1 was to remake the vmmon.tar package...

cd /usr/lib/vmware/modules/source
sudo mv vmmon.tar vmmon.tar.original
sudo mkdir tmp
cd tmp
sudo tar -xf ../vmmon.tar.original
cd vmmon-only/linux

... with a text editor edit the file iommu.c and replace:
iommu_map_range_array   with    iommu_map_range
iommu_unmap_range_array  with iommu_unmap_range

cd /usr/lib/vmware/modules/source/tmp
sudo tar -cf ../vmmon.tar vmmon-only

Now it will work. BUT, it will compile EACH time you start the workstation..
I would love to know how to fix it so it doesn't recompile each start-up.

---

### Post by dcstar on 2010-06-08
If people spent 5 minutes in the Virtualization forum they might get their VM problems fixed instead of wasting weeks in the wrong forum.

---

### Post by tommytomtom on 2010-06-08
> **dcstar said:**
> If people spent 5 minutes in the Virtualization forum they might get their VM problems fixed instead of wasting weeks in the wrong forum.
Very insightful and very unhelpful.  Where do they talk about kernel 2.6.35.  I couldn't find it...

---

### Post by rrfx on 2010-06-14
> **tommytomtom said:**
> Very insightful and very unhelpful.  Where do they talk about kernel 2.6.35.  I couldn't find it...

You are being very polite tommytomtom. David if you dont have anything helpful to add, then please refrain.

Back on topic, there is currently only one mention of this vmmon compilation problem on 64 bit kernel 2.6.35 in the official Vmware forums:

[http://communities.vmware.com/thread/272114]("http://communities.vmware.com/thread/272114")

The question is unanswered. 

In my searching, tommytomtom's answer was most helpful for what seems like a very similar issue. Using linux-image-2.6.35-2-generic from the kernel-ppa's with VMware-Player-3.1.0-261024.x86_64.bundle 

The source function calls to iommu_map_range and iommu_unmap_range in iommu.c need to have the '_range' suffix removed.

This worked for me:
```
cd /tmp
tar xvf /usr/lib/vmware/modules/source/vmmon.tar -C /tmp
perl -pi -e 's,_range,,' vmmon-only/linux/iommu.c
tar cvf /usr/lib/vmware/modules/source/vmmon.tar vmmon-only
vmplayer
```

---

### Post by devroute on 2010-08-20
this post has been helpful as i was having same issue but now i get this error sorry for stealing thread =p

```

Aug 20 01:55:04.389: app-140622668777216| Log for VMware Workstation pid=14281 version=7.1.1 build=build-282343 option=Release Aug 20 01:55:04.389: app-140622668777216| The process is 64-bit. Aug 20 01:55:04.389: app-140622668777216| Host codepage=UTF-8 encoding=UTF-8 Aug 20 01:55:04.389: app-140622668777216| Logging to /tmp/vmware-root/setup-14281.log Aug 20 01:55:04.477: app-140622668777216| modconf query interface initialized Aug 20 01:55:04.478: app-140622668777216| modconf library initialized Aug 20 01:55:04.494: app-140622668777216| Your GCC version: 4.4 Aug 20 01:55:04.497: app-140622668777216| Your GCC version: 4.4 Aug 20 01:55:04.503: app-140622668777216| Your GCC version: 4.4 Aug 20 01:55:04.510: app-140622668777216| Your GCC version: 4.4 Aug 20 01:55:04.515: app-140622668777216| Your GCC version: 4.4 Aug 20 01:55:04.532: app-140622668777216| Trying to find a suitable PBM set for kernel 2.6.35.2-custom. Aug 20 01:55:04.533: app-140622668777216| Trying to find a suitable PBM set for kernel 2.6.35.2-custom. Aug 20 01:55:04.535: app-140622668777216| Trying to find a suitable PBM set for kernel 2.6.35.2-custom. Aug 20 01:55:04.536: app-140622668777216| Trying to find a suitable PBM set for kernel 2.6.35.2-custom. Aug 20 01:55:04.538: app-140622668777216| Trying to find a suitable PBM set for kernel 2.6.35.2-custom. Aug 20 01:55:04.547: app-140622668777216| Trying to find a suitable PBM set for kernel 2.6.35.2-custom. Aug 20 01:55:04.549: app-140622668777216| Trying to find a suitable PBM set for kernel 2.6.35.2-custom. Aug 20 01:55:04.551: app-140622668777216| Trying to find a suitable PBM set for kernel 2.6.35.2-custom. Aug 20 01:55:04.552: app-140622668777216| Trying to find a suitable PBM set for kernel 2.6.35.2-custom. Aug 20 01:55:04.554: app-140622668777216| Trying to find a suitable PBM set for kernel 2.6.35.2-custom. Aug 20 01:55:04.556: app-140622668777216| Your GCC version: 4.4 Aug 20 01:55:04.561: app-140622668777216| Your GCC version: 4.4 Aug 20 01:55:04.579: app-140622668777216| Trying to find a suitable PBM set for kernel 2.6.35.2-custom. Aug 20 01:55:04.582: app-140622668777216| Trying to find a suitable PBM set for kernel 2.6.35.2-custom. Aug 20 01:55:04.584: app-140622668777216| Trying to find a suitable PBM set for kernel 2.6.35.2-custom. Aug 20 01:55:04.585: app-140622668777216| Trying to find a suitable PBM set for kernel 2.6.35.2-custom. Aug 20 01:55:04.587: app-140622668777216| Trying to find a suitable PBM set for kernel 2.6.35.2-custom. Aug 20 01:55:04.589: app-140622668777216| Your GCC version: 4.4 Aug 20 01:55:04.594: app-140622668777216| Your GCC version: 4.4 Aug 20 01:55:04.618: app-140622668777216| Trying to find a suitable PBM set for kernel 2.6.35.2-custom. Aug 20 01:55:04.619: app-140622668777216| Trying to find a suitable PBM set for kernel 2.6.35.2-custom. Aug 20 01:55:04.621: app-140622668777216| Trying to find a suitable PBM set for kernel 2.6.35.2-custom. Aug 20 01:55:04.622: app-140622668777216| Trying to find a suitable PBM set for kernel 2.6.35.2-custom. Aug 20 01:55:04.624: app-140622668777216| Trying to find a suitable PBM set for kernel 2.6.35.2-custom. Aug 20 01:55:04.905: app-140622668777216| Trying to find a suitable PBM set for kernel 2.6.35.2-custom. Aug 20 01:55:04.905: app-140622668777216| Building module vmmon. Aug 20 01:55:04.905: app-140622668777216| Extracting the sources of the vmmon module. Aug 20 01:55:04.912: app-140622668777216| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmmon-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.35.2-custom/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.3 Aug 20 01:55:08.857: app-140622668777216| Installing module vmmon from /tmp/vmware-root/modules/vmmon.o. Aug 20 01:55:08.859: app-140622668777216| Registering file: /usr/lib/vmware-installer/1.1/vmware-installer --register-file vmware-player-app regular /lib/modules/2.6.35.2-custom/misc/vmmon.o Aug 20 01:55:09.382: app-140622668777216| Registering file: /usr/lib/vmware-installer/1.1/vmware-installer --register-file vmware-player-app regular /lib/modules/2.6.35.2-custom/misc/vmmon.ko Aug 20 01:55:10.125: app-140622668777216| Trying to find a suitable PBM set for kernel 2.6.35.2-custom. Aug 20 01:55:10.125: app-140622668777216| Building module vmnet. Aug 20 01:55:10.125: app-140622668777216| Extracting the sources of the vmnet module. Aug 20 01:55:10.131: app-140622668777216| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmnet-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.35.2-custom/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.3 Aug 20 01:55:15.203: app-140622668777216| Installing module vmnet from /tmp/vmware-root/modules/vmnet.o. Aug 20 01:55:15.205: app-140622668777216| Registering file: /usr/lib/vmware-installer/1.1/vmware-installer --register-file vmware-player-app regular /lib/modules/2.6.35.2-custom/misc/vmnet.o Aug 20 01:55:15.628: app-140622668777216| Registering file: /usr/lib/vmware-installer/1.1/vmware-installer --register-file vmware-player-app regular /lib/modules/2.6.35.2-custom/misc/vmnet.ko Aug 20 01:55:16.358: app-140622668777216| Trying to find a suitable PBM set for kernel 2.6.35.2-custom. Aug 20 01:55:16.358: app-140622668777216| Building module vmblock. Aug 20 01:55:16.358: app-140622668777216| Extracting the sources of the vmblock module. Aug 20 01:55:16.364: app-140622668777216| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmblock-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.35.2-custom/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.3 Aug 20 01:55:19.406: app-140622668777216| Installing module vmblock from /tmp/vmware-root/modules/vmblock.o. Aug 20 01:55:19.407: app-140622668777216| Registering file: /usr/lib/vmware-installer/1.1/vmware-installer --register-file vmware-player-app regular /lib/modules/2.6.35.2-custom/misc/vmblock.o Aug 20 01:55:19.823: app-140622668777216| Registering file: /usr/lib/vmware-installer/1.1/vmware-installer --register-file vmware-player-app regular /lib/modules/2.6.35.2-custom/misc/vmblock.ko Aug 20 01:55:20.546: app-140622668777216| Trying to find a suitable PBM set for kernel 2.6.35.2-custom. Aug 20 01:55:20.547: app-140622668777216| Building module vmci. Aug 20 01:55:20.547: app-140622668777216| Extracting the sources of the vmci module. Aug 20 01:55:20.552: app-140622668777216| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmci-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.35.2-custom/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.3 Aug 20 01:55:21.505: app-140622668777216| Failed to compile module vmci! Aug 20 01:55:21.508: app-140622668777216| Trying to find a suitable PBM set for kernel 2.6.35.2-custom. Aug 20 01:55:21.508: app-140622668777216| Building module vmci. Aug 20 01:55:21.508: app-140622668777216| Extracting the sources of the vmci module. Aug 20 01:55:21.515: app-140622668777216| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmci-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.35.2-custom/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.3 Aug 20 01:55:21.916: app-140622668777216| Failed to compile module vmci!

```

---

### Post by enkrypt3d on 2011-02-20
just use the 32bit installer man theres no need to really install vmware 64bit unless u absolutely have to run 64bit guest VM's?

---

