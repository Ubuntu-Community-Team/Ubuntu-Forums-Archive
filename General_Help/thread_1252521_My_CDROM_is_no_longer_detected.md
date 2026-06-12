---
title: "My CDROM is no longer detected"
date: 2009-08-28
forum: General Help
---

### Post by Sporkman on 2009-08-28
My cdrom is no longer detected on my Acer Aspire 5100 laptop... Not sure when it stopped working, as I don't use it often. The machine has been through several release upgrades, and is currently at Ubuntu 9.04 (Linux 2.6.28-15-generic).

The cdrom does however spin up when I insert a disc, but nothing happens SW wise. Nothing shows up in /var/log/syslog or dmesg either.

Any ideas?

Here is my dev directory, note the absence of any cd related devices:

```
crw-rw----+ 1 root   audio      14,   4 2009-08-28 23:29 audio
drwxr-xr-x  2 root   root           600 2009-08-28 23:29 block
drwxr-xr-x  3 root   root            60 2009-08-28 23:29 bus
drwxr-xr-x  2 root   root          3020 2009-08-28 23:29 char
crw-------  1 root   root        5,   1 2009-08-28 23:29 console
lrwxrwxrwx  1 root   root            11 2009-08-28 23:29 core -> /proc/kcore
crw-rw----  1 root   root       10,  60 2009-08-28 23:29 cpu_dma_latency
drwxr-xr-x  5 root   root           100 2009-08-28 23:29 disk
drwxr-xr-x  2 root   root            60 2009-08-28 23:29 dri
crw-rw----+ 1 root   audio      14,   3 2009-08-28 23:29 dsp
crw-rw----  1 root   root       10,  63 2009-08-28 23:29 ecryptfs
lrwxrwxrwx  1 root   root            13 2009-08-28 23:29 fd -> /proc/self/fd
crw-rw-rw-  1 root   root        1,   7 2009-08-28 23:29 full
crw-rw-rw-+ 1 root   fuse       10, 229 2009-08-28 23:29 fuse
crw-rw----  1 root   root       10, 228 2009-08-28 23:29 hpet
prw-------  1 root   root             0 2009-08-28 23:29 initctl
drwxr-xr-x  3 root   root           300 2009-08-28 23:29 input
crw-r-----  1 root   kmem        1,   2 2009-08-27 20:35 kmem
crw-rw----  1 root   root        1,  11 2009-08-28 23:29 kmsg
srw-rw-rw-  1 root   root             0 2009-08-28 23:29 log
brw-rw----  1 root   disk        7,   0 2009-08-27 20:35 loop0
brw-rw----  1 root   disk        7,   1 2009-08-28 23:29 loop1
brw-rw----  1 root   disk        7,   2 2009-08-28 23:29 loop2
brw-rw----  1 root   disk        7,   3 2009-08-28 23:29 loop3
brw-rw----  1 root   disk        7,   4 2009-08-28 23:29 loop4
brw-rw----  1 root   disk        7,   5 2009-08-28 23:29 loop5
brw-rw----  1 root   disk        7,   6 2009-08-28 23:29 loop6
brw-rw----  1 root   disk        7,   7 2009-08-28 23:29 loop7
lrwxrwxrwx  1 root   root            13 2009-08-28 23:29 MAKEDEV -> /sbin/MAKEDEV
drwxr-xr-x  2 root   root            60 2009-08-28 23:29 mapper
crw-r-----  1 root   kmem        1,   1 2009-08-28 23:29 mem
crw-rw----+ 1 root   audio      14,   0 2009-08-28 23:29 mixer
drwxr-xr-x  2 root   root            60 2009-08-27 20:35 net
crw-rw----  1 root   root       10,  59 2009-08-28 23:29 network_latency
crw-rw----  1 root   root       10,  58 2009-08-28 23:29 network_throughput
crw-rw-rw-  1 root   root        1,   3 2009-08-27 20:35 null
crw-rw----  1 root   video     195,   0 2009-08-28 23:29 nvidia0
crw-rw----  1 root   video     195, 255 2009-08-28 23:29 nvidiactl
crw-rw----  1 root   root        1,  12 2009-08-28 23:29 oldmem
drwxr-xr-x  2 root   root            60 2009-08-28 23:29 pktcdvd
crw-r-----  1 root   kmem        1,   4 2009-08-28 23:29 port
crw-------  1 root   root      108,   0 2009-08-27 20:35 ppp
crw-rw----  1 root   root       10,   1 2009-08-28 23:29 psaux
crw-rw-rw-  1 root   tty         5,   2 2009-08-28 23:36 ptmx
drwxr-xr-x  2 root   root             0 2009-08-28 23:29 pts
brw-rw----  1 root   disk        1,   0 2009-08-28 23:29 ram0
brw-rw----  1 root   disk        1,   1 2009-08-28 23:29 ram1
brw-rw----  1 root   disk        1,  10 2009-08-28 23:29 ram10
brw-rw----  1 root   disk        1,  11 2009-08-28 23:29 ram11
brw-rw----  1 root   disk        1,  12 2009-08-28 23:29 ram12
brw-rw----  1 root   disk        1,  13 2009-08-28 23:29 ram13
brw-rw----  1 root   disk        1,  14 2009-08-28 23:29 ram14
brw-rw----  1 root   disk        1,  15 2009-08-28 23:29 ram15
brw-rw----  1 root   disk        1,   2 2009-08-28 23:29 ram2
brw-rw----  1 root   disk        1,   3 2009-08-28 23:29 ram3
brw-rw----  1 root   disk        1,   4 2009-08-28 23:29 ram4
brw-rw----  1 root   disk        1,   5 2009-08-28 23:29 ram5
brw-rw----  1 root   disk        1,   6 2009-08-28 23:29 ram6
brw-rw----  1 root   disk        1,   7 2009-08-28 23:29 ram7
brw-rw----  1 root   disk        1,   8 2009-08-28 23:29 ram8
brw-rw----  1 root   disk        1,   9 2009-08-28 23:29 ram9
crw-rw-rw-  1 root   root        1,   8 2009-08-28 23:29 random
lrwxrwxrwx  1 root   root             4 2009-08-28 23:29 rtc -> rtc0
crw-rw----  1 root   root      254,   0 2009-08-28 23:29 rtc0
brw-rw----  1 root   disk        8,   0 2009-08-28 23:29 sda
brw-rw----  1 root   disk        8,   1 2009-08-28 23:29 sda1
brw-rw----  1 root   disk        8,   2 2009-08-28 23:29 sda2
brw-rw----  1 root   disk        8,   5 2009-08-28 23:29 sda5
crw-rw----+ 1 root   audio      14,   1 2009-08-28 23:29 sequencer
crw-rw----+ 1 root   audio      14,   8 2009-08-28 23:29 sequencer2
crw-rw----  1 root   disk       21,   0 2009-08-28 23:29 sg0
drwxrwxrwt  2 root   root            80 2009-08-28 23:30 shm
crw-rw----  1 root   root       10, 231 2009-08-28 23:29 snapshot
drwxr-xr-x  2 root   root           160 2009-08-28 23:29 snd
lrwxrwxrwx  1 root   root            24 2009-08-28 23:29 sndstat -> /proc/asound/oss/sndstat
lrwxrwxrwx  1 root   root            15 2009-08-28 23:29 stderr -> /proc/self/fd/2
lrwxrwxrwx  1 root   root            15 2009-08-28 23:29 stdin -> /proc/self/fd/0
lrwxrwxrwx  1 root   root            15 2009-08-28 23:29 stdout -> /proc/self/fd/1
crw-rw-rw-  1 root   tty         5,   0 2009-08-28 23:29 tty
crw--w----  1 root   root        4,   0 2009-08-28 23:29 tty0
crw-------  1 root   root        4,   1 2009-08-28 23:29 tty1
crw--w----  1 root   tty         4,  10 2009-08-28 23:29 tty10
crw--w----  1 root   tty         4,  11 2009-08-28 23:29 tty11
crw--w----  1 root   tty         4,  12 2009-08-28 23:29 tty12
crw--w----  1 root   tty         4,  13 2009-08-28 23:29 tty13
crw--w----  1 root   tty         4,  14 2009-08-28 23:29 tty14
crw--w----  1 root   tty         4,  15 2009-08-28 23:29 tty15
crw--w----  1 root   tty         4,  16 2009-08-28 23:29 tty16
crw--w----  1 root   tty         4,  17 2009-08-28 23:29 tty17
crw--w----  1 root   tty         4,  18 2009-08-28 23:29 tty18
crw--w----  1 root   tty         4,  19 2009-08-28 23:29 tty19
crw-------  1 root   root        4,   2 2009-08-28 23:29 tty2
crw--w----  1 root   tty         4,  20 2009-08-28 23:29 tty20
crw--w----  1 root   tty         4,  21 2009-08-28 23:29 tty21
crw--w----  1 root   tty         4,  22 2009-08-28 23:29 tty22
crw--w----  1 root   tty         4,  23 2009-08-28 23:29 tty23
crw--w----  1 root   tty         4,  24 2009-08-28 23:29 tty24
crw--w----  1 root   tty         4,  25 2009-08-28 23:29 tty25
crw--w----  1 root   tty         4,  26 2009-08-28 23:29 tty26
crw--w----  1 root   tty         4,  27 2009-08-28 23:29 tty27
crw--w----  1 root   tty         4,  28 2009-08-28 23:29 tty28
crw--w----  1 root   tty         4,  29 2009-08-28 23:29 tty29
crw-------  1 root   root        4,   3 2009-08-28 23:29 tty3
crw--w----  1 root   tty         4,  30 2009-08-28 23:29 tty30
crw--w----  1 root   tty         4,  31 2009-08-28 23:29 tty31
crw--w----  1 root   tty         4,  32 2009-08-28 23:29 tty32
crw--w----  1 root   tty         4,  33 2009-08-28 23:29 tty33
crw--w----  1 root   tty         4,  34 2009-08-28 23:29 tty34
crw--w----  1 root   tty         4,  35 2009-08-28 23:29 tty35
crw--w----  1 root   tty         4,  36 2009-08-28 23:29 tty36
crw--w----  1 root   tty         4,  37 2009-08-28 23:29 tty37
crw--w----  1 root   tty         4,  38 2009-08-28 23:29 tty38
crw--w----  1 root   tty         4,  39 2009-08-28 23:29 tty39
crw-------  1 root   root        4,   4 2009-08-28 23:29 tty4
crw--w----  1 root   tty         4,  40 2009-08-28 23:29 tty40
crw--w----  1 root   tty         4,  41 2009-08-28 23:29 tty41
crw--w----  1 root   tty         4,  42 2009-08-28 23:29 tty42
crw--w----  1 root   tty         4,  43 2009-08-28 23:29 tty43
crw--w----  1 root   tty         4,  44 2009-08-28 23:29 tty44
crw--w----  1 root   tty         4,  45 2009-08-28 23:29 tty45
crw--w----  1 root   tty         4,  46 2009-08-28 23:29 tty46
crw--w----  1 root   tty         4,  47 2009-08-28 23:29 tty47
crw--w----  1 root   tty         4,  48 2009-08-28 23:29 tty48
crw--w----  1 root   tty         4,  49 2009-08-28 23:29 tty49
crw-------  1 root   root        4,   5 2009-08-28 23:29 tty5
crw--w----  1 root   tty         4,  50 2009-08-28 23:29 tty50
crw--w----  1 root   tty         4,  51 2009-08-28 23:29 tty51
crw--w----  1 root   tty         4,  52 2009-08-28 23:29 tty52
crw--w----  1 root   tty         4,  53 2009-08-28 23:29 tty53
crw--w----  1 root   tty         4,  54 2009-08-28 23:29 tty54
crw--w----  1 root   tty         4,  55 2009-08-28 23:29 tty55
crw--w----  1 root   tty         4,  56 2009-08-28 23:29 tty56
crw--w----  1 root   tty         4,  57 2009-08-28 23:29 tty57
crw--w----  1 root   tty         4,  58 2009-08-28 23:29 tty58
crw--w----  1 root   tty         4,  59 2009-08-28 23:29 tty59
crw-------  1 root   root        4,   6 2009-08-28 23:29 tty6
crw--w----  1 root   tty         4,  60 2009-08-28 23:29 tty60
crw--w----  1 root   tty         4,  61 2009-08-28 23:29 tty61
crw--w----  1 root   tty         4,  62 2009-08-28 23:29 tty62
crw--w----  1 root   tty         4,  63 2009-08-28 23:29 tty63
crw--w----  1 root   root        4,   7 2009-08-28 23:29 tty7
crw--w----  1 root   tty         4,   8 2009-08-28 23:29 tty8
crw--w----  1 root   tty         4,   9 2009-08-28 23:29 tty9
crw-rw----  1 root   dialout     4,  64 2009-08-28 23:29 ttyS0
crw-rw----  1 root   dialout     4,  65 2009-08-28 23:29 ttyS1
crw-rw----  1 root   dialout     4,  66 2009-08-28 23:29 ttyS2
crw-rw----  1 root   dialout     4,  67 2009-08-28 23:29 ttyS3
crw-rw-rw-  1 root   root        1,   9 2009-08-28 23:29 urandom
crw-rw----  1 root   root      252,   1 2009-08-28 23:29 usbdev1.1_ep00
crw-rw----  1 root   root      252,   0 2009-08-28 23:29 usbdev1.1_ep81
crw-rw----  1 root   root      252,   3 2009-08-28 23:29 usbdev2.1_ep00
crw-rw----  1 root   root      252,   2 2009-08-28 23:29 usbdev2.1_ep81
crw-rw----  1 root   root      252,   5 2009-08-28 23:29 usbdev3.1_ep00
crw-rw----  1 root   root      252,   4 2009-08-28 23:29 usbdev3.1_ep81
crw-rw----  1 root   root      253,   0 2009-08-28 23:29 usbmon0
crw-rw----  1 root   root      253,   1 2009-08-28 23:29 usbmon1
crw-rw----  1 root   root      253,   2 2009-08-28 23:29 usbmon2
crw-rw----  1 root   root      253,   3 2009-08-28 23:29 usbmon3
crw-------  1 root   vboxusers  10,  57 2009-08-28 23:29 vboxdrv
crw-rw----  1 root   tty         7,   0 2009-08-28 23:29 vcs
crw-rw----  1 root   tty         7,   1 2009-08-28 23:29 vcs1
crw-rw----  1 root   tty         7,   2 2009-08-28 23:29 vcs2
crw-rw----  1 root   tty         7,   3 2009-08-28 23:29 vcs3
crw-rw----  1 root   tty         7,   4 2009-08-28 23:29 vcs4
crw-rw----  1 root   tty         7,   5 2009-08-28 23:29 vcs5
crw-rw----  1 root   tty         7,   6 2009-08-28 23:29 vcs6
crw-rw----  1 root   tty         7,   7 2009-08-28 23:29 vcs7
crw-rw----  1 root   tty         7,   8 2009-08-28 23:29 vcs8
crw-rw----  1 root   tty         7, 128 2009-08-28 23:29 vcsa
crw-rw----  1 root   tty         7, 129 2009-08-28 23:29 vcsa1
crw-rw----  1 root   tty         7, 130 2009-08-28 23:29 vcsa2
crw-rw----  1 root   tty         7, 131 2009-08-28 23:29 vcsa3
crw-rw----  1 root   tty         7, 132 2009-08-28 23:29 vcsa4
crw-rw----  1 root   tty         7, 133 2009-08-28 23:29 vcsa5
crw-rw----  1 root   tty         7, 134 2009-08-28 23:29 vcsa6
crw-rw----  1 root   tty         7, 135 2009-08-28 23:29 vcsa7
crw-rw----  1 root   tty         7, 136 2009-08-28 23:29 vcsa8
prw-r-----  1 syslog adm              0 2009-08-28 23:29 xconsole
crw-rw-rw-  1 root   root        1,   5 2009-08-28 23:29 zero

```

Here is my lshw output:

```
    description: Notebook
    product: Aspire 5100
    vendor: Acer
    version: V2.73
    serial: LXAX90X050705090431601
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal chassis=notebook cpus=1 uuid=61656131-6563-6435-3761-0016D4B68826
  *-core
       description: Motherboard
       product: Navarro
       vendor: Acer
       physical id: 0
       version: N/A
       serial: LXAX90X050705090431601
     *-firmware
          description: BIOS
          vendor: Acer
          physical id: 0
          version: V2.73 (01/23/2007)
          size: 109KiB
          capacity: 960KiB
          capabilities: pci pcmcia pnp upgrade shadowing escd cdboot bootselect int5printscreen int9keyboard int17printer int10video acpi usb agp smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: AMD Turion(tm) 64 Mobile Technology MK-36
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 15.12.2
          slot: Socket M2/S1G1
          size: 2GHz
          capacity: 2GHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow up pni cx16 lahf_lm svm extapic cr8_legacy cpufreq
        *-cache:0
             description: L2 cache
             physical id: 5
             slot: L2 Cache
             size: 512KiB
             capacity: 1MiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:2
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-memory
          description: System Memory
          physical id: a
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: DIMM Synchronous
             physical id: 0
             slot: S1
             size: 512MiB
             width: 64 bits
        *-bank:1
             description: DIMM Synchronous
             physical id: 1
             slot: S2
             size: 512MiB
             width: 64 bits
     *-pci:0
          description: Host bridge
          product: RS480 Host Bridge
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 10
          width: 32 bits
          clock: 66MHz
          configuration: latency=64
        *-pci:0
             description: PCI bridge
             product: RS480 PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci ht bus_master cap_list
           *-display UNCLAIMED
                description: VGA compatible controller
                product: RS482 [Radeon Xpress 200M]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm bus_master cap_list
                configuration: latency=66 mingnt=8
        *-pci:1
             description: PCI bridge
             product: RS480 PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: RS480 PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport-driver
        *-ide:0
             description: IDE interface
             product: IXP SB400 Serial ATA Controller
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: scsi0
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm msi bus_master cap_list emulated
             configuration: driver=sata_sil latency=64 module=sata_sil
           *-disk
                description: ATA Disk
                product: Hitachi HTS54161
                vendor: Hitachi
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: SBDO
                serial: SB2D04E4HVULUE
                size: 111GiB (120GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=d0014e92
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: b6d5649c-9e88-4b60-b9ff-d8f969e88884
                   size: 109GiB
                   capacity: 109GiB
                   capabilities: primary bootable journaled large_files ext3 ext2 initialized
                   configuration: created=2008-04-07 20:18:24 filesystem=ext3 modified=2009-08-28 23:29:07 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2009-08-28 23:05:58 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 2212MiB
                   capacity: 2212MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 2212MiB
                      capabilities: nofs
        *-usb:0
             description: USB Controller
             product: IXP SB400 USB Host Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
        *-usb:1
             description: USB Controller
             product: IXP SB400 USB Host Controller
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
        *-usb:2
             description: USB Controller
             product: IXP SB400 USB2 Host Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ehci_hcd latency=64 module=ehci_hcd
        *-serial
             description: SMBus
             product: IXP SB400 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 83
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: driver=piix4_smbus latency=0 module=i2c_piix4
        *-ide:1
             description: IDE interface
             product: IXP SB400 IDE Controller
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: ide msi bus_master cap_list
             configuration: driver=pata_atiixp latency=64
        *-multimedia
             description: Audio device
             product: IXP SB4x0 High Definition Audio Controller
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=HDA Intel latency=64 module=snd_hda_intel
        *-isa
             description: ISA bridge
             product: IXP SB400 PCI-ISA Bridge
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:3
             description: PCI bridge
             product: IXP SB400 PCI-PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
           *-network:0
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 1
                bus info: pci@0000:06:01.0
                logical name: eth0
                version: 10
                serial: 00:16:d4:b6:88:26
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
           *-network:1
                description: Wireless interface
                product: AR2413 802.11bg NIC
                vendor: Atheros Communications Inc.
                physical id: 2
                bus info: pci@0000:06:02.0
                logical name: wmaster0
                version: 01
                serial: 00:19:7d:7f:3c:59
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=ath5k_pci ip=192.168.1.3 latency=168 maxlatency=28 mingnt=10 module=ath5k multicast=yes wireless=IEEE 802.11bg
           *-pcmcia
                description: CardBus bridge
                product: CB-712/4 Cardbus Controller
                vendor: ENE Technology Inc
                physical id: 4
                bus info: pci@0000:06:04.0
                version: 10
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
           *-memory:0 UNCLAIMED
                description: FLASH memory
                product: ENE PCI Memory Stick Card Reader Controller
                vendor: ENE Technology Inc
                physical id: 4.1
                bus info: pci@0000:06:04.1
                version: 01
                width: 32 bits
                clock: 33MHz (30.3ns)
                capabilities: pm bus_master cap_list
                configuration: latency=64 maxlatency=4 mingnt=1
           *-system
                description: SD Host controller
                product: ENE PCI Secure Digital Card Reader Controller
                vendor: ENE Technology Inc
                physical id: 4.2
                bus info: pci@0000:06:04.2
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=64 maxlatency=72 mingnt=32 module=sdhci_pci
           *-memory:1 UNCLAIMED
                description: FLASH memory
                product: FLASH memory: ENE Technology Inc:
                vendor: ENE Technology Inc
                physical id: 4.3
                bus info: pci@0000:06:04.3
                version: 01
                width: 32 bits
                clock: 33MHz (30.3ns)
                capabilities: pm bus_master cap_list
                configuration: latency=64 maxlatency=4 mingnt=1
           *-memory:2
                description: FLASH memory
                product: SD/MMC Card Reader Controller
                vendor: ENE Technology Inc
                physical id: 4.4
                bus info: pci@0000:06:04.4
                version: 01
                width: 32 bits
                clock: 33MHz (30.3ns)
                capabilities: pm cap_list
                configuration: driver=sdhci-pci latency=0 maxlatency=72 mingnt=32 module=sdhci_pci
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp module=k8temp
  *-battery
       description: Lithium Ion Battery
       product: PANASONIC
       vendor: PANASONIC
       physical id: 1
       slot: 1st Battery
       capacity: 3900mWh
       configuration: voltage=14.8V

```

Here is the lsmod output:

```
Module                  Size  Used by
radeon                342816  2 
drm                    96424  3 radeon
ppdev                  15620  0 
vboxnetflt             91016  0 
vboxdrv               117672  1 vboxnetflt
input_polldev          11912  0 
dm_crypt               20996  0 
joydev                 18496  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
arc4                    9856  2 
ecb                    10752  2 
pcmcia                 44748  0 
snd_hda_intel         434100  2 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                83076  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
ath5k                 107520  0 
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mac80211              217592  1 ath5k
yenta_socket           32396  1 
psmouse                61972  0 
snd                    62756  13 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
acer_wmi               24260  0 
sdhci_pci              15232  0 
sdhci                  23940  1 sdhci_pci
rsrc_nonstatic         19328  1 yenta_socket
pcmcia_core            43540  3 pcmcia,yenta_socket,rsrc_nonstatic
serio_raw              13444  0 
pcspkr                 10496  0 
k8temp                 12416  0 
cfg80211               38288  2 ath5k,mac80211
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
led_class              12036  2 ath5k,acer_wmi
i2c_piix4              18448  0 
shpchp                 40212  0 
video                  25360  0 
ati_agp                14988  0 
agpgart                42696  2 drm,ati_agp
output                 11008  1 video
8139too                32128  0 
8139cp                 27776  0 
mii                    13312  2 8139too,8139cp
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

```

---

### Post by ptn107 on 2009-08-29
Check your /etc/fstab make sure a cdrom entry exists in there.  I have two and they show up in /etc/fstab as:
```
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
```

I don't see any *scdx* devices in your list there.  You may have to manually re-add it using makedev or makenod.

---

### Post by Sporkman on 2009-08-29
> **ptn107 said:**
> Check your /etc/fstab make sure a cdrom entry exists in there.  I have two and they show up in /etc/fstab as:
```
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
```

I don't see any *scdx* devices in your list there.  You may have to manually re-add it using makedev or makenod.

I do have such an entry:

```
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

---

### Post by ptn107 on 2009-08-29
Well your /dev/sdc0 does not exist.  Rebooting won't fix it huh?  You might need to run mknod to recreate it.  I'm not too familiar with it.

---

### Post by Sporkman on 2009-08-29
> **ptn107 said:**
> Well you /dev/sdc0 does not exist.  Rebooting won't fix it huh?  You might need to run mknod to recreate it.  I'm not too familiar with it.

Nope - rebooting doesn't help (with or without a cd in the drive).

Which block device would I mknod it to? Here is my /proc/devices:

```
/proc> more devices 
Character devices:
  1 mem
  4 /dev/vc/0
  4 tty
  4 ttyS
  5 /dev/tty
  5 /dev/console
  5 /dev/ptmx
  6 lp
  7 vcs
 10 misc
 13 input
 14 sound
 21 sg
 29 fb
 99 ppdev
108 ppp
116 alsa
128 ptm
136 pts
180 usb
189 usb_device
216 rfcomm
226 drm
250 pcmcia
251 hidraw
252 usb_endpoint
253 usbmon
254 rtc

Block devices:
  1 ramdisk
259 blkext
  7 loop
  8 sd
  9 md
 11 sr
 65 sd
 66 sd
 67 sd
 68 sd
 69 sd
 70 sd
 71 sd
128 sd
129 sd
130 sd
131 sd
132 sd
133 sd
134 sd
135 sd
252 device-mapper
253 pktcdvd
254 mdp

```

---

### Post by ptn107 on 2009-08-29
Try (copy/paste as one command):
```
cd /dev && sudo mknod -m 0660 /dev/sr0 b 8 32 && sudo chown root.cdrom /dev/sr0 && sudo ln -s sr0 scd0 && sudo ln -s sr0 cdrom && sudo ln -s sr0 cdrw
```

---

### Post by Sporkman on 2009-08-31
Sorry I was out of internet range for a couple of days...

No luck with that command string, either with or without a reboot.

---

### Post by holycow131415 on 2009-08-31
if you have grub, try to boot from an earlier kernal and see if it works. if so, go to synaptic package, search for linux-image, uninstall all the versions that dont work, reboot, then reinstall the linux-image

---

