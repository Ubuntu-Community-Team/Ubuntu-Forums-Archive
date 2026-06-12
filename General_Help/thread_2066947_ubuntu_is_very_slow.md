---
title: "ubuntu is very slow"
date: 2012-10-05
forum: General Help
---

### Post by bentzi259 on 2012-10-05
hi guys ^

i installed ubuntu few days ago because i heard few good things about it , but mostly i heard its extremely fast , however in my computer (i5 cpu 8Gb ram) is extremely slow !!
when i open a program it takes between 6-10 seconds to open it !!
i tried to update and upgrade and downloaded the driver for graphics , didnt hepled

thanks for helpers :)

---

### Post by daslinkard on 2012-10-05
> **bentzi259 said:**
> hi guys ^

i installed ubuntu few days ago because i heard few good things about it , but mostly i heard its extremely fast , however in my computer (i5 cpu 8Gb ram) is extremely slow !!
when i open a program it takes between 6-10 seconds to open it !!
i tried to update and upgrade and downloaded the driver for graphics , didnt hepled

thanks for helpers :)
What is the make and model of your PC?

---

### Post by varunendra on 2012-10-06
> **daslinkard said:**
> What is the make and model of your PC?Is this what you were interested in-
> **bentzi259 said:**
> however in my computer (**[COLOR="Red"]i5 cpu 8Gb ram[/COLOR]**) is extremely slow !!
Obviously, these two knock out the two most common issues - low ram or weak cpu. Nevertheless it would definitely be good to have the rest of the hardware specs, especially - the graphics.

Some other usual suspects for slower performance are:
[LIST]
[*]A dodgy/incorrect driver.
[*]Some external hardware (for example a USB HDD) playing tricks with linux, keeping the system busy in detecting/configurig that device.
[*]It is a WUBI installation 'inside windows', not a native one on its own partition. It sometimes suffers the inherent 'fragmentation' issue of windows os.
[*]The Ubuntu partition is too full to perform decently. Usually a 16 to 26 GB partition-size is recommended for full Ubuntu installation. But this may vary depending on your mount-points layout and any additional packages you install.
[*]Some specific application has gone nuts and is hogging the CPU.
[*]A failing or corrupt hard drive/partition. Given your CPU & RAM specs, it is easy to rule out a failing hard drive scenario, but the chances of a fully or partially corrupt partition may not be completely ruled out.[/LIST]

*@bentzi259*, please, let us know the following:
[LIST=1]
[*]Is it a desktop or a laptop?
[*]The full hardware specs, as asked above.
[*]Which graphics driver have you installed and how? (maybe a link, if you followed a guide or tutorial..)
[*]Is it a full installation on its own partition or a WUBI installation 'inside' windows?
[*]Apparently, Ubuntu is your second OS. Which is the main one (windows??)? Is it performing better compared to Ubuntu? Any examples?
[*]Is all the hardware working correctly in Ubuntu (network, peripherals, etc.)?
[/LIST]

Additionally, please post the outputs of the following:
```
uname -mr
lsb_release -d
df -h
free -m
sudo fdisk -l
dmesg | tail -20
top
```

**PS:**
Oh, and let me clarify something else. Ubuntu is 'usually' "faster" than windows on a given platform. Please note the words 'usually' (not always.. due to various reasons), and 'faster'. If someone says "Extremely fast" for a heavy GUI version like default Ubuntu, it is a lie, whoever told you that. It 'can be' extremely fast, but only at the cost of a lot of GUI and eye-candy stuff.
The reason why linux is and will always be faster than windows (unless one switches its basic kernel architecture to the other's) lies in the basic difference in the kernel architecture. Read about [Microkernel vs. Monolithic kernel]("http://en.wikipedia.org/wiki/Kernel_(computing)#Monolithic_kernels_vs._microkernels") on wikipedia, or search for the same [debate]("http://www.dina.dk/~abraham/Linus_vs_Tanenbaum.html") between [Linus torvalds and Tanenbaum]("http://en.wikipedia.org/wiki/Tanenbaum%E2%80%93Torvalds_debate").

---

### Post by bentzi259 on 2012-10-06
bentzi259@bentzi:~$ uname -mr
3.2.0-31-generic x86_64


--------------------------------------------------------------


bentzi259@bentzi:~$ lsb_release -d
Description:	Ubuntu 12.04.1 LTS


-----------------------------------------------------------------



bentzi259@bentzi:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdb1       105G   12G   89G  12% /
udev            3.9G  4.0K  3.9G   1% /dev
tmpfs           1.6G  832K  1.6G   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            3.9G  284K  3.9G   1% /run/shm

-----------------------------------------------------------------

bentzi259@bentzi:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          7949       7787        162          0         19       6878
-/+ buffers/cache:        888       7060
Swap:         8151          0       8151


---------------------------------------------------------------
151
bentzi259@bentzi:~$ sudo fdisk -l
[sudo] password for bentzi259: 

Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders, total 320173056 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006e1b8

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders, total 240121728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00050388

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   223422463   111710208   83  Linux
/dev/sdb2       223424510   240119807     8347649    5  Extended
/dev/sdb5       223424512   240119807     8347648   82  Linux swap / Solaris

----------------------------------------------------------------


bentzi259@bentzi:~$ dmesg | tail -20
[   21.367928] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.368915] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.722841] type=1400 audit(1349525883.182:10): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=958 comm="apparmor_parser"
[   21.723063] type=1400 audit(1349525883.182:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=958 comm="apparmor_parser"
[   21.723186] type=1400 audit(1349525883.182:12): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=958 comm="apparmor_parser"
[   21.724861] type=1400 audit(1349525883.182:13): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=962 comm="apparmor_parser"
[   21.725117] type=1400 audit(1349525883.182:14): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=962 comm="apparmor_parser"

-------------------------------------------------------------
bentzi259@bentzi:~$ top

top - 16:55:37 up  2:37,  2 users,  load average: 0.14, 0.30, 0.40
Tasks: 168 total,   1 running, 167 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.6%us,  0.1%sy,  0.0%ni, 99.3%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   8140296k total,  7976544k used,   163752k free,    20204k buffers
Swap:  8347644k total,        0k used,  8347644k free,  7041012k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 2761 bentzi25  20   0  651m  66m  28m S    3  0.8   0:34.07 chromium-browse    
 1081 root      20   0  262m 100m  19m S    1  1.3   9:10.44 Xorg               
 2903 bentzi25  20   0  512m  17m  11m S    1  0.2   0:02.85 gnome-terminal     
   63 root      20   0     0    0    0 S    0  0.0   0:15.23 kworker/u:4        
   85 root      20   0     0    0    0 S    0  0.0   0:04.74 kworker/0:2        
 1755 bentzi25  20   0 1307m 145m  41m S    0  1.8   7:14.18 compiz             
 2635 bentzi25  20   0  545m  69m  36m S    0  0.9   0:21.08 chromium-browse    
 2988 bentzi25  20   0 17340 1340  952 R    0  0.0   0:00.07 top                
    1 root      20   0 24440 2432 1360 S    0  0.0   0:00.74 init               
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      20   0     0    0    0 S    0  0.0   0:00.75 ksoftirqd/0        
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0        
    7 root      RT   0     0    0    0 S    0  0.0   0:00.03 watchdog/0         
    8 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1        
   10 root      20   0     0    0    0 S    0  0.0   0:00.76 ksoftirqd/1        
   12 root      RT   0     0    0    0 S    0  0.0   0:00.03 watchdog/1         
   13 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/2
---------------------------------------------------------------

im running on a desktop





---------------------------------------------------------------

this ia my computer :

bentzi259@bentzi:~$ sudo lshw 
[sudo] password for bentzi259: 
bentzi                    
    description: Desktop Computer
    product: To be filled by O.E.M. (To be filled by O.E.M.)
    vendor: Gigabyte Technology Co., Ltd.
    version: To be filled by O.E.M.
    serial: To be filled by O.E.M.
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall32
    configuration: boot=normal chassis=desktop family=To be filled by O.E.M. sku=To be filled by O.E.M. uuid=00020003-0004-0005-0006-000700080009
  *-core
       description: Motherboard
       product: H77M-D3H
       vendor: Gigabyte Technology Co., Ltd.
       physical id: 0
       version: x.x
       serial: To be filled by O.E.M.
       slot: To be filled by O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: F5
          date: 03/29/2012
          size: 64KiB
          capacity: 6080KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification
     *-cache:0
          description: L1 cache
          physical id: 4
          slot: CPU Internal L1
          size: 128KiB
          capacity: 128KiB
          capabilities: internal write-through
     *-cache:1
          description: L2 cache
          physical id: 5
          slot: CPU Internal L2
          size: 1MiB
          capacity: 1MiB
          capabilities: internal write-through instruction
     *-cache:2
          description: L3 cache
          physical id: 6
          slot: CPU Internal L3
          size: 6MiB
          capacity: 6MiB
          capabilities: internal write-back instruction
     *-memory
          description: System Memory
          physical id: 7
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: DIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: F3-10666CL9-4GBNT
             vendor: Fujitsu
             physical id: 0
             serial: 00000000
             slot: ChannelA-DIMM0
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: DIMM [empty]
             product: [Empty]
             vendor: [Empty]
             physical id: 1
             serial: [Empty]
             slot: ChannelA-DIMM1
        *-bank:2
             description: DIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: F3-10666CL9-4GBNT
             vendor: Fujitsu
             physical id: 2
             serial: 00000000
             slot: ChannelB-DIMM0
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:3
             description: DIMM [empty]
             product: [Empty]
             vendor: [Empty]
             physical id: 3
             serial: [Empty]
             slot: ChannelB-DIMM1
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i5-3470 CPU @ 3.20GHz
          vendor: Intel Corp.
          physical id: 43
          bus info: cpu@0
          version: Intel(R) Core(TM) i5-3470 CPU @ 3.20GHz
          slot: Intel(R) Core(TM) i5-3470 CPU @ 3.20GHz
          size: 3600MHz
          capacity: 3600MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid fsgsbase smep erms cpufreq
          configuration: cores=4 enabledcores=1
     *-pci
          description: Host bridge
          product: Ivy Bridge DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
        *-usb:0
             description: USB controller
             product: Panther Point USB xHCI Host Controller
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:41 memory:f7200000-f720ffff
        *-communication
             description: Communication controller
             product: Panther Point MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei latency=0
             resources: irq:42 memory:f7219000-f721900f
        *-usb:1
             description: USB controller
             product: Panther Point USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:f7217000-f72173ff
        *-multimedia
             description: Audio device
             product: Panther Point High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:43 memory:f7210000-f7213fff
        *-pci:0
             description: PCI bridge
             product: Panther Point PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:e000(size=4096) memory:f5000000-f70fffff ioport:e0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: G73 [GeForce 7300 GT]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:f6000000-f6ffffff memory:e0000000-efffffff memory:f5000000-f5ffffff ioport:e000(size=128) memory:f7000000-f701ffff
        *-pci:1
             description: PCI bridge
             product: Panther Point PCI Express Root Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:d000(size=4096) memory:f7100000-f71fffff
           *-network
                description: Ethernet interface
                product: AR8151 v2.0 Gigabit Ethernet
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: c0
                serial: 90:2b:34:1a:e2:f2
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
                resources: irq:44 memory:f7100000-f713ffff ioport:d000(size=128)
        *-pci:2
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1c.6
             bus info: pci@0000:00:1c.6
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm subtractive_decode bus_master cap_list
           *-pci
                description: PCI bridge
                product: Integrated Technology Express, Inc.
                vendor: Integrated Technology Express, Inc.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 30
                width: 32 bits
                clock: 33MHz
                capabilities: pci pm subtractive_decode bus_master cap_list
        *-usb:2
             description: USB controller
             product: Panther Point USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:f7216000-f72163ff
        *-isa
             description: ISA bridge
             product: Panther Point LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: Panther Point 4 port SATA Controller [IDE mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:f0d0(size=8) ioport:f0c0(size=4) ioport:f0b0(size=8) ioport:f0a0(size=4) ioport:f090(size=16) ioport:f080(size=16)
           *-disk
                description: ATA Disk
                product: Maxtor 6L160M0
                vendor: Maxtor
                physical id: 0
                bus info: scsi@0:0.1.0
                logical name: /dev/sda
                version: BANC
                serial: L398ZY3G
                size: 152GiB (163GB)
                configuration: ansiversion=5 signature=0006e1b8
           *-cdrom
                description: DVD-RAM writer
                product: CDDVDW SH-S223C
                vendor: TSSTcorp
                physical id: 1
                bus info: scsi@1:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/sr0
                version: SB02
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: Panther Point SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 04
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f7215000-f72150ff ioport:f000(size=32)
        *-ide:1
             description: IDE interface
             product: Panther Point 2 port SATA Controller [IDE mode]
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             logical name: scsi3
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:f070(size=8) ioport:f060(size=4) ioport:f050(size=8) ioport:f040(size=4) ioport:f030(size=16) ioport:f020(size=16)
           *-disk
                description: ATA Disk
                product: Maxtor 6Y120M0
                vendor: Maxtor
                physical id: 0.0.0
                bus info: scsi@3:0.0.0
                logical name: /dev/sdb
                version: YAR5
                serial: Y3NWCDNE
                size: 114GiB (122GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=00050388
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@3:0.0.0,1
                   logical name: /dev/sdb1
                   logical name: /
                   version: 1.0
                   serial: 3b6dee03-981a-4efc-bd0c-11bc62fc7047
                   size: 106GiB
                   capacity: 106GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2012-10-06 13:21:23 filesystem=ext4 lastmountpoint=/ modified=2012-10-06 13:35:18 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,barrier=1,data=ordered mounted=2012-10-06 14:17:52 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@3:0.0.0,2
                   logical name: /dev/sdb2
                   size: 8152MiB
                   capacity: 8152MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sdb5
                      capacity: 8152MiB
                      capabilities: nofs
  *-power UNCLAIMED
       description: To Be Filled By O.E.M.
       product: To Be Filled By O.E.M.
       vendor: To Be Filled By O.E.M.
       physical id: 1
       version: To Be Filled By O.E.M.
       serial: To Be Filled By O.E.M.
       capacity: 32768mWh
  *-network
       description: Wireless interface
       physical id: 2
       bus info: usb@1:1.3
       logical name: wlan0
       serial: 00:a1:b0:20:1d:6d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt73usb driverversion=3.2.0-31-generic firmware=1.7 ip=192.168.1.106 link=yes multicast=yes wireless=IEEE 802.11bg

---

### Post by offgridguy on 2012-10-06
I find ubuntu faster than windows, but not remarkably faster,  I attribute part of that to the
fact that I use Norton anti-virus with windows and use no anti-virus program with ubuntu.

---

### Post by varunendra on 2012-10-07
*bentzi259,*
First off, I'd request you to edit your last post to wrap the outputs within [noparse]```
..and..
```[/noparse] tags. Make it a habit for posting output codes.

To do so, either click on the **#** symbol at the top to auto-generate the pair of tags, then cut-paste the code part in-between them, or just highlight the desired text with mouse cursor, then click on the same **#** symbol.

Doing so preserves the formatting of the output & puts the code in a nice box, thus making post neat and easily readable.


On to the issue now.
Everything seems good so far (although you didn't post all 20 lines of the dmesg command).

And what is that **160GB HDD** there for? Isn't it partitioned yet? By the outputs your system seems to be Ubuntu-only, so we don't have a second OS to compare speeds against.

By the way, I forgot to mention earlier, 4-6 sec. for opening apps (for the first time) like firefox or libre-office is not abnormal IMHO, regardless of how powerful the CPU you have. These speeds are limited by disk I/O speeds, which is not very fast for regular hard drives. However, anything above 6 sec. for normal apps like these is definitely too slow! Also, they should open up much faster if they have been closed very recently and are re-opened (due to most of their part being cached in memory).

So please give us some examples of applications you are experiencing long delays in, and the time they take to get ready.

Also, how is the performance of the same apps (open-closed more than once) if you run a live session from the Live cd/usb ?

And don't forget to wrap the codes in your previous post in 'code' tags :). You'll like what it does.
(more about BB codes with examples : [http://ubuntuforums.org/misc.php?do=bbcode](http://ubuntuforums.org/misc.php?do=bbcode))

PS:
All those smileys with goggles in your outputs were originally "8"s followed by a closed brace ")". eg- ```
(size=12**[COLOR="Red"]8)[/COLOR]**
```. That's also what code tag does- prevents such codes from turning into funny smileys ! ;)

[COLOR="Red"][I]PPS:
Off the track, but I'm too pissed off !:mad:
To all my fellow Indians reading this post, never trust TataDocomo GSM for your ISP. Their service is the crappiest of the 8-9 ISPs I've tried so far - guaranteed to disconnect after every 20-22MB, often even every 2-3 min. in daytime![/I][/COLOR]

---

