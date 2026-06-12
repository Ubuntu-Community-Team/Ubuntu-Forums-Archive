---
title: "help with graphics"
date: 2010-07-06
forum: General Help
---

### Post by lordofhumankind on 2010-07-06
I put Ubuntu on my grandmother's Dimension 2400. I am still working on the set up, and have two problems.
The first (and more pressing) is that when left alone for a while the whole system hangs going through a cycle of blank screen, white lines, putting the monitor into power saver, and then turning it back on.

I think I found a fix for this but don't know how to implement it.
[https://bugs.freedesktop.org/attachment.cgi?id=36587](https://bugs.freedesktop.org/attachment.cgi?id=36587)

The second problem is that I cannot enable desktop effects. I tried to install the Intel driver, but was told that the agpgart module did not compile, and then that the kernel modules did not compile. Here is the dri.log
```
make -C /lib/modules/2.6.32-23-generic/build SUBDIRS=/home/georgia/dripkg/agpgart-2.0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-23-generic'
  CC [M]  /home/georgia/dripkg/agpgart-2.0/backend.o
/home/georgia/dripkg/agpgart-2.0/backend.c:68: error: conflicting types for ‘agp_backend_acquire’
include/linux/agp_backend.h:108: note: previous declaration of ‘agp_backend_acquire’ was here
/home/georgia/dripkg/agpgart-2.0/backend.c:77: error: conflicting types for ‘agp_backend_acquire’
include/linux/agp_backend.h:108: note: previous declaration of ‘agp_backend_acquire’ was here
/home/georgia/dripkg/agpgart-2.0/backend.c:88: error: conflicting types for ‘agp_backend_release’
include/linux/agp_backend.h:109: note: previous declaration of ‘agp_backend_release’ was here
/home/georgia/dripkg/agpgart-2.0/backend.c:93: error: conflicting types for ‘agp_backend_release’
include/linux/agp_backend.h:109: note: previous declaration of ‘agp_backend_release’ was here
/home/georgia/dripkg/agpgart-2.0/backend.c:220: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘drm_agp’
/home/georgia/dripkg/agpgart-2.0/backend.c: In function ‘agp_add_bridge’:
/home/georgia/dripkg/agpgart-2.0/backend.c:281: error: implicit declaration of function ‘inter_module_register’
/home/georgia/dripkg/agpgart-2.0/backend.c:281: error: ‘drm_agp’ undeclared (first use in this function)
/home/georgia/dripkg/agpgart-2.0/backend.c:281: error: (Each undeclared identifier is reported only once
/home/georgia/dripkg/agpgart-2.0/backend.c:281: error: for each function it appears in.)
/home/georgia/dripkg/agpgart-2.0/backend.c: In function ‘agp_remove_bridge’:
/home/georgia/dripkg/agpgart-2.0/backend.c:301: error: implicit declaration of function ‘inter_module_unregister’
make[2]: *** [/home/georgia/dripkg/agpgart-2.0/backend.o] Error 1
make[1]: *** [_module_/home/georgia/dripkg/agpgart-2.0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-23-generic'
make: *** [default] Error 2
make -f Makefile.linux DRM_MODULES=gdg.ko modules
make[1]: Entering directory `/home/georgia/dripkg/drm'
make -C /lib/modules/2.6.32-23-generic/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.32-23-generic'
rm: cannot remove `/home/georgia/dripkg/drm/.tmp_versions/CVS': Is a directory
make[2]: *** [crmodverdir] Error 1
make[2]: Leaving directory `/usr/src/linux-headers-2.6.32-23-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/georgia/dripkg/drm'
make: *** [gdg.ko] Error 2 
```

---

### Post by bigsmitty64 on 2010-07-06
First off, my firefox doesn't like that link you provided.
 
Any bugs can be found at [URL="https://bugs.launchpad.net/ubuntu"]HERE
[/URL] 
People are gonna want more info: 

Ram= how much
Video= nVidia, Ati, 
Version of Ubuntu= 10.04, or 9.10, or 8.blah blah
64 bit or 32 bit= ?

As far as drivers go you should go to the top panel, click System>Administration>Hardware Drivers. It will look for the latest drivers for you, then choose the recommended one, and hopefully you can use that and enable desktop effects.
I have never had to look elsewhere for drivers. But thats my case, yours may be different.

---

### Post by lordofhumankind on 2010-07-06
My sudo lshw 
Amounts to 2 gigabytes of ram and intel 82845g chip. 
 ```
  description: Space-saving Computer
    product: Dimension 2400
    vendor: Dell Computer Corporation
    serial: 1GG6941
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: administrator_password=enabled boot=normal chassis=space-saving cpus=1 power-on_password=enabled uuid=44454C4C-4700-1047-8036-B1C04F393431
  *-core
       description: Motherboard
       product: 0C2425
       vendor: Dell Computer Corp.
       physical id: 0
       version: A01
       serial: ..CN137403CF01IJ.
     *-firmware
          description: BIOS
          vendor: Dell Computer Corporation
          physical id: 0
          version: A05 (12/02/2003)
          size: 64KiB
          capacity: 448KiB
          capabilities: pci pnp apm upgrade shadowing escd cdboot bootselect edd int13floppytoshiba int5printscreen int9keyboard int14serial int17printer acpi usb ls120boot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.53GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 15.2.9
          slot: Microprocessor
          size: 2533MHz
          capacity: 3600MHz
          width: 32 bits
          clock: 533MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 8KiB
             capacity: 8KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 512KiB
             capacity: 512KiB
             capabilities: internal varies unified
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM SDRAM Synchronous 333 MHz (3.0 ns)
             physical id: 0
             slot: DIMM_1
             size: 1GiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:1
             description: DIMM SDRAM Synchronous 333 MHz (3.0 ns)
             physical id: 1
             slot: DIMM_2
             size: 1GiB
             width: 64 bits
             clock: 333MHz (3.0ns)
     *-pci
          description: Host bridge
          product: 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 01
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:f0000000-f7ffffff(prefetchable)
        *-display UNCLAIMED
             description: VGA compatible controller
             product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:e8000000-efffffff(prefetchable) memory:feb80000-febfffff
        *-usb:0
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:ff80(size=32)
        *-usb:1
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:ff60(size=32)
        *-usb:2
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:ff40(size=32)
        *-usb:3
             description: USB Controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:ffa80800-ffa80bff
        *-pci
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
             resources: ioport:d000(size=4096) memory:fe900000-feafffff memory:80000000-800fffff(prefetchable)
           *-communication
                description: Modem
                product: BCM4212 v.90 56k modem
                vendor: Broadcom Corporation
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=serial latency=64
                resources: irq:17 memory:fe9fd000-fe9fdfff ioport:dff0(size=16)
           *-network
                description: Ethernet interface
                product: BCM4401 100Base-T
                vendor: Broadcom Corporation
                physical id: 9
                bus info: pci@0000:01:09.0
                logical name: eth0
                version: 01
                serial: 00:0d:56:cb:07:6e
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list rom ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=24.180.169.118 latency=64 link=yes multicast=yes port=twisted pair speed=100MB/s
                resources: irq:17 memory:fe9fe000-fe9fffff memory:80000000-80003fff(prefetchable)
        *-isa
             description: ISA bridge
             product: 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801DB (ICH4) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16) memory:feb7fc00-feb7ffff
           *-disk
                description: ATA Disk
                product: Maxtor 6Y080L0
                vendor: Maxtor
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: YAR4
                serial: Y2DELDJE
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=9dc96e9e
              *-volume:0
                   description: Windows FAT volume
                   vendor: Dell 4.1
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: FAT16
                   serial: 07d4-0204
                   size: 31MiB
                   capacity: 31MiB
                   capabilities: primary fat initialized
                   configuration: FATs=2 filesystem=fat label=DellUtility
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 3.1
                   serial: cc4925c4-1fa0-6a43-bb6e-a6e140a44d47
                   size: 45GiB
                   capacity: 45GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2004-02-04 18:53:59 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
              *-volume:2
                   description: Extended partition
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   size: 28GiB
                   capacity: 28GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /
                      capacity: 27GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 1260MiB
                      capabilities: nofs
           *-cdrom
                description: DVD reader
                product: RW/DVD GCC-4480B
                vendor: HL-DT-ST
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: C104
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:eda0(size=32)
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0
             resources: irq:17 ioport:ee00(size=256) ioport:edc0(size=64) memory:feb7fa00-feb7fbff memory:feb7f900-feb7f9ff
     *-scsi
          physical id: 1
          bus info: usb@1:2
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: Photosmart C4280
             vendor: HP
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
             version: 1.00
             capabilities: removable
             configuration: ansiversion=5
           *-medium
                physical id: 0
                logical name: /dev/sdb
```No graphics drivers are suggested by the hardware drivers utility, so I went to the Intel website and downloaded the Linux drivers appropriate to my card. The installation then gave the error listed in my previous post.

If the link is an issue, here are its contents. ```
From e469048a0be109b6354cc25728b83be3f8bcfbc5 Mon Sep 17 00:00:00 2001
From: Jesse Barnes <jbarnes@virtuousgeek.org>
Date: Mon, 28 Jun 2010 15:54:33 -0700
Subject: [PATCH 1/2] OS support: fix writeable client vs IgnoreClient behavior

When ResetCurrentRequest is called, or IgnoreClient is called when a
client has input pending, IgnoredClientsWithInput will be set.  However,
a subsequent IgnoreClient request will clear the client fd from that fd
set, potentially causing the client to hang.

So leave the client fd bit in IgnoredClientsWithInput set if needed and
clear it in AttendClient if we used it.

Fixes https://bugs.freedesktop.org/show_bug.cgi?id=27035.

Signed-off-by: Jesse Barnes <jbarnes@virtuousgeek.org>
---
 os/connection.c |   12 ++++++------
 1 files changed, 6 insertions(+), 6 deletions(-)

diff --git a/os/connection.c b/os/connection.c
index 61ba72a..a3665b1 100644
--- a/os/connection.c
+++ b/os/connection.c
@@ -1152,8 +1152,6 @@ IgnoreClient (ClientPtr client)
     {
         if (FD_ISSET (connection, &ClientsWithInput))
         FD_SET(connection, &IgnoredClientsWithInput);
-        else
-        FD_CLR(connection, &IgnoredClientsWithInput);
         FD_CLR(connection, &ClientsWithInput);
         FD_CLR(connection, &AllSockets);
         FD_CLR(connection, &AllClients);
@@ -1163,8 +1161,6 @@ IgnoreClient (ClientPtr client)
     {
         if (FD_ISSET (connection, &SavedClientsWithInput))
         FD_SET(connection, &IgnoredClientsWithInput);
-        else
-        FD_CLR(connection, &IgnoredClientsWithInput);
     FD_CLR(connection, &SavedClientsWithInput);
     FD_CLR(connection, &SavedAllSockets);
     FD_CLR(connection, &SavedAllClients);
@@ -1187,15 +1183,19 @@ AttendClient (ClientPtr client)
         FD_SET(connection, &AllClients);
         FD_SET(connection, &AllSockets);
     FD_SET(connection, &LastSelectMask);
-        if (FD_ISSET (connection, &IgnoredClientsWithInput))
+        if (FD_ISSET (connection, &IgnoredClientsWithInput)) {
         FD_SET(connection, &ClientsWithInput);
+        FD_CLR(connection, &IgnoredClientsWithInput);
+    }
     }
     else
     {
     FD_SET(connection, &SavedAllClients);
     FD_SET(connection, &SavedAllSockets);
-    if (FD_ISSET(connection, &IgnoredClientsWithInput))
+    if (FD_ISSET(connection, &IgnoredClientsWithInput)) {
         FD_SET(connection, &SavedClientsWithInput);
+        FD_CLR(connection, &IgnoredClientsWithInput);
+    }
     }
 }
 
-- 
1.6.6.1

```
No graphics drivers are suggested by the hardware drivers utility, so I  went to the Intel website and downloaded the Linux drivers appropriate  to my card. The installation then gave the error listed in my previous  post.

---

### Post by lordofhumankind on 2010-07-06
I leave Thursday, and if this isn't fixed by then then I will have to remove the Linux partition.

---

### Post by lordofhumankind on 2010-07-07
bump

---

### Post by lordofhumankind on 2010-07-07
My problem is fairly simple. What language is this code, and if it isn't just a program where do I put it. 
```
From e469048a0be109b6354cc25728b83be3f8bcfbc5 Mon Sep 17 00:00:00 2001
From: Jesse Barnes <jbarnes@virtuousgeek.org>
Date: Mon, 28 Jun 2010 15:54:33 -0700
Subject: [PATCH 1/2] OS support: fix writeable client vs IgnoreClient behavior

When ResetCurrentRequest is called, or IgnoreClient is called when a
client has input pending, IgnoredClientsWithInput will be set.  However,
a subsequent IgnoreClient request will clear the client fd from that fd
set, potentially causing the client to hang.

So leave the client fd bit in IgnoredClientsWithInput set if needed and
clear it in AttendClient if we used it.

Fixes https://bugs.freedesktop.org/show_bug.cgi?id=27035.

Signed-off-by: Jesse Barnes <jbarnes@virtuousgeek.org>
---
 os/connection.c |   12 ++++++------
 1 files changed, 6 insertions(+), 6 deletions(-)

diff --git a/os/connection.c b/os/connection.c
index 61ba72a..a3665b1 100644
--- a/os/connection.c
+++ b/os/connection.c
@@ -1152,8 +1152,6 @@ IgnoreClient (ClientPtr client)
     {
         if (FD_ISSET (connection, &ClientsWithInput))
         FD_SET(connection, &IgnoredClientsWithInput);
-        else
-        FD_CLR(connection, &IgnoredClientsWithInput);
         FD_CLR(connection, &ClientsWithInput);
         FD_CLR(connection, &AllSockets);
         FD_CLR(connection, &AllClients);
@@ -1163,8 +1161,6 @@ IgnoreClient (ClientPtr client)
     {
         if (FD_ISSET (connection, &SavedClientsWithInput))
         FD_SET(connection, &IgnoredClientsWithInput);
-        else
-        FD_CLR(connection, &IgnoredClientsWithInput);
     FD_CLR(connection, &SavedClientsWithInput);
     FD_CLR(connection, &SavedAllSockets);
     FD_CLR(connection, &SavedAllClients);
@@ -1187,15 +1183,19 @@ AttendClient (ClientPtr client)
         FD_SET(connection, &AllClients);
         FD_SET(connection, &AllSockets);
     FD_SET(connection, &LastSelectMask);
-        if (FD_ISSET (connection, &IgnoredClientsWithInput))
+        if (FD_ISSET (connection, &IgnoredClientsWithInput)) {
         FD_SET(connection, &ClientsWithInput);
+        FD_CLR(connection, &IgnoredClientsWithInput);
+    }
     }
     else
     {
     FD_SET(connection, &SavedAllClients);
     FD_SET(connection, &SavedAllSockets);
-    if (FD_ISSET(connection, &IgnoredClientsWithInput))
+    if (FD_ISSET(connection, &IgnoredClientsWithInput)) {
         FD_SET(connection, &SavedClientsWithInput);
+        FD_CLR(connection, &IgnoredClientsWithInput);
+    }
     }
 }
 
-- 
1.6.6.1
```

The graphics drivers are just the icing. 
And I am leaving tomorrow, but I will still be able to either tell my grandparents what to do by phone or do it by ssh.

---

### Post by steve_dupuis on 2010-07-07
Hi ..

??? I've installed Ubuntu (now 10.04) on several machines and have't had any problems except for my new laptop with new nvidia graphics. I used the alternative installation CD for it and it worked fine.

The install should be vanilla for your gm's laptop. I've never had to compile any code to get to a working system.

What version of Ubuntu are you trying to install? Does the installation crash, or does it garble the display manager when it boots up?

---

### Post by hikaricore on 2010-07-07
> **steve_dupuis said:**
> Hi ..

??? I've installed Ubuntu (now 10.04) on several machines and have't had any problems except for my new laptop with new nvidia graphics. I used the alternative installation CD for it and it worked fine.

The install should be vanilla for your gm's laptop. I've never had to compile any code to get to a working system.

What version of Ubuntu are you trying to install? Does the installation crash, or does it garble the display manager when it boots up?

You realize the OP is asking for help patching and compiling INTEL display drivers and at no point mentioned nvidia right?

---

