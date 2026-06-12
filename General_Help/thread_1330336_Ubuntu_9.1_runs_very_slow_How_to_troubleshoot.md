---
title: "Ubuntu 9.1 runs very slow How to troubleshoot ?"
date: 2009-11-18
forum: General Help
---

### Post by zonemikel on 2009-11-18
I have a new install of 9.1 and have reinstalled it a few times. I'm running it on a system this is the lshw output

> 
    description: Desktop Computer
    product: M848A
    vendor: ECS
    version: 5.0
    serial: 00000000
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: chassis=desktop
  *-core
       description: Motherboard
       product: M848A
       vendor: ECS
       physical id: 0
       version: 5.0
       serial: 00000000
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 07.00T (04/02/01)
          size: 64KiB
          capacity: 192KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Athlon(tm) XP 2500+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 6.10.0
          slot: Slot-1
          size: 1833MHz
          width: 32 bits
          clock: 166MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow up
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: Internal Cache
             size: 128KiB
             capacity: 1MiB
             capabilities: synchronous internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: Internal Cache
             size: 512KiB
             capacity: 1MiB
             capabilities: synchronous internal write-back unified
     *-memory
          description: System memory
          physical id: 1
          size: 255MiB
     *-pci
          description: Host bridge
          product: 746 Host
          vendor: Silicon Integrated Systems [SiS]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 10
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-sis
          resources: irq:0 memory:d0000000-d7ffffff
        *-pci
             description: PCI bridge
             product: SG86C202
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
             resources: memory:cbd00000-cfefffff memory:aba00000-cbbfffff(prefetchable)
           *-display
                description: VGA compatible controller
                product: NV44A [GeForce 6200]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 bus_master cap_list rom
                configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5
                resources: irq:16 memory:ce000000-ceffffff memory:b0000000-bfffffff(prefetchable) memory:cd000000-cdffffff memory:cfee0000-cfefffff(prefetchable)
        *-isa
             description: ISA bridge
             product: SiS963 [MuTIOL Media IO]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 25
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-serial UNCLAIMED
             description: SMBus
             product: SiS961/2 SMBus Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 00
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:c00(size=32)
        *-ide
             description: IDE interface
             product: 5513 [IDE]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.5
             bus info: pci@0000:00:02.5
             logical name: scsi0
             logical name: scsi1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=pata_sis latency=128
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ff00(size=16)
           *-disk:0
                description: ATA Disk
                product: WDC WD800BB-56JK
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 05.0
                serial: WD-WCAMD6831631
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=aa06c6e2
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: a798520b-3908-498d-add7-89cd35ebcf3e
                   size: 5020MiB
                   capacity: 5020MiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2009-11-07 05:01:41 filesystem=ext4 lastmountpoint=/&#1843;&#65533;u&#65533;&#65533;&#65533;&#65533;&#65533;\&#960;w&#924;&#1949;&#65533;9&#65533;&#65533;&#65533;I&#65533;&#65533;I&#65533;u&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#1016;&#1949;&#981;&#65533;&#65533;u&#65533;&#65533;0)&&#65533;J modified=2009-11-17 21:20:04 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2009-11-17 21:52:14 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 713MiB
                   capacity: 713MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 713MiB
                      capabilities: nofs
           *-disk:1
                description: ATA Disk
                product: Hitachi HDS72161
                vendor: Hitachi
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/sdb
                version: P22O
                serial: PV2300Z2R1550D
                size: 153GiB (164GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=9eb99eb9
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: /dev/sdb1
                   version: 1.0
                   serial: 37ec6777-8faf-4228-a18c-471a79d3245d
                   size: 20GiB
                   capacity: 20GiB
                   capabilities: primary journaled extended_attributes large_files ext3 ext2 initialized
                   configuration: created=2009-10-18 21:14:15 filesystem=ext3 modified=2009-11-17 20:59:01 mounted=2009-11-17 20:53:49 state=clean
              *-volume:1
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 4
                   bus info: scsi@1:0.0.0,4
                   logical name: /dev/sdb4
                   logical name: /mnt/sdb4
                   version: 1.0
                   serial: 468ccf5d-fae6-417a-8e58-655ffd7f07e2
                   size: 132GiB
                   capacity: 132GiB
                   capabilities: primary journaled extended_attributes large_files recover ext3 ext2 initialized
                   configuration: created=2009-09-11 18:52:33 filesystem=ext3 modified=2009-11-17 22:02:33 mount.fstype=ext3 mount.options=rw,relatime,errors=continue,data=writeback mounted=2009-11-17 22:02:33 state=mounted
           *-cdrom
                description: CD-R/CD-RW writer
                physical id: 0.1.0
                bus info: scsi@1:0.1.0
                logical name: /dev/cdrom1
                logical name: /dev/cdrw1
                logical name: /dev/scd0
                logical name: /dev/sr0
                capabilities: audio cd-r cd-rw
                configuration: status=nodisc
        *-multimedia
             description: Multimedia audio controller
             product: AC'97 Sound Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.7
             bus info: pci@0000:00:02.7
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=64 maxlatency=11 mingnt=52
             resources: irq:18 ioport:dc00(size=256) ioport:d800(size=128)
        *-usb:0
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80
             resources: irq:20 memory:cfffd000-cfffdfff
        *-usb:1
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.1
             bus info: pci@0000:00:03.1
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80
             resources: irq:21 memory:cfffe000-cfffefff
        *-usb:2
             description: USB Controller
             product: USB 2.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.2
             bus info: pci@0000:00:03.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ehci_hcd latency=64 maxlatency=80
             resources: irq:23 memory:cffff000-cfffffff
        *-network:0
             description: Ethernet interface
             product: SiS900 PCI Fast Ethernet
             vendor: Silicon Integrated Systems [SiS]
             physical id: 4
             bus info: pci@0000:00:04.0
             logical name: eth0
             version: 91
             serial: 00:1e:90:c9:5f:5e
             size: 10MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=half ip=10.0.2.1 latency=64 link=no maxlatency=11 mingnt=52 multicast=yes port=MII speed=10MB/s
             resources: irq:19 ioport:d400(size=256) memory:cfffc000-cfffcfff memory:cffc0000-cffdffff(prefetchable)
        *-network:1
             description: Ethernet interface
             product: RTL-8169 Gigabit Ethernet
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: 9
             bus info: pci@0000:00:09.0
             logical name: eth1
             version: 10
             serial: 00:0e:2e:06:ed:01
             size: 100MB/s
             capacity: 1GB/s
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.200 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
             resources: irq:17 ioport:d000(size=256) memory:cfffbf00-cfffbfff memory:cffe0000-cffeffff(prefetchable)
        *-network:2 DISABLED
             description: Ethernet interface
             product: RTL8139 Ethernet
             vendor: D-Link System Inc
             physical id: a
             bus info: pci@0000:00:0a.0
             logical name: eth2
             version: 10
             serial: 00:05:5d:42:63:82
             size: 10MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
             resources: irq:18 ioport:cc00(size=256) memory:10000000-100000ff
        *-network:3
             description: Ethernet interface
             product: 3c905C-TX/TX-M [Tornado]
             vendor: 3Com Corporation
             physical id: b
             bus info: pci@0000:00:0b.0
             logical name: eth3
             version: 6c
             serial: 00:50:04:ad:3a:30
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=full ip=98.195.221.139 latency=64 link=yes maxlatency=10 mingnt=10 multicast=yes port=MII speed=100MB/s
             resources: irq:17 ioport:c800(size=128) memory:cfffbd80-cfffbdff memory:cffa0000-cffbffff(prefetchable)



This system is a nfs,web,router,mysql server so it is doing a lot. My old server did all that also it was a old p3@1ghz running 9.04 and it ran like a champ, granted it did have 3x more memory.
The most noticable slow downs are logging in and such, from the time you type your password to the time it actually displays everything takes a long time. 

When I look into htop i see multiple mysql and web is that normal ? Like right now there are 10 processes that are for "/usr/sbin/apache2 -k start" and there are always tons for mysql also. 

The system will even kill mysql automatically sometimes saying it does not have enough memory ? And i often get this error printed to my console

> ERROR 1045 (28000): Access denied for user 'debian-sys-maint'@'localhost' (using password: YES)

This is dmesg of it killing process because of lack of memory ? 
> 
[32363.917342] Mem-Info:
[32363.917345] DMA per-cpu:
[32363.917348] CPU    0: hi:    0, btch:   1 usd:   0
[32363.917350] Normal per-cpu:
[32363.917353] CPU    0: hi:   90, btch:  15 usd:  70
[32363.917359] Active_anon:26961 active_file:147 inactive_anon:26280
[32363.917360]  inactive_file:149 unevictable:0 dirty:0 writeback:0 unstable:0
[32363.917362]  free:743 slab:2617 mapped:141 pagetables:860 bounce:0
[32363.917369] DMA free:1072kB min:120kB low:148kB high:180kB active_anon:4924kB inactive_anon:1968kB active_file:28kB inactive_file:16kB unevictable:0kB present:15804kB pages_scanned:16 all_unreclaimable? no
[32363.917374] lowmem_reserve[]: 0 238 238 238
[32363.917382] Normal free:1900kB min:1912kB low:2388kB high:2868kB active_anon:102920kB inactive_anon:103152kB active_file:560kB inactive_file:580kB unevictable:0kB present:243776kB pages_scanned:896 all_unreclaimable? no
[32363.917387] lowmem_reserve[]: 0 0 0 0
[32363.917391] DMA: 20*4kB 2*8kB 1*16kB 0*32kB 1*64kB 1*128kB 1*256kB 1*512kB 0*1024kB 0*2048kB 0*4096kB = 1072kB
[32363.917403] Normal: 343*4kB 30*8kB 6*16kB 4*32kB 1*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 1900kB
[32363.917415] 412 total pagecache pages
[32363.917417] 0 pages in swap cache
[32363.917420] Swap cache stats: add 0, delete 0, find 0/0
[32363.917422] Free swap  = 0kB
[32363.917424] Total swap = 0kB
[32363.921122] 65504 pages RAM
[32363.921127] 0 pages HighMem
[32363.921129] 2866 pages reserved
[32363.921131] 5485 pages shared
[32363.921133] 60757 pages non-shared
[32363.921139] Out of memory: kill process 2365 (mysqld) score 37225 or a child
[32363.921220] Killed process 2365 (mysqld)
[32367.693152] type=1503 audit(1258545091.262:29): operation="open" pid=2376 parent=1199 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[32790.960424] rtorrent invoked oom-killer: gfp_mask=0x201da, order=0, oomkilladj=0
[32790.960435] rtorrent cpuset=/ mems_allowed=0
[32790.960442] Pid: 2043, comm: rtorrent Tainted: P           2.6.31-14-generic-pae #48-Ubuntu
[32790.960446] Call Trace:
[32790.960465]  [<c01b79bf>] oom_kill_process+0x9f/0x250
[32790.960471]  [<c01b7fce>] ? select_bad_process+0xbe/0xf0
[32790.960476]  [<c01b8051>] __out_of_memory+0x51/0xa0
[32790.960565]  [<c01b80f3>] out_of_memory+0x53/0xb0
[32790.960571]  [<c01ba3ae>] __alloc_pages_slowpath+0x42e/0x480
[32790.960577]  [<c01ba50f>] __alloc_pages_nodemask+0x10f/0x120
[32790.960583]  [<c01bcfc2>] __do_page_cache_readahead+0xe2/0x190
[32790.960588]  [<c01bd091>] ra_submit+0x21/0x30
[32790.960592]  [<c01b48d0>] do_sync_mmap_readahead+0x90/0xc0
[32790.960596]  [<c01b5bfd>] ? find_get_page+0x1d/0x90
[32790.960601]  [<c01b6aa6>] filemap_fault+0x316/0x340
[32790.960607]  [<c012eb77>] ? kmap_atomic_prot+0x47/0x100
[32790.960613]  [<c01cda87>] __do_fault+0x47/0x4d0
[32790.960617]  [<c01cee83>] handle_mm_fault+0x193/0x4a0
[32790.960623]  [<c04931e6>] ? sys_send+0x36/0x40
[32790.960633]  [<c0578ab8>] do_page_fault+0x148/0x380
[32790.960637]  [<c0578970>] ? do_page_fault+0x0/0x380
[32790.960641]  [<c0576963>] error_code+0x73/0x80
[32790.960645] Mem-Info:
[32790.960648] DMA per-cpu:
[32790.960651] CPU    0: hi:    0, btch:   1 usd:   0
[32790.960653] Normal per-cpu:
[32790.960656] CPU    0: hi:   90, btch:  15 usd:  53
[32790.960662] Active_anon:26751 active_file:156 inactive_anon:26572
[32790.960663]  inactive_file:212 unevictable:0 dirty:0 writeback:0 unstable:0
[32790.960665]  free:745 slab:2586 mapped:152 pagetables:855 bounce:0
[32790.960672] DMA free:1064kB min:120kB low:148kB high:180kB active_anon:3904kB inactive_anon:2988kB active_file:16kB inactive_file:32kB unevictable:0kB present:15804kB pages_scanned:0 all_unreclaimable? no
[32790.960677] lowmem_reserve[]: 0 238 238 238
[32790.960685] Normal free:1916kB min:1912kB low:2388kB high:2868kB active_anon:103100kB inactive_anon:103300kB active_file:608kB inactive_file:816kB unevictable:0kB present:243776kB pages_scanned:1088 all_unreclaimable? no
[32790.960690] lowmem_reserve[]: 0 0 0 0
[32790.960694] DMA: 46*4kB 0*8kB 1*16kB 1*32kB 1*64kB 0*128kB 1*256kB 1*512kB 0*1024kB 0*2048kB 0*4096kB = 1064kB
[32790.960706] Normal: 389*4kB 21*8kB 0*16kB 4*32kB 1*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 1916kB
[32790.960718] 480 total pagecache pages
[32790.960720] 0 pages in swap cache
[32790.960723] Swap cache stats: add 0, delete 0, find 0/0
[32790.960725] Free swap  = 0kB
[32790.960727] Total swap = 0kB
[32790.964496] 65504 pages RAM
[32790.964501] 0 pages HighMem
[32790.964503] 2866 pages reserved
[32790.964505] 5564 pages shared
[32790.964507] 60767 pages non-shared
[32790.964513] Out of memory: kill process 2376 (mysqld) score 36857 or a child
[32790.964582] Killed process 2376 (mysqld)
[32796.716713] type=1503 audit(1258545520.286:30): operation="open" pid=2411 parent=1199 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[40905.072601] eth0: Media Link On 100mbps full-duplex 
[41531.072310] eth0: Media Link Off
[41611.072603] eth0: Media Link On 100mbps full-duplex 
[41672.072311] eth0: Media Link Off
[41888.307627] r8169: eth1: link down
[41889.879410] r8169: eth1: link up
[41905.503420] r8169: eth1: link down
[41915.622351] r8169: eth1: link up
[44956.519845] type=1503 audit(1258557680.089:31): operation="open" pid=3050 parent=3049 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[44956.952214] type=1503 audit(1258557680.522:32): operation="open" pid=3070 parent=3069 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[44957.300312] type=1503 audit(1258557680.870:33): operation="open" pid=3184 parent=3076 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[44958.119565] type=1503 audit(1258557681.686:34): operation="open" pid=3194 parent=3193 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[44959.248319] type=1503 audit(1258557682.818:35): operation="open" pid=3210 parent=3209 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[44959.327412] type=1503 audit(1258557682.894:36): operation="open" pid=3221 parent=3220 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
 

Is it just as simple as adding  more memory ? Is 256MB just not enough ? 

Thanks for the help.

---

### Post by falconindy on 2009-11-18
> **zonemikel said:**
> Is it just as simple as adding  more memory ? Is 256MB just not enough ?
Yes. I'm surprised you're able to boot into something even temporarily usable.

---

### Post by zonemikel on 2009-11-18
> **falconindy said:**
> Yes. I'm surprised you're able to boot into something even temporarily usable.

Oh wow, thanks ... silly/stupid me i was just reading the requirements here [http://www.ubuntu.com/products/whatisubuntu/serveredition/techspecs/9.10](http://www.ubuntu.com/products/whatisubuntu/serveredition/techspecs/9.10)

> Ubuntu Server Edition is meant to run on any Intel or AMD x86, AMD_64, EM_64T processors. It requires a minimum of 192Mb of RAM and 1Gb of disk space. Depending on your needs, you might manage with less than this. However, most users risk being frustrated if they ignore these suggestions.

Well i ordered an additional 512MB, I'll just take it easy on the server till then.

---

### Post by hitman9211 on 2009-11-18
Yes. I'm surprised you're able to boot into something even temporarily usable.:popcorn:

---

