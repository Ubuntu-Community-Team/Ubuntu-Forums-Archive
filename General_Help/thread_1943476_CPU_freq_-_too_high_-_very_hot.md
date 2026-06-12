---
title: "CPU freq - too high - very hot"
date: 2012-03-19
forum: General Help
---

### Post by overkill22 on 2012-03-19
since i've installed lubuntu 11.10 i had a problem with the cpu controll. it seems that the cpu is always running a high speed also when i'm doing nothing.
i tried to install powernowd (but i'm not shure i did it right), how can i set an automatic cpu controll ?

---

### Post by HiImTye on 2012-03-19
give [jupiter]("http://www.webupd8.org/2011/09/jupiter-applet-finally-available-for.html") a try

---

### Post by TeoBigusGeekus on 2012-03-19
Which app is causing this?
Run top or htop to find out.

---

### Post by overkill22 on 2012-03-20
> **TeoBigusGeekus said:**
> Which app is causing this?
Run top or htop to find out.

no apps running....cpu 1% ... but it is always running...

---

### Post by idoitprone on 2012-03-20
sudo cat /proc/cpuinfo

---

### Post by overkill22 on 2012-03-20
> **idoitprone said:**
> sudo cat /proc/cpuinfo

```
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 28
model name	: Intel(R) Atom(TM) CPU N270   @ 1.60GHz
stepping	: 2
cpu MHz		: 1600.000
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 1
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 xtpr pdcm movbe lahf_lm dts
bogomips	: 3199.49
clflush size	: 64
cache_alignment	: 64
address sizes	: 32 bits physical, 32 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 28
model name	: Intel(R) Atom(TM) CPU N270   @ 1.60GHz
stepping	: 2
cpu MHz		: 800.000
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 1
apicid		: 1
initial apicid	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 xtpr pdcm movbe lahf_lm dts
bogomips	: 3200.03
clflush size	: 64
cache_alignment	: 64
address sizes	: 32 bits physical, 32 bits virtual
power management:

```

---

### Post by idoitprone on 2012-03-20
install a lighter distro. kde4 is lighter than ubuntu because n270 is not such a great cpu. I know because i hate using it. Run lubuntu or xubuntu because ur cpu cannot handle it

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-03-20
> **overkill22 said:**
> no apps running....cpu 1% ... but it is always running...

Then why do you say it's CPU that's causing you trouble?

First thing, if your CPU's frequency is high, that's not a bad thing, that's a good thing. The higher the frequency, the stronger the CPU.

Second, if you meant to say CPU usage, but then later on you say CPU usage is 1%, then it means that it's not the CPU usage that's causing you trouble.

Third, why don't you let us know which computer model you have? does it perhaps have switchable graphic system?

---

### Post by overkill22 on 2012-03-20
> **idoitprone said:**
> install a lighter distro. kde4 is lighter than ubuntu because n270 is not such a great cpu. I know because i hate using it. Run lubuntu or xubuntu because ur cpu cannot handle it

my so is LUBUNTU 11.10..  and with ubuntu 10.04 it was right...

---

### Post by idoitprone on 2012-03-20
> **overkill22 said:**
> my so is LUBUNTU 11.10..  and with ubuntu 10.04 it was right...

my aplogies you where running lubuntu sorry

strange

---

### Post by Rodney9 on 2012-03-20
The OP is using[COLOR="Blue"] Lubuntu[/COLOR]

For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by idoitprone on 2012-03-20
> **overkill22 said:**
> my so is LUBUNTU 11.10..  and with ubuntu 10.04 it was right...

hmm dont tell me those intel guy disable all of i915 power saving features arrrrg


post output of 

sudo lspci -v

sudo modinfo i915

---

### Post by overkill22 on 2012-03-20
> **&#1058 said:**
> Then why do you say it's CPU that's causing you trouble?

First thing, if your CPU's frequency is high, that's not a bad thing, that's a good thing. The higher the frequency, the stronger the CPU.

Second, if you meant to say CPU usage, but then later on you say CPU usage is 1%, then it means that it's not the CPU usage that's causing you trouble.

Third, why don't you let us know which computer model you have? does it perhaps have switchable graphic system?

i'm sorry. i think it is cpu problem because the cooling fun is always running.. before it was always low... 
the pc is 
compaq mini 311.

lshw

```
compaq-mini-311           
    description: Notebook
    version: 0391100000201C00000320000
    width: 32 bits
    capabilities: smbios-2.6 dmi-2.6
    configuration: boot=normal chassis=notebook family=103C_5335KV sku=VT400EA#ABZ uuid=434E4639-3339-364D-5130-00269E505CF3
  *-core
       description: Motherboard
       product: 3651
       vendor: Quanta
       physical id: 0
       version: 49.14
       serial: CNF9396MQ0
       slot: Base Board Chassis Location
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 0
          version: F.02
          date: 08/04/2009
          size: 1MiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb
     *-memory
          description: System Memory
          physical id: d
          slot: System board or motherboard
          size: 3GiB
          capacity: 3GiB
        *-bank:0
             description: DIMM DDR3 Synchronous 1066 MHz (0,9 ns)
             product: M471B2873EH1-C7
             vendor: Samsung
             physical id: 0
             serial: 0x00000000
             slot: Bottom - Slot 1 (top)
             size: 1GiB
             width: 64 bits
             clock: 1066MHz (0.9ns)
        *-bank:1
             description: DIMM DDR3 Synchronous 1066 MHz (0,9 ns)
             product: 16JSF25664HZ-1G1F1
             vendor: Micron Technology
             physical id: 1
             serial: 0xDE3CF8E4
             slot: J3MY
             size: 2GiB
             width: 64 bits
             clock: 1066MHz (0.9ns)
     *-cpu
          description: CPU
          product: Intel(R) Atom(TM) CPU N270   @ 1.60GHz
          vendor: Intel Corp.
          physical id: 16
          bus info: cpu@0
          version: 6.12.2
          serial: 0001-06C2-0000-0000-0000-0000
          slot: CPU
          size: 800MHz
          capacity: 1600MHz
          width: 32 bits
          clock: 533MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 xtpr pdcm movbe lahf_lm cpufreq
          configuration: cores=1 enabledcores=1 id=0 threads=2
        *-cache:0
             description: L2 cache
             physical id: 17
             slot: Unknown
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous internal write-back unified
        *-cache:1
             description: L1 cache
             physical id: 18
             slot: Unknown
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back instruction
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 32 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: MCP79 Host Bridge
          vendor: nVidia Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: b1
          width: 32 bits
          clock: 66MHz
        *-memory:0 UNCLAIMED
             description: RAM memory
             product: MCP79 Memory Controller
             vendor: nVidia Corporation
             physical id: 0.1
             bus info: pci@0000:00:00.1
             version: b1
             width: 32 bits
             clock: 66MHz (15.2ns)
             capabilities: bus_master
             configuration: latency=0
        *-isa
             description: ISA bridge
             product: MCP79 LPC Bridge
             vendor: nVidia Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: b3
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-memory:1 UNCLAIMED
             description: RAM memory
             product: MCP79 Memory Controller
             vendor: nVidia Corporation
             physical id: 3.1
             bus info: pci@0000:00:03.1
             version: b1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-serial
             description: SMBus
             product: MCP79 SMBus
             vendor: nVidia Corporation
             physical id: 3.2
             bus info: pci@0000:00:03.2
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: pm cap_list
             configuration: driver=nForce2_smbus latency=0
             resources: irq:11 ioport:3080(size=64) ioport:3040(size=64) ioport:3000(size=64)
        *-memory:2 UNCLAIMED
             description: RAM memory
             product: MCP79 Memory Controller
             vendor: nVidia Corporation
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: b1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-processor UNCLAIMED
             description: Co-processor
             product: MCP79 Co-processor
             vendor: nVidia Corporation
             physical id: 3.5
             bus info: pci@0000:00:03.5
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: latency=0 maxlatency=1 mingnt=3
             resources: memory:feb80000-febfffff
        *-usb:0
             description: USB Controller
             product: MCP79 OHCI USB 1.1 Controller
             vendor: nVidia Corporation
             physical id: 4
             bus info: pci@0000:00:04.0
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
             resources: irq:21 memory:d3108000-d3108fff
        *-usb:1
             description: USB Controller
             product: MCP79 EHCI USB 2.0 Controller
             vendor: nVidia Corporation
             physical id: 4.1
             bus info: pci@0000:00:04.1
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: debug pm ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
             resources: irq:23 memory:d3109200-d31092ff
        *-usb:2
             description: USB Controller
             product: MCP79 OHCI USB 1.1 Controller
             vendor: nVidia Corporation
             physical id: 6
             bus info: pci@0000:00:06.0
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
             resources: irq:20 memory:d3107000-d3107fff
        *-usb:3
             description: USB Controller
             product: MCP79 EHCI USB 2.0 Controller
             vendor: nVidia Corporation
             physical id: 6.1
             bus info: pci@0000:00:06.1
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: debug pm ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
             resources: irq:22 memory:d3109100-d31091ff
        *-multimedia
             description: Audio device
             product: MCP79 High Definition Audio
             vendor: nVidia Corporation
             physical id: 8
             bus info: pci@0000:00:08.0
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list
             configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2
             resources: irq:20 memory:d3100000-d3103fff
        *-pci:0
             description: PCI bridge
             product: MCP79 PCI Bridge
             vendor: nVidia Corporation
             physical id: 9
             bus info: pci@0000:00:09.0
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-network
             description: Ethernet interface
             product: MCP79 Ethernet
             vendor: nVidia Corporation
             physical id: a
             bus info: pci@0000:00:0a.0
             logical name: eth0
             version: b1
             serial: 00:26:9e:50:5c:f3
             capacity: 100Mbit/s
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
             resources: irq:22 memory:d3106000-d3106fff ioport:30e0(size=8) memory:d3109000-d31090ff memory:d3109300-d310930f
        *-storage
             description: SATA controller
             product: MCP79 AHCI Controller
             vendor: nVidia Corporation
             physical id: b
             bus info: pci@0000:00:0b.0
             logical name: scsi0
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm msi ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0 maxlatency=1 mingnt=3
             resources: irq:40 ioport:30d8(size=8) ioport:30ec(size=4) ioport:30d0(size=8) ioport:30e8(size=4) ioport:30c0(size=16) memory:d3104000-d3105fff
           *-disk
                description: ATA Disk
                product: ST9320325AS
                vendor: Seagate
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 0005
                serial: 5VD1VC94
                size: 298GiB (320GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0006e686
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: fa1311a1-925a-4a8a-a760-30cb1a2fa5b8
                   size: 295GiB
                   capacity: 295GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2012-03-07 11:44:35 filesystem=ext4 lastmountpoint=/ modified=2012-03-16 09:25:04 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,acl,commit=600,barrier=1,data=ordered mounted=2012-03-20 09:38:31 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 2813MiB
                   capacity: 2813MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 2813MiB
                      capabilities: nofs
        *-pci:1
             description: PCI bridge
             product: MCP79 PCI Express Bridge
             vendor: nVidia Corporation
             physical id: 10
             bus info: pci@0000:00:10.0
             version: b1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi normal_decode bus_master cap_list
             resources: ioport:2000(size=4096) memory:d2000000-d2ffffff ioport:c0000000(size=301989888)
           *-display
                description: VGA compatible controller
                product: ION VGA [GeForce 9400M]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                version: b1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi vga_controller bus_master cap_list rom
                configuration: driver=nouveau latency=0
                resources: irq:21 memory:d2000000-d2ffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:2000(size=128)
        *-pci:2
             description: PCI bridge
             product: MCP79 PCI Express Bridge
             vendor: nVidia Corporation
             physical id: 15
             bus info: pci@0000:00:15.0
             version: b1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 memory:d3000000-d30fffff
           *-network
                description: Wireless interface
                product: BCM4312 802.11b/g LP-PHY
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth1
                version: 01
                serial: 0c:60:76:55:c2:68
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 latency=0 multicast=yes wireless=IEEE 802.11bg
                resources: irq:16 memory:d3000000-d3003fff
        *-pci:3
             description: PCI bridge
             product: MCP79 PCI Express Bridge
             vendor: nVidia Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: b1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16
     *-scsi
          physical id: 1
          bus info: usb@2:1
          logical name: scsi13
          logical name: scsi14
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-cdrom
             description: SCSI CD-ROM
             product: Mass Storage
             vendor: HUAWEI
             physical id: 0
             bus info: scsi@13:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/scd0
             logical name: /dev/sr0
             version: 2.31
             capabilities: removable audio
             configuration: ansiversion=2 status=ready
           *-medium
                physical id: 0
                logical name: /dev/cdrom
                capabilities: partitioned partitioned:mac
              *-volume:0 UNCLAIMED
                   description: Apple partition map
                   physical id: 1
                   capacity: 1KiB
              *-volume:1 UNCLAIMED
                   description: Apple HFS
                   physical id: 2
                   version: 4
                   serial: 00000000-0000-0000-0000-000000000800
                   size: 29MiB
                   capacity: 29MiB
                   capabilities: hfsplus initialized
                   configuration: checked=2010-04-08 14:28:20 created=2010-04-08 12:28:20 filesystem=hfsplus lastmountedby=LSDf modified=2010-04-08 14:28:21 state=unclean
        *-disk
             description: SCSI Disk
             physical id: 1
             bus info: scsi@14:0.0.0
             logical name: /dev/sdb
  *-battery
       product: PT06055
       vendor: SMP-LG26B3
       physical id: 1
       version: 0
       serial: 0
       slot: Primary
       capacity: 5100mWh
       configuration: voltage=10,8V
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: wwan0
       serial: 02:50:f3:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes driver=cdc_ether driverversion=22-Aug-2005 firmware=Mobile Broadband Network Device link=no multicast=yes


```

---

### Post by overkill22 on 2012-03-20
> **idoitprone said:**
> hmm dont tell me those intel guy disable all of i915 power saving features arrrrg


post output of 

sudo lspci -v

sudo modinfo i915

```
utente@compaq-mini-311:~$ sudo ispci -v
[sudo] password for utente: 
sudo: ispci: command not found
utente@compaq-mini-311:~$ sudo modinfo i915
filename:       /lib/modules/3.0.0-16-generic/kernel/drivers/gpu/drm/i915/i915.ko
license:        GPL and additional rights
description:    Intel Graphics
author:         Tungsten Graphics, Inc.
license:        GPL and additional rights
srcversion:     42E662E7B8968DC329F73B7
alias:          pci:v00008086d0000015Asv*sd*bc03sc*i*
alias:          pci:v00008086d00000162sv*sd*bc03sc*i*
alias:          pci:v00008086d00000152sv*sd*bc03sc*i*
alias:          pci:v00008086d00000166sv*sd*bc03sc*i*
alias:          pci:v00008086d00000156sv*sd*bc03sc*i*
alias:          pci:v00008086d0000010Asv*sd*bc03sc*i*
alias:          pci:v00008086d00000126sv*sd*bc03sc*i*
alias:          pci:v00008086d00000116sv*sd*bc03sc*i*
alias:          pci:v00008086d00000106sv*sd*bc03sc*i*
alias:          pci:v00008086d00000122sv*sd*bc03sc*i*
alias:          pci:v00008086d00000112sv*sd*bc03sc*i*
alias:          pci:v00008086d00000102sv*sd*bc03sc*i*
alias:          pci:v00008086d00000046sv*sd*bc03sc*i*
alias:          pci:v00008086d00000042sv*sd*bc03sc*i*
alias:          pci:v00008086d0000A011sv*sd*bc03sc*i*
alias:          pci:v00008086d0000A001sv*sd*bc03sc*i*
alias:          pci:v00008086d00002E92sv*sd*bc03sc*i*
alias:          pci:v00008086d00002E42sv*sd*bc03sc*i*
alias:          pci:v00008086d00002E32sv*sd*bc03sc*i*
alias:          pci:v00008086d00002E22sv*sd*bc03sc*i*
alias:          pci:v00008086d00002E12sv*sd*bc03sc*i*
alias:          pci:v00008086d00002E02sv*sd*bc03sc*i*
alias:          pci:v00008086d00002A42sv*sd*bc03sc*i*
alias:          pci:v00008086d00002A12sv*sd*bc03sc*i*
alias:          pci:v00008086d00002A02sv*sd*bc03sc*i*
alias:          pci:v00008086d000029D2sv*sd*bc03sc*i*
alias:          pci:v00008086d000029C2sv*sd*bc03sc*i*
alias:          pci:v00008086d000029B2sv*sd*bc03sc*i*
alias:          pci:v00008086d000029A2sv*sd*bc03sc*i*
alias:          pci:v00008086d00002992sv*sd*bc03sc*i*
alias:          pci:v00008086d00002982sv*sd*bc03sc*i*
alias:          pci:v00008086d00002972sv*sd*bc03sc*i*
alias:          pci:v00008086d000027AEsv*sd*bc03sc*i*
alias:          pci:v00008086d000027A2sv*sd*bc03sc*i*
alias:          pci:v00008086d00002772sv*sd*bc03sc*i*
alias:          pci:v00008086d00002592sv*sd*bc03sc*i*
alias:          pci:v00008086d0000258Asv*sd*bc03sc*i*
alias:          pci:v00008086d00002582sv*sd*bc03sc*i*
alias:          pci:v00008086d00002572sv*sd*bc03sc*i*
alias:          pci:v00008086d0000358Esv*sd*bc03sc*i*
alias:          pci:v00008086d00003582sv*sd*bc03sc*i*
alias:          pci:v00008086d00002562sv*sd*bc03sc*i*
alias:          pci:v00008086d00003577sv*sd*bc03sc*i*
depends:        drm,drm_kms_helper,video,i2c-algo-bit
vermagic:       3.0.0-16-generic SMP mod_unload modversions 686 
parm:           modeset:int
parm:           fbpercrtc:int
parm:           panel_ignore_lid:int
parm:           powersave:int
parm:           semaphores:int
parm:           i915_enable_rc6:int
parm:           i915_enable_fbc:int
parm:           lvds_downclock:int
parm:           lvds_use_ssc:Use Spread Spectrum Clock with panels [LVDS/eDP] (default: auto from VBT) (int)
parm:           vbt_sdvo_panel_type:int
parm:           reset:bool
utente@compaq-mini-311:~$ 

```

---

### Post by idoitprone on 2012-03-20
```
vermagic:       3.0.0-16-generic SMP mod_unload modversions 686  
parm:           modeset:int
 parm:           fbpercrtc:int 
parm:           panel_ignore_lid:int
 parm:           powersave:int 
parm:           semaphores:in
t parm:           i915_enable_rc6:int 
parm:           i915_enable_fbc:int 
parm:           lvds_downclock:int 
parm:           lvds_use_ssc:Use Spread Spectrum Clock with panels [LVDS/eDP] (default: auto from VBT) (int)
 parm:           vbt_sdvo_panel_type:int 
parm:           reset:bool
```strange it does not say the defaults like mine. I wonder why would ubuntu like to change this?

```
vermagic:       3.2.0-2-amd64 SMP mod_unload modversions 
parm:           modeset:Use kernel modesetting [KMS] (0=DRM_I915_KMS from .config, 1=on, -1=force vga console preference [default]) (int)
parm:           fbpercrtc:int
parm:           panel_ignore_lid:Override lid status (0=autodetect [default], 1=lid open, -1=lid closed) (int)
parm:           powersave:Enable powersavings, fbc, downclocking, etc. (default: true) (int)
parm:           semaphores:Use semaphores for inter-ring sync (default: -1 (use per-chip defaults)) (int)
parm:           i915_enable_rc6:Enable power-saving render C-state 6 (default: -1 (use per-chip **default**) (int)
parm:           i915_enable_fbc:Enable frame buffer compression for power savings (default: -1 (use per-chip **default**)) (int)
parm:           lvds_downclock:Use panel (LVDS/eDP) downclocking for power savings (**default**: false) (int)
parm:           lvds_use_ssc:Use Spread Spectrum Clock with panels [LVDS/eDP] (default: auto from VBT) (int)
parm:           vbt_sdvo_panel_type:Override selection of SDVO panel mode in the VBT (default: auto) (int)
parm:           reset:Attempt GPU resets (default: true) (bool)
parm:           enable_hangcheck:Periodically check GPU activity for detecting hangs. WARNING: Disabling this can cause system wide hangs. (default: true) (bool)
```i am all out of ideas
[http://danielj.se/2011/11/16/how-to-fix-powerbattery-problem-with-linux-kernel-3-x-on-ubuntu-11-10/](http://danielj.se/2011/11/16/how-to-fix-powerbattery-problem-with-linux-kernel-3-x-on-ubuntu-11-10/) this might help you but i cannot tell if it your gpu that eating you power

install powertop it might give you a power idea

```
sudo apt-get install powertop
```to run
```
sudo powertop
```q to quit

ignore this post ii guess

---

### Post by overkill22 on 2012-03-20
sorry, first command was wrong

```
utente@compaq-mini-311:~$ sudo lspci
00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b3)
00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:06.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:06.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1)
00:0a.0 Ethernet controller: nVidia Corporation MCP79 Ethernet (rev b1)
00:0b.0 SATA controller: nVidia Corporation MCP79 AHCI Controller (rev b1)
00:10.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:16.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
02:00.0 VGA compatible controller: nVidia Corporation ION VGA [GeForce 9400M] (rev b1)
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)

```

---

### Post by idoitprone on 2012-03-20
> **overkill22 said:**
> sorry, first command was wrong

```
utente@compaq-mini-311:~$ sudo lspci
00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b3)
00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:06.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:06.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1)
00:0a.0 Ethernet controller: nVidia Corporation MCP79 Ethernet (rev b1)
00:0b.0 SATA controller: nVidia Corporation MCP79 AHCI Controller (rev b1)
00:10.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:16.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
02:00.0 VGA compatible controller: nVidia Corporation ION VGA [GeForce 9400M] (rev b1)
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)

```

it is not your intel gpu

** 02:00.0 VGA compatible controller: nVidia Corporation ION VGA [GeForce 9400M] (rev b1)**

please install the priotory driver it might save you power cuz the opensource driver is doing strange things

---

### Post by overkill22 on 2012-03-20
seems that i'm using only cpu1....

---

### Post by overkill22 on 2012-03-20
> **idoitprone said:**
> it is not your intel gpu

** 02:00.0 VGA compatible controller: nVidia Corporation ION VGA [GeForce 9400M] (rev b1)**

please install the priotory driver it might save you power cuz the opensource driver is doing strange things

no way to install nvidia driver...i opened a thread for that but no one can help me...

---

### Post by idoitprone on 2012-03-20
> **overkill22 said:**
> seems that i'm using only cpu1....

an operating system aways doing work, but you said that it is using 1 percent of the total power which means it cannot be your cpu that draining your power making your computer hot. Well on my computer, this is usually not a problem. and I was using a de like kde4

In this case I have to suspect the nvidia gpu.

[http://www.nvidia.com/object/linux-display-ia32-295.20-driver.html](http://www.nvidia.com/object/linux-display-ia32-295.20-driver.html)

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by overkill22 on 2012-03-20
> **idoitprone said:**
> an operating system aways doing work, but you said that it is using 1 percent of the total power which means it cannot be your cpu that draining your power making your computer hot. Well on my computer, this is usually not a problem. and I was using a de like kde4

In this case I have to suspect the nvidia gpu.

[http://www.nvidia.com/object/linux-display-ia32-295.20-driver.html](http://www.nvidia.com/object/linux-display-ia32-295.20-driver.html)

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

i've tryed a lot... but...see... [http://ubuntuforums.org/showthread.php?t=1938166]("http://ubuntuforums.org/showthread.php?t=1938166")

---

### Post by Adrian98 on 2012-03-20
That's right , better the frequency better the CPU is, and usages is 1% as per the specs he gave us!! May be his CPU's fan would be making noise and that's why he is relating it to the CPU usages frequencies!!!

---

### Post by overkill22 on 2012-03-20
> **Adrian98 said:**
> That's right , better the frequency better the CPU is, and usages is 1% as per the specs he gave us!! May be his CPU's fan would be making noise and that's why he is relating it to the CPU usages frequencies!!!

is not only noise, is hot and the battery finish quickly than before...

---

### Post by overkill22 on 2012-03-20
i've tried to install nvidia drivers but nothing...
fan is always running high.... i tryed to install Psensor for controll gpu temp but it seems allright...
i don't know why before this pc was very very cool we used on a playd for 3-4 ours and nothing was hot... if i start the pc and wait for 3 minutes doing nothing, the pc burns....

---

### Post by idoitprone on 2012-03-20
then test 

```
aspm=force
```

for grub default

at it to /etc/default/grub 

at GRUB_CMDLINE_LINUX_DEFAULT after splash before the quotes
[http://www.dedoimedo.com/computers/grub-2.html#mozTocId624480](http://www.dedoimedo.com/computers/grub-2.html#mozTocId624480)

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-03-20
What I am guessing is that it's either a CPU **fan only** related problem, or a **GPU / GPU fan** problem. I've got Acer 5830, so it's a different machine, but this sounds as the same problem I've had after installing Ubuntu. This blog post helped me solving it:

[http://blogs.law.harvard.edu/djcp/2011/11/kubuntu-11-10-on-the-acer-aspire-timelinex-4830tg-6450/](http://blogs.law.harvard.edu/djcp/2011/11/kubuntu-11-10-on-the-acer-aspire-timelinex-4830tg-6450/)

Maybe you should give those solutions a shot?

---

### Post by overkill22 on 2012-03-21
> **idoitprone said:**
> then test 

```
aspm=force
```for grub default

at it to /etc/default/grub 

at GRUB_CMDLINE_LINUX_DEFAULT after splash before the quotes
[http://www.dedoimedo.com/computers/grub-2.html#mozTocId624480](http://www.dedoimedo.com/computers/grub-2.html#mozTocId624480)

what does it means?
i've added ```
**GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash pcie_aspm=force acpi_osi=Linux i915.i915_enable_rc6=1&#8243;**
```

but nothing to do...now i think fan is always running...

---

### Post by idoitprone on 2012-03-21
remove this 
```
i915.i915_enable_rc6=1
```you do not have intel intergrated

did you run```
 sudo update-grub
```?


> what does it means?
i've added      Code:
     **GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash pcie_aspm=force acpi_osi=Linux i915.i915_enable_rc6=1&#8243;** 
but nothing to do...now i think fan is always running...theyre kernel boot options
they each do something

like quiet tell the kernel to not write to screen while booting

---

### Post by idoitprone on 2012-03-21
@TOMHIIA
> **&#1058 said:**
> What I am guessing is that it's either a CPU **fan only** related problem, or a **GPU / GPU fan** problem. I've got Acer 5830, so it's a different machine, but this sounds as the same problem I've had after installing Ubuntu. This blog post helped me solving it:

[http://blogs.law.harvard.edu/djcp/2011/11/kubuntu-11-10-on-the-acer-aspire-timelinex-4830tg-6450/](http://blogs.law.harvard.edu/djcp/2011/11/kubuntu-11-10-on-the-acer-aspire-timelinex-4830tg-6450/)

Maybe you should give those solutions a shot?

btw i have the same machine you should also add
lvds is the important one

```
i915.lvds_downclock=1 i915.i915_enable_fbc=1
``````

cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.2.0-2-amd64 root=UUID=0b48a573-9da1-4792-b2f5-dc9f97abbee1 ro quiet acpi_osi=Linux apci_xbacklight=vendor i915.i915_enable_rc6=1 i915.i915_enable_fbc=1 i915.lvds_downclock=1
```

---

### Post by overkill22 on 2012-03-22
> **idoitprone said:**
> remove this 
```
i915.i915_enable_rc6=1
```you do not have intel intergrated

did you run```
 sudo update-grub
```?


theyre kernel boot options
they each do something

like quiet tell the kernel to not write to screen while booting

yeas, i've done sudo-update grub.

problem is that with or without "quite splash" the screen at the boot is always black.

but this is another problem.

---

### Post by idoitprone on 2012-03-22
> **overkill22 said:**
> yeas, i've done sudo-update grub.

problem is that with or without "quite splash" the screen at the boot is always black.

but this is another problem.

oh crp. i did a newbie mistake.

I forgot to tell you to add

```
nomodeset
```

to the kernel parameters

Nvidia binary blobs do not use kms so it will boot a black screen.

srry. I forgot to mention it

---

### Post by overkill22 on 2012-03-22
> **idoitprone said:**
> oh crp. i did a newbie mistake.

I forgot to tell you to add

```
nomodeset
```to the kernel parameters

Nvidia binary blobs do not use kms so it will boot a black screen.

srry. I forgot to mention it

and where i have to put it ?

---

### Post by idoitprone on 2012-03-22
> **overkill22 said:**
> and where i have to put it ?

GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash pcie_aspm=force acpi_osi=Linux **nomodeset**&#8243;

---

### Post by overkill22 on 2012-03-23
> **idoitprone said:**
> GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash pcie_aspm=force acpi_osi=Linux **nomodeset**&#8243;

nothing to do....the pc is every day slower...
then now i see the battery full 91% and remaining time **8 minuts** ...
i'm going to hate lubuntu...

---

### Post by idoitprone on 2012-03-23
> **overkill22 said:**
> nothing to do....the pc is every day slower...
then now i see the battery full 91% and remaining time **8 minuts** ...
i'm going to hate lubuntu...



ok i stumped

unless ur problem is actually that stupid hardware bug that every keeps calling it the linux power regression
then  you have to install kernel 3.3 backport

remove aspm=force 
its pointless
kernel 3.3 fixes the problem by emulating windows which is the non standard way of handling the aspm specs

here the link for the precise kernel and header. It might work. download both and install it
Boot into both to see if it fixes you problem, but you might have to install nvidia blob again if it is not set up properly
if you have 32 bit
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.3-precise/linux-image-3.3.0-030300-generic_3.3.0-030300.201203182135_i386.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.3-precise/linux-image-3.3.0-030300-generic_3.3.0-030300.201203182135_i386.deb")
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.3-precise/linux-headers-3.3.0-030300-generic_3.3.0-030300.201203182135_i386.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.3-precise/linux-headers-3.3.0-030300-generic_3.3.0-030300.201203182135_i386.deb")

if you have a 64 bit 
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.3-precise/linux-headers-3.3.0-030300-generic_3.3.0-030300.201203182135_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.3-precise/linux-headers-3.3.0-030300-generic_3.3.0-030300.201203182135_amd64.deb)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.3-precise/linux-image-3.3.0-030300-generic_3.3.0-030300.201203182135_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.3-precise/linux-image-3.3.0-030300-generic_3.3.0-030300.201203182135_amd64.deb)

---

