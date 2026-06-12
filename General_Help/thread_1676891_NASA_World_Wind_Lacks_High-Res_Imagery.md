---
title: "NASA World Wind Lacks High-Res Imagery"
date: 2011-01-27
forum: General Help
---

### Post by NearlyALaugh on 2011-01-27
Hi there,

NASA World Wind doesn't appear to be downloading any high-resolution satellite imagery, and when I deselect the "Blue Marble" layer, the globe disappears. (See attached screenshots.) Does anybody have experience running World Wind and getting the detailed layers to show up?

I have the same problem on separate computers running Ubuntu 10.04 and Debian 6.0. Here is their setup:

```
$ lsb_release -ds
Ubuntu 10.04.1 LTS

$ uname -a
Linux ubuntu-desktop 2.6.32-27-generic #49-Ubuntu SMP Wed Dec 1 23:52:12 UTC 2010 i686 GNU/Linux

$ java -version
java version "1.6.0_20"
OpenJDK Runtime Environment (IcedTea6 1.9.4) (6b20-1.9.4-0ubuntu1~10.04.1)
OpenJDK Client VM (build 19.0-b09, mixed mode, sharing)

$ dpkg --status worldwind | grep Version
Version: 0.5.0-7

$ lshw -C video
WARNING: you should run this program as super-user.
  *-display               
       description: VGA compatible controller
       product: 82915G/GV/910GL Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 04
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:fbe00000-fbe7ffff ioport:cc00(size=8) memory:d0000000-dfffffff(prefetchable) memory:fbdc0000-fbdfffff

``````
$ lsb_release -ds
Debian GNU/Linux 6.0 (squeeze)

$ uname -a
Linux debian 2.6.32-5-amd64 #1 SMP Wed Jan 12 03:40:32 UTC 2011 x86_64
GNU/Linux

$ java -version
java version "1.6.0_18"
OpenJDK Runtime Environment (IcedTea6 1.8.3) (6b18-1.8.3-2)
OpenJDK 64-Bit Server VM (build 16.0-b13, mixed mode)

$ dpkg --status worldwind | grep Version
Version: 0.5.0-8

$ lshw -C video
WARNING: you should run this program as super-user.
  *-display
       description: VGA compatible controller
       product: Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:33 memory:d0000000-d03fffff
memory:c0000000-cfffffff(prefetchable) ioport:5050(size=8)

```


Best Wishes~

---

