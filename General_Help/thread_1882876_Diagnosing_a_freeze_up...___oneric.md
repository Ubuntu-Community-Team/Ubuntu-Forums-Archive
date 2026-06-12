---
title: "Diagnosing a freeze up...   oneric"
date: 2011-11-18
forum: General Help
---

### Post by ZootHornRollo on 2011-11-18
Hi,

I'll need to be quick and post this before my system freezes.

Randomly, sometimes 2 mins after boot up, sometimes 20 minutes, and anywhere in between my system freezes.  The screen freezes on and no inputs (keyboard, touchpad, usb mouse) appear to do anything.

can anyone advise on the best way to diagnose what is causing the freeze up?

---

### Post by lotharmat on 2011-11-18
This occasionally happens to me!

---

### Post by Orange_and_Green on 2011-11-18
Is this a new computer / old computer that had not been used for a long time, or was it fine until recently under a different version of Ubuntu/different distro, and started showing this freezing behaviour only after you installed oneiric?

Also, how did you install oneiric, fresh install or upgrade?

---

### Post by matt_symes on 2011-11-18
Hi

Is this a kernel freeze or x freezing ?

Can you reboot using the magic key combination when frozen ?

Is the caps lock light flashing ?

Boot into multi-user text mode, so it does not boot into X, and leave it. Does it freeze after a period of time ?

You can also stop X after from a virtual terminal to test that.

That will cut your search down by half.

Make and model of your system and all the hardware info please.

What do the logs say ?

Kind regards

---

### Post by ZootHornRollo on 2011-11-19
> **Orange_and_Green said:**
> Is this a new computer / old computer that had not been used for a long time, or was it fine until recently under a different version of Ubuntu/different distro, and started showing this freezing behaviour only after you installed oneiric?

Also, how did you install oneiric, fresh install or upgrade?

hi,

its a laptop i have been running ubuntu on since 10.04 - an HP NC6400 and i've never had an issue.  Only after a fresh install (retaining /home) did the problem arise.

---

### Post by ZootHornRollo on 2011-11-19
> **matt_symes said:**
> Hi

Is this a kernel freeze or x freezing ? - [COLOR="Blue"]how would i tell?  there is no response at all from keyboard/mouse/touchpad[/COLOR]

Can you reboot using the magic key combination when frozen ? [COLOR="Blue"]see above[/COLOR]

Is the caps lock light flashing ? [COLOR="Blue"]ironically it has run just fine all day today so i haven't had a chance to check[/COLOR]

Boot into multi-user text mode, so it does not boot into X, and leave it. Does it freeze after a period of time ? [COLOR="Blue"]not sure how to do this?[/COLOR]

You can also stop X after from a virtual terminal to test that.

That will cut your search down by half.

Make and model of your system and all the hardware info please.

What do the logs say ? [COLOR="Blue"]if you point me in the right direction i can tell you[/COLOR]

Kind regards

thanks

---

### Post by ZootHornRollo on 2011-11-19
just to add...

i have gnome-shell 3.2 and it freezes equally using that as it does unity

---

### Post by matt_symes on 2011-11-19
Hi

I'll cover my question in more detail one by one for you.

> Is this a kernel freeze or x freezing ?Please see below.

> Can you reboot using the magic key combination when frozen ?The magic key combination will help you reboot unless you have had a major kernel crash. It will work even if X has frozen.

Press and hold 'RIGHT ATL' and SysReq keys together and with your other hand it these key one after another giving 5 seconds between each key press.

r e i s u b

That is busier backwards.

Practice it before you have a crash so you can see it in action.

> Is the caps lock light flashing ?The caps lock light will flash if you have had a kernel panic. If the kernel has had a panic there are times when the light will not flash but if it is flashing then it is indicative of a kernel panic.

> 
Boot into multi-user text mode, so it does not boot into X, and leave it. Does it freeze after a period of time ?

You can also stop X after from a virtual terminal to test that.This is another test to see if it is the kernel or X crashing. The easiest way is this. After you log in press ctrl alt and F1 together at the same time. This will display VT1. Enter your user name and password. Your password will not be echoed to the screen. Then type

```
sudo service lightdm stop
```Leave it running over night and check in the morning whether it has frozen

To restart

```
sudo service lightdm start
```> That will cut your search down by half.The whole idea of the above is to narrow down the two main parts that can cause your freezes.

> Make and model of your system and all the hardware info please.Open a terminal and type

> sudo lshwPost the results back here by copying (highlight text in the terminal, right click, copy) and pasting into your next post between code tags (# button abive where you type your reply)

```
like this
```> What do the logs say ?Your logs are kept in the folder /var/log.

Look in /var/log/syslog and /var/log/Xorg.0.log to start with.

Kind regards

---

### Post by Bobhuber on 2011-11-19
> **ZootHornRollo said:**
> Hi,

I'll need to be quick and post this before my system freezes.

Randomly, sometimes 2 mins after boot up, sometimes 20 minutes, and anywhere in between my system freezes.  The screen freezes on and no inputs (keyboard, touchpad, usb mouse) appear to do anything.

can anyone advise on the best way to diagnose what is causing the freeze up?
You answered your own question. Your using your old home directory. Old and new system files do not play nicely with each other.And yes there are plenty of files in your home directory used by the system.

---

### Post by minork on 2011-11-21
> **Bobhuber said:**
> You answered your own question. Your using your old home directory. Old and new system files do not play nicely with each other.And yes there are plenty of files in your home directory used by the system.

I'm afraid it's not that simple. I've done several fresh installs of Ubuntu on my nc6400 and (i think) that from 10.10 the system freezes every now and then. I also think (not sure...) that this happens more frequently on 64-bit versions. 10.04 LTS 32-bit is so far stable.
It happens on other variations of Ubuntu as well, like xubuntu and Linux mint.

As a side note, windows 7 64-bit also sometimes blue screens with the following message: "A clock interrupt was not received on a secondary processor within the allocated time interval".
When it happens (both Ubuntu freeze and windows BSOD) the laptop feels warm.

My bios is the latest available.

---

### Post by ZootHornRollo on 2011-11-21
> **matt_symes said:**
> Hi

I'll cover my question in more detail one by one for you.

Please see below.

[COLOR="Red"]The magic key combination will help you reboot unless you have had a major kernel crash. It will work even if X has frozen.

Press and hold 'RIGHT ATL' and SysReq keys together and with your other hand it these key one after another giving 5 seconds between each key press.

r e i s u b

That is busier backwards.[/COLOR][COLOR="Blue"]Yes, i can reboot using the instructions given[/COLOR]

Practice it before you have a crash so you can see it in action.

[COLOR="Red"]The caps lock light will flash if you have had a kernel panic. If the kernel has had a panic there are times when the light will not flash but if it is flashing then it is indicative of a kernel panic.[/COLOR][COLOR="Blue"] The caplock light does not flash but the wifi light continues to flicker as if in use[/COLOR]

This is another test to see if it is the kernel or X crashing. The easiest way is this. After you log in press ctrl alt and F1 together at the same time. This will display VT1. Enter your user name and password. Your password will not be echoed to the screen. Then type
[COLOR="Red"]
```
sudo service lightdm stop
```Leave it running over night and check in the morning whether it has frozen

To restart

```
sudo service lightdm start
```The whole idea of the above is to narrow down the two main parts that can cause your freezes.[/COLOR] [COLOR="Blue"] - I will try this tonight[/COLOR]



Many thanks for taking the time to assist.

---

### Post by ZootHornRollo on 2011-11-21
My laptop is an HP NC6400

```
graham@Crafter:~$ sudo lshw 
[sudo] password for graham: 
crafter                   
    description: Notebook
    version: F.0B
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4
    configuration: boot=normal chassis=notebook family=103C_5336AN sku=RN434UC#ABU uuid=FA720813-AE09-DC11-1E84-66990E2ED129
  *-core
       description: Motherboard
       product: 30AD
       vendor: Hewlett-Packard
       physical id: 0
       version: KBC Version 56.34
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 0
          version: 68YCU Ver. F.0B
          date: 09/05/2007
          size: 128KiB
          capacity: 960KiB
          capabilities: pci pcmcia pnp upgrade shadowing cdboot bootselect edd int13floppy720 int5printscreen int9keyboard int14serial int17printer acpi usb ls120boot smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.15.6
          serial: 0000-06F6-0000-0000-0000-0000
          slot: U10
          size: 2GHz
          capacity: 2GHz
          width: 64 bits
          clock: 166MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm tpr_shadow cpufreq
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: Internal L1 Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: burst internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: Internal L2 Cache
             size: 4MiB
             capacity: 4MiB
             capabilities: burst external write-back unified
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: a
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: SODIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: 9905295-045.A01LF
             vendor: Kingston
             physical id: 0
             serial: 8F17E228
             slot: DIMM #1
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: SODIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: 16HTF25664HY-667E1
             vendor: Micron Technology
             physical id: 1
             serial: E314DAF7
             slot: DIMM #2
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-pci
          description: Host bridge
          product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:f4600000-f467ffff ioport:4000(size=8) memory:e0000000-efffffff memory:f4680000-f46bffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:f4700000-f477ffff
        *-multimedia
             description: Audio device
             product: N10/ICH 7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:45 memory:f4780000-f4783fff
        *-pci:0
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:7000(size=4096) memory:f4100000-f41fffff ioport:dc400000(size=2097152)
           *-network
                description: Ethernet interface
                product: NetXtreme BCM5753M Gigabit Ethernet PCI Express
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:08:00.0
                logical name: eth0
                version: 21
                serial: 00:16:d4:f0:da:42
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.119 firmware=5753m-v3.56 latency=0 link=no multicast=yes port=twisted pair
                resources: irq:46 memory:f4100000-f410ffff
        *-pci:1
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:6000(size=4096) memory:f4000000-f40fffff ioport:dc200000(size=2097152)
           *-network
                description: Wireless interface
                product: PRO/Wireless 3945ABG [Golan] Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:10:00.0
                logical name: wlan0
                version: 02
                serial: 00:1b:77:22:97:75
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwl3945 driverversion=3.0.0-12-generic firmware=15.32.2.9 ip=192.168.1.9 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
                resources: irq:44 memory:f4000000-f4000fff
        *-pci:2
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:2000(size=8192) memory:f0000000-f3ffffff ioport:dc000000(size=2097152)
        *-usb:0
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:20 ioport:4020(size=32)
        *-usb:1
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:22 ioport:4040(size=32)
        *-usb:2
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:4060(size=32)
        *-usb:3
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:4080(size=32)
        *-usb:4
             description: USB Controller
             product: N10/ICH 7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:20 memory:f4784000-f47843ff
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:5000(size=4096) memory:f4200000-f45fffff ioport:d8000000(size=67108864)
           *-pcmcia
                description: CardBus bridge
                product: PCIxx12 Cardbus Controller
                vendor: Texas Instruments
                physical id: 6
                bus info: pci@0000:02:06.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: irq:18 memory:f4200000-f4200fff ioport:5000(size=256) ioport:5400(size=256) memory:d8000000-dbffffff memory:dc800000-dcbfffff
           *-storage
                description: Mass storage controller
                product: 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
                vendor: Texas Instruments
                physical id: 6.2
                bus info: pci@0000:02:06.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm bus_master cap_list
                configuration: driver=tifm_7xx1 latency=64 maxlatency=4 mingnt=7
                resources: irq:18 memory:f4201000-f4201fff
           *-generic
                description: SD Host controller
                product: PCIxx12 SDA Standard Compliant SD Host Controller
                vendor: Texas Instruments
                physical id: 6.3
                bus info: pci@0000:02:06.3
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=64 maxlatency=4 mingnt=7
                resources: irq:22 memory:f4202000-f42020ff
           *-communication UNCLAIMED
                description: Communication controller
                product: PCIxx12 GemCore based SmartCard controller
                vendor: Texas Instruments
                physical id: 6.4
                bus info: pci@0000:02:06.4
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm cap_list
                configuration: latency=0
                resources: memory:f4203000-f4203fff memory:f4204000-f4204fff
        *-isa
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:40a0(size=16)
           *-cdrom
                description: DVD reader
                product: RW/DVD GCC-4247N
                vendor: HL-DT-ST
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.01
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5 status=nodisc
        *-storage
             description: SATA controller
             product: 82801GBM/GHM (ICH7 Family) SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi2
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:43 ioport:13f0(size=8) ioport:15f4(size=4) ioport:1370(size=8) ioport:1574(size=4) ioport:40d0(size=16) memory:f4785000-f47853ff
           *-disk
                description: ATA Disk
                product: ST9160412AS
                vendor: Seagate
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: 0002
                serial: 5VG0EVFB
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=c39a9a07
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 0ee700c1-1a7c-eb48-b4a1-7e973cf0e5fe
                   size: 79GiB
                   capacity: 79GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2011-02-07 12:50:49 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   size: 69GiB
                   capacity: 69GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 2941MiB
                      capabilities: nofs
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /
                      capacity: 14GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,acl,commit=600,barrier=1,data=ordered state=mounted
                 *-logicalvolume:2
                      description: Linux filesystem partition
                      physical id: 7
                      logical name: /dev/sda7
                      logical name: /home
                      capacity: 51GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,user_xattr,acl,commit=600,barrier=1,data=ordered state=mounted

```

---

### Post by ZootHornRollo on 2011-11-21
> **matt_symes said:**
> 

```
like this
```Your logs are kept in the folder /var/log.

Look in /var/log/syslog and /var/log/Xorg.0.log to start with.

Kind regards

last few lines of syslog covering a crash, let me know if you need to see more but it is a substantial amount of text:
```
'gsettings-data-convert.desktop' killed by signal
Nov 21 16:57:52 Crafter gnome-session[1551]: WARNING: Application 'gsettings-data-convert.desktop' killed by signal
Nov 21 16:57:52 Crafter gnome-session[1551]: WARNING: App 'gsettings-data-convert.desktop' respawning too quickly
Nov 21 16:57:52 Crafter gnome-session[1551]: WARNING: Error on restarting session managed app: Component 'gsettings-data-convert.desktop' crashing too quickly
Nov 21 16:57:53 Crafter rtkit-daemon[1442]: Successfully made thread 1646 of process 1646 (n/a) owned by '1000' high priority at nice level -11.
Nov 21 16:57:53 Crafter rtkit-daemon[1442]: Supervising 4 threads of 2 processes of 2 users.
Nov 21 16:57:53 Crafter rtkit-daemon[1442]: Successfully made thread 1647 of process 1646 (n/a) owned by '1000' RT at priority 5.
Nov 21 16:57:53 Crafter rtkit-daemon[1442]: Supervising 5 threads of 2 processes of 2 users.
Nov 21 16:57:53 Crafter rtkit-daemon[1442]: Successfully made thread 1648 of process 1646 (n/a) owned by '1000' RT at priority 5.
Nov 21 16:57:53 Crafter rtkit-daemon[1442]: Supervising 6 threads of 2 processes of 2 users.
Nov 21 16:58:01 Crafter NetworkManager[1037]: <info> (wlan0): IP6 addrconf timed out or failed.
Nov 21 16:58:01 Crafter NetworkManager[1037]: <info> Activation (wlan0) Stage 4 of 5 (IP6 Configure Timeout) scheduled...
Nov 21 16:58:01 Crafter NetworkManager[1037]: <info> Activation (wlan0) Stage 4 of 5 (IP6 Configure Timeout) started...
Nov 21 16:58:01 Crafter NetworkManager[1037]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Nov 21 16:58:01 Crafter NetworkManager[1037]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Nov 21 16:58:01 Crafter NetworkManager[1037]: <info> Activation (wlan0) Stage 4 of 5 (IP6 Configure Timeout) complete.
Nov 21 16:58:23 Crafter dbus[928]: [system] Activating service name='org.freedesktop.UDisks' (using servicehelper)
Nov 21 16:58:23 Crafter dbus[928]: [system] Successfully activated service 'org.freedesktop.UDisks'
Nov 21 16:59:29 Crafter dbus[928]: [system] Activating service name='org.debian.apt' (using servicehelper)
Nov 21 16:59:30 Crafter AptDaemon: INFO: Initializing daemon
Nov 21 16:59:30 Crafter dbus[928]: [system] Successfully activated service 'org.debian.apt'
Nov 21 16:59:30 Crafter AptDaemon: INFO: UpgradeSystem() was called with safe mode: 1
Nov 21 16:59:30 Crafter AptDaemon.Trans: INFO: Simulate was called
Nov 21 16:59:30 Crafter AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/f2f794096d4e4e03b270de36378daf8e
Nov 21 16:59:32 Crafter AptDaemon.Worker: INFO: Upgrade system with safe mode: 1
```

There is a gap of a minute at 16:58:23 - that was when a crash occurred.


Xorg.0.log in its entirety :
```
[    40.369] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[    40.369] X Protocol Version 11, Revision 0
[    40.369] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[    40.369] Current Operating System: Linux Crafter 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:25:36 UTC 2011 i686
[    40.369] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-13-generic root=UUID=02111112-e280-450e-a4e3-1345be13091a ro quiet splash vt.handoff=7
[    40.369] Build Date: 19 October 2011  05:09:41AM
[    40.369] xorg-server 2:1.10.4-1ubuntu4.2 (For technical support please see http://www.ubuntu.com/support) 
[    40.369] Current version of pixman: 0.22.2
[    40.369] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    40.369] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    40.369] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Nov 21 16:57:28 2011
[    40.555] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    41.028] (==) No Layout section.  Using the first Screen section.
[    41.028] (==) No screen section available. Using defaults.
[    41.028] (**) |-->Screen "Default Screen Section" (0)
[    41.028] (**) |   |-->Monitor "<default monitor>"
[    41.028] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    41.028] (==) Automatically adding devices
[    41.028] (==) Automatically enabling devices
[    41.054] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    41.054] 	Entry deleted from font path.
[    41.054] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    41.054] 	Entry deleted from font path.
[    41.054] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    41.054] 	Entry deleted from font path.
[    41.056] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    41.056] 	Entry deleted from font path.
[    41.056] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    41.057] 	Entry deleted from font path.
[    41.079] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    41.079] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    41.079] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    41.079] (II) Loader magic: 0x823ada0
[    41.079] (II) Module ABI versions:
[    41.079] 	X.Org ANSI C Emulation: 0.4
[    41.079] 	X.Org Video Driver: 10.0
[    41.079] 	X.Org XInput driver : 12.3
[    41.079] 	X.Org Server Extension : 5.0
[    41.080] (--) PCI:*(0:0:2:0) 8086:27a2:103c:30ad rev 3, Mem @ 0xf4600000/524288, 0xe0000000/268435456, 0xf4680000/262144, I/O @ 0x00004000/8
[    41.080] (--) PCI: (0:0:2:1) 8086:27a6:103c:30ad rev 3, Mem @ 0xf4700000/524288
[    41.080] (II) Open ACPI successful (/var/run/acpid.socket)
[    41.080] (II) LoadModule: "extmod"
[    41.176] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    41.228] (II) Module extmod: vendor="X.Org Foundation"
[    41.228] 	compiled for 1.10.4, module version = 1.0.0
[    41.228] 	Module class: X.Org Server Extension
[    41.229] 	ABI class: X.Org Server Extension, version 5.0
[    41.229] (II) Loading extension MIT-SCREEN-SAVER
[    41.229] (II) Loading extension XFree86-VidModeExtension
[    41.229] (II) Loading extension XFree86-DGA
[    41.233] (II) Loading extension DPMS
[    41.233] (II) Loading extension XVideo
[    41.233] (II) Loading extension XVideo-MotionCompensation
[    41.233] (II) Loading extension X-Resource
[    41.233] (II) LoadModule: "dbe"
[    41.234] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    41.250] (II) Module dbe: vendor="X.Org Foundation"
[    41.250] 	compiled for 1.10.4, module version = 1.0.0
[    41.250] 	Module class: X.Org Server Extension
[    41.250] 	ABI class: X.Org Server Extension, version 5.0
[    41.250] (II) Loading extension DOUBLE-BUFFER
[    41.250] (II) LoadModule: "glx"
[    41.251] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    41.397] (II) Module glx: vendor="X.Org Foundation"
[    41.397] 	compiled for 1.10.4, module version = 1.0.0
[    41.397] 	ABI class: X.Org Server Extension, version 5.0
[    41.397] (==) AIGLX enabled
[    41.397] (II) Loading extension GLX
[    41.397] (II) LoadModule: "record"
[    41.398] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    41.423] (II) Module record: vendor="X.Org Foundation"
[    41.423] 	compiled for 1.10.4, module version = 1.13.0
[    41.423] 	Module class: X.Org Server Extension
[    41.423] 	ABI class: X.Org Server Extension, version 5.0
[    41.423] (II) Loading extension RECORD
[    41.423] (II) LoadModule: "dri"
[    41.424] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    41.436] (II) Module dri: vendor="X.Org Foundation"
[    41.436] 	compiled for 1.10.4, module version = 1.0.0
[    41.436] 	ABI class: X.Org Server Extension, version 5.0
[    41.436] (II) Loading extension XFree86-DRI
[    41.436] (II) LoadModule: "dri2"
[    41.436] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    41.447] (II) Module dri2: vendor="X.Org Foundation"
[    41.447] 	compiled for 1.10.4, module version = 1.2.0
[    41.447] 	ABI class: X.Org Server Extension, version 5.0
[    41.447] (II) Loading extension DRI2
[    41.447] (==) Matched intel as autoconfigured driver 0
[    41.447] (==) Matched vesa as autoconfigured driver 1
[    41.447] (==) Matched fbdev as autoconfigured driver 2
[    41.447] (==) Assigned the driver to the xf86ConfigLayout
[    41.447] (II) LoadModule: "intel"
[    41.447] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    41.509] (II) Module intel: vendor="X.Org Foundation"
[    41.509] 	compiled for 1.10.4, module version = 2.15.901
[    41.509] 	Module class: X.Org Video Driver
[    41.509] 	ABI class: X.Org Video Driver, version 10.0
[    41.509] (II) LoadModule: "vesa"
[    41.509] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    41.517] (II) Module vesa: vendor="X.Org Foundation"
[    41.517] 	compiled for 1.10.2, module version = 2.3.0
[    41.517] 	Module class: X.Org Video Driver
[    41.517] 	ABI class: X.Org Video Driver, version 10.0
[    41.517] (II) LoadModule: "fbdev"
[    41.518] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    41.571] (II) Module fbdev: vendor="X.Org Foundation"
[    41.571] 	compiled for 1.10.0, module version = 0.4.2
[    41.571] 	ABI class: X.Org Video Driver, version 10.0
[    41.571] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
	Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
	Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
	Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
	Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server
[    41.571] (II) VESA: driver for VESA chipsets: vesa
[    41.571] (II) FBDEV: driver for framebuffer: fbdev
[    41.571] (++) using VT number 7

[    41.573] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    41.573] (WW) Falling back to old probe method for vesa
[    41.573] (WW) Falling back to old probe method for fbdev
[    41.573] (II) Loading sub module "fbdevhw"
[    41.573] (II) LoadModule: "fbdevhw"
[    41.574] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    41.594] (II) Module fbdevhw: vendor="X.Org Foundation"
[    41.594] 	compiled for 1.10.4, module version = 0.0.2
[    41.594] 	ABI class: X.Org Video Driver, version 10.0
[    41.594] drmOpenDevice: node name is /dev/dri/card0
[    41.594] drmOpenDevice: open result is 12, (OK)
[    41.594] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    41.594] drmOpenDevice: node name is /dev/dri/card0
[    41.594] drmOpenDevice: open result is 12, (OK)
[    41.594] drmOpenByBusid: drmOpenMinor returns 12
[    41.594] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    41.595] (II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    41.595] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    41.595] (==) intel(0): RGB weight 888
[    41.595] (==) intel(0): Default visual is TrueColor
[    41.595] (II) intel(0): Integrated Graphics Chipset: Intel(R) 945GM
[    41.595] (--) intel(0): Chipset: "945GM"
[    41.595] (**) intel(0): Relaxed fencing disabled
[    41.595] (**) intel(0): Wait on SwapBuffers? enabled
[    41.595] (**) intel(0): Triple buffering? enabled
[    41.595] (**) intel(0): Framebuffer tiled
[    41.595] (**) intel(0): Pixmaps tiled
[    41.595] (**) intel(0): 3D buffers tiled
[    41.595] (**) intel(0): SwapBuffers wait enabled
[    41.595] (==) intel(0): video overlay key set to 0x101fe
[    41.595] (II) intel(0): Output LVDS1 has no monitor section
[    41.595] (II) intel(0): found backlight control interface /sys/class/backlight/acpi_video0
[    41.624] (II) intel(0): Output VGA1 has no monitor section
[    41.670] (II) intel(0): Output DVI1 has no monitor section
[    42.056] (II) intel(0): Output TV1 has no monitor section
[    42.056] (II) intel(0): EDID for output LVDS1
[    42.056] (II) intel(0): Manufacturer: SEC  Model: 5042  Serial#: 0
[    42.056] (II) intel(0): Year: 2005  Week: 0
[    42.056] (II) intel(0): EDID Version: 1.3
[    42.056] (II) intel(0): Digital Display Input
[    42.056] (II) intel(0): Max Image Size [cm]: horiz.: 30  vert.: 19
[    42.056] (II) intel(0): Gamma: 2.20
[    42.056] (II) intel(0): No DPMS capabilities specified
[    42.056] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    42.056] (II) intel(0): First detailed timing is preferred mode
[    42.056] (II) intel(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
[    42.056] (II) intel(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
[    42.056] (II) intel(0): Manufacturer's mask: 0
[    42.056] (II) intel(0): Supported detailed timing:
[    42.056] (II) intel(0): clock: 105.1 MHz   Image Size:  303 x 190 mm
[    42.056] (II) intel(0): h_active: 1440  h_sync: 1488  h_sync_end 1616 h_blank_end 1920 h_border: 0
[    42.056] (II) intel(0): v_active: 900  v_sync: 906  v_sync_end 909 v_blanking: 912 v_border: 0
[    42.056] (II) intel(0): Unknown vendor-specific block f
[    42.056] (II) intel(0):  SAMSUNG
[    42.056] (II) intel(0):  LTN141WD-L04
[    42.056] (II) intel(0): EDID (in hex):
[    42.056] (II) intel(0): 	00ffffffffffff004ca3425000000000
[    42.056] (II) intel(0): 	000f0103801e13780a87f594574f8c27
[    42.056] (II) intel(0): 	27505400000001010101010101010101
[    42.056] (II) intel(0): 	0101010101010a29a0e051840c303080
[    42.057] (II) intel(0): 	63002fbe100000190000000f00000000
[    42.057] (II) intel(0): 	0000000000e6fa022301000000fe0053
[    42.057] (II) intel(0): 	414d53554e470a2020202020000000fe
[    42.057] (II) intel(0): 	004c544e31343157442d4c30340a002f
[    42.057] (II) intel(0): EDID vendor "SEC", prod id 20546
[    42.057] (II) intel(0): Printing DDC gathered Modelines:
[    42.057] (II) intel(0): Modeline "1440x900"x0.0  105.06  1440 1488 1616 1920  900 906 909 912 -hsync -vsync (54.7 kHz)
[    42.057] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    42.057] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    42.057] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    42.057] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    42.057] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    42.057] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    42.057] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    42.057] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    42.057] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    42.057] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    42.057] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    42.057] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    42.057] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    42.057] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    42.057] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    42.057] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    42.057] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    42.057] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    42.057] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    42.057] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    42.057] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    42.057] (II) intel(0): Printing probed modes for output LVDS1
[    42.057] (II) intel(0): Modeline "1440x900"x60.0  105.06  1440 1488 1616 1920  900 906 909 912 -hsync -vsync (54.7 kHz)
[    42.057] (II) intel(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    42.057] (II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    42.057] (II) intel(0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz)
[    42.057] (II) intel(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
[    42.057] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    42.057] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    42.057] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    42.057] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    42.088] (II) intel(0): EDID for output VGA1
[    42.104] (II) intel(0): EDID for output DVI1
[    42.492] (II) intel(0): EDID for output TV1
[    42.492] (II) intel(0): Output LVDS1 connected
[    42.492] (II) intel(0): Output VGA1 disconnected
[    42.492] (II) intel(0): Output DVI1 disconnected
[    42.492] (II) intel(0): Output TV1 disconnected
[    42.493] (II) intel(0): Using exact sizes for initial modes
[    42.493] (II) intel(0): Output LVDS1 using initial mode 1440x900
[    42.493] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    42.493] (II) intel(0): Kernel page flipping support detected, enabling
[    42.493] (**) intel(0): Display dimensions: (300, 190) mm
[    42.493] (**) intel(0): DPI set to (121, 120)
[    42.493] (II) Loading sub module "fb"
[    42.493] (II) LoadModule: "fb"
[    42.493] (II) Loading /usr/lib/xorg/modules/libfb.so
[    42.507] (II) Module fb: vendor="X.Org Foundation"
[    42.507] 	compiled for 1.10.4, module version = 1.0.0
[    42.507] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    42.507] (II) Loading sub module "dri2"
[    42.507] (II) LoadModule: "dri2"
[    42.508] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    42.508] (II) Module dri2: vendor="X.Org Foundation"
[    42.508] 	compiled for 1.10.4, module version = 1.2.0
[    42.508] 	ABI class: X.Org Server Extension, version 5.0
[    42.508] (II) UnloadModule: "vesa"
[    42.508] (II) Unloading vesa
[    42.508] (II) UnloadModule: "fbdev"
[    42.508] (II) Unloading fbdev
[    42.508] (II) UnloadModule: "fbdevhw"
[    42.508] (II) Unloading fbdevhw
[    42.508] (==) Depth 24 pixmap format is 32 bpp
[    42.508] (II) intel(0): [DRI2] Setup complete
[    42.508] (II) intel(0): [DRI2]   DRI driver: i915
[    42.508] (II) intel(0): Allocated new frame buffer 1472x900 stride 8192, tiled
[    42.530] (II) UXA(0): Driver registered support for the following operations:
[    42.530] (II)         solid
[    42.530] (II)         copy
[    42.530] (II)         composite (RENDER acceleration)
[    42.530] (II)         put_image
[    42.530] (II)         get_image
[    42.530] (==) intel(0): Backing store disabled
[    42.530] (==) intel(0): Silken mouse enabled
[    42.531] (II) intel(0): Initializing HW Cursor
[    42.560] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    42.564] (==) intel(0): DPMS enabled
[    42.564] (==) intel(0): Intel XvMC decoder disabled
[    42.564] (II) intel(0): Set up textured video
[    42.564] (II) intel(0): Set up overlay video
[    42.564] (II) intel(0): direct rendering: DRI2 Enabled
[    42.564] (==) intel(0): hotplug detection: "enabled"
[    42.564] (--) RandR disabled
[    42.564] (II) Initializing built-in extension Generic Event Extension
[    42.564] (II) Initializing built-in extension SHAPE
[    42.564] (II) Initializing built-in extension MIT-SHM
[    42.564] (II) Initializing built-in extension XInputExtension
[    42.564] (II) Initializing built-in extension XTEST
[    42.564] (II) Initializing built-in extension BIG-REQUESTS
[    42.564] (II) Initializing built-in extension SYNC
[    42.564] (II) Initializing built-in extension XKEYBOARD
[    42.564] (II) Initializing built-in extension XC-MISC
[    42.564] (II) Initializing built-in extension SECURITY
[    42.564] (II) Initializing built-in extension XINERAMA
[    42.564] (II) Initializing built-in extension XFIXES
[    42.564] (II) Initializing built-in extension RENDER
[    42.564] (II) Initializing built-in extension RANDR
[    42.564] (II) Initializing built-in extension COMPOSITE
[    42.564] (II) Initializing built-in extension DAMAGE
[    42.564] (II) Initializing built-in extension GESTURE
[    42.814] (II) AIGLX: Trying DRI driver /usr/lib/i386-linux-gnu/dri/i915_dri.so
[    42.910] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    42.910] (II) AIGLX: enabled GLX_INTEL_swap_event
[    42.910] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    42.910] (II) AIGLX: enabled GLX_SGI_make_current_read
[    42.910] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    42.910] (II) AIGLX: Loaded and initialized i915
[    42.910] (II) GLX: Initialized DRI2 GL provider for screen 0
[    42.911] (II) intel(0): Setting screen physical size to 380 x 238
[    43.229] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    43.252] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    43.252] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    43.252] (II) LoadModule: "evdev"
[    43.253] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    43.320] (II) Module evdev: vendor="X.Org Foundation"
[    43.320] 	compiled for 1.10.2, module version = 2.6.0
[    43.320] 	Module class: X.Org XInput Driver
[    43.320] 	ABI class: X.Org XInput driver, version 12.3
[    43.320] (II) Using input driver 'evdev' for 'Power Button'
[    43.320] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    43.320] (**) Power Button: always reports core events
[    43.320] (**) Power Button: Device: "/dev/input/event2"
[    43.320] (--) Power Button: Found keys
[    43.320] (II) Power Button: Configuring as keyboard
[    43.320] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    43.320] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    43.320] (**) Option "xkb_rules" "evdev"
[    43.320] (**) Option "xkb_model" "pc105"
[    43.320] (**) Option "xkb_layout" "gb"
[    43.323] (II) XKB: reuse xkmfile /var/lib/xkb/server-2B4266AA55228AE7D9557A18F1965DBA19850816.xkm
[    43.325] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[    43.325] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    43.325] (II) Using input driver 'evdev' for 'Video Bus'
[    43.325] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    43.325] (**) Video Bus: always reports core events
[    43.325] (**) Video Bus: Device: "/dev/input/event4"
[    43.325] (--) Video Bus: Found keys
[    43.325] (II) Video Bus: Configuring as keyboard
[    43.325] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input4/event4"
[    43.325] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    43.325] (**) Option "xkb_rules" "evdev"
[    43.325] (**) Option "xkb_model" "pc105"
[    43.326] (**) Option "xkb_layout" "gb"
[    43.331] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[    43.331] (II) No input driver/identifier specified (ignoring)
[    43.331] (II) config/udev: Adding input device Sleep Button (/dev/input/event0)
[    43.331] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    43.331] (II) Using input driver 'evdev' for 'Sleep Button'
[    43.331] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    43.331] (**) Sleep Button: always reports core events
[    43.331] (**) Sleep Button: Device: "/dev/input/event0"
[    43.331] (--) Sleep Button: Found keys
[    43.331] (II) Sleep Button: Configuring as keyboard
[    43.331] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input0/event0"
[    43.332] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    43.332] (**) Option "xkb_rules" "evdev"
[    43.332] (**) Option "xkb_model" "pc105"
[    43.332] (**) Option "xkb_layout" "gb"
[    43.343] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    43.343] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    43.343] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    43.343] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    43.343] (**) AT Translated Set 2 keyboard: always reports core events
[    43.343] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    43.343] (--) AT Translated Set 2 keyboard: Found keys
[    43.343] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    43.343] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    43.343] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    43.343] (**) Option "xkb_rules" "evdev"
[    43.343] (**) Option "xkb_model" "pc105"
[    43.343] (**) Option "xkb_layout" "gb"
[    43.344] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event7)
[    43.344] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    43.344] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    43.344] (II) LoadModule: "synaptics"
[    43.344] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    43.347] (II) Module synaptics: vendor="X.Org Foundation"
[    43.347] 	compiled for 1.10.4, module version = 1.4.1
[    43.347] 	Module class: X.Org XInput Driver
[    43.347] 	ABI class: X.Org XInput driver, version 12.3
[    43.347] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    43.347] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    43.347] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    43.347] (**) Option "Device" "/dev/input/event7"
[    43.372] (--) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
[    43.372] (--) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
[    43.372] (--) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    43.372] (--) SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    43.372] (--) SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    43.396] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    43.396] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    43.420] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio4/input/input7/event7"
[    43.420] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    43.420] (**) SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    43.420] (**) SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[    43.420] (**) SynPS/2 Synaptics TouchPad: AccelFactor is now 0.040
[    43.420] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    43.420] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    43.420] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    43.420] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    43.420] (II) SynPS/2 Synaptics TouchPad: failed to open grail, no gesture support
[    43.420] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    43.420] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    43.420] (II) No input driver/identifier specified (ignoring)
[    43.421] (II) config/udev: Adding input device PS/2 Generic Mouse (/dev/input/event8)
[    43.421] (**) PS/2 Generic Mouse: Applying InputClass "evdev pointer catchall"
[    43.421] (II) Using input driver 'evdev' for 'PS/2 Generic Mouse'
[    43.421] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    43.421] (**) PS/2 Generic Mouse: always reports core events
[    43.421] (**) PS/2 Generic Mouse: Device: "/dev/input/event8"
[    43.421] (--) PS/2 Generic Mouse: Found 3 mouse buttons
[    43.421] (--) PS/2 Generic Mouse: Found relative axes
[    43.421] (--) PS/2 Generic Mouse: Found x and y relative axes
[    43.421] (II) PS/2 Generic Mouse: Configuring as mouse
[    43.421] (**) PS/2 Generic Mouse: YAxisMapping: buttons 4 and 5
[    43.421] (**) PS/2 Generic Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    43.421] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio4/serio5/input/input8/event8"
[    43.421] (II) XINPUT: Adding extended input device "PS/2 Generic Mouse" (type: MOUSE)
[    43.421] (II) PS/2 Generic Mouse: initialized for relative axes.
[    43.421] (**) PS/2 Generic Mouse: (accel) keeping acceleration scheme 1
[    43.421] (**) PS/2 Generic Mouse: (accel) acceleration profile 0
[    43.421] (**) PS/2 Generic Mouse: (accel) acceleration factor: 2.000
[    43.421] (**) PS/2 Generic Mouse: (accel) acceleration threshold: 4
[    43.422] (II) config/udev: Adding input device PS/2 Generic Mouse (/dev/input/mouse1)
[    43.422] (II) No input driver/identifier specified (ignoring)
[    43.422] (II) config/udev: Adding input device ST LIS3LV02DL Accelerometer (/dev/input/event5)
[    43.422] (II) No input driver/identifier specified (ignoring)
[    43.422] (II) config/udev: Adding input device ST LIS3LV02DL Accelerometer (/dev/input/js0)
[    43.422] (II) No input driver/identifier specified (ignoring)
[    43.429] (II) config/udev: Adding input device HP WMI hotkeys (/dev/input/event6)
[    43.429] (**) HP WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    43.429] (II) Using input driver 'evdev' for 'HP WMI hotkeys'
[    43.429] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    43.429] (**) HP WMI hotkeys: always reports core events
[    43.429] (**) HP WMI hotkeys: Device: "/dev/input/event6"
[    43.429] (--) HP WMI hotkeys: Found keys
[    43.429] (II) HP WMI hotkeys: Configuring as keyboard
[    43.429] (**) Option "config_info" "udev:/sys/devices/virtual/input/input6/event6"
[    43.429] (II) XINPUT: Adding extended input device "HP WMI hotkeys" (type: KEYBOARD)
[    43.429] (**) Option "xkb_rules" "evdev"
[    43.429] (**) Option "xkb_model" "pc105"
[    43.429] (**) Option "xkb_layout" "gb"
[    48.661] (II) intel(0): EDID vendor "SEC", prod id 20546
[    48.661] (II) intel(0): Printing DDC gathered Modelines:
[    48.661] (II) intel(0): Modeline "1440x900"x0.0  105.06  1440 1488 1616 1920  900 906 909 912 -hsync -vsync (54.7 kHz)
[    53.606] (II) intel(0): EDID vendor "SEC", prod id 20546
[    53.606] (II) intel(0): Printing DDC gathered Modelines:
[    53.606] (II) intel(0): Modeline "1440x900"x0.0  105.06  1440 1488 1616 1920  900 906 909 912 -hsync -vsync (54.7 kHz)
[    58.178] (II) intel(0): EDID vendor "SEC", prod id 20546
[    58.178] (II) intel(0): Printing DDC gathered Modelines:
[    58.178] (II) intel(0): Modeline "1440x900"x0.0  105.06  1440 1488 1616 1920  900 906 909 912 -hsync -vsync (54.7 kHz)
[    62.765] (II) intel(0): EDID vendor "SEC", prod id 20546
[    62.765] (II) intel(0): Printing DDC gathered Modelines:
[    62.765] (II) intel(0): Modeline "1440x900"x0.0  105.06  1440 1488 1616 1920  900 906 909 912 -hsync -vsync (54.7 kHz)
[    63.188] (II) intel(0): EDID vendor "SEC", prod id 20546
[    63.188] (II) intel(0): Printing DDC gathered Modelines:
[    63.188] (II) intel(0): Modeline "1440x900"x0.0  105.06  1440 1488 1616 1920  900 906 909 912 -hsync -vsync (54.7 kHz)
[    94.224] (II) intel(0): EDID vendor "SEC", prod id 20546
[    94.224] (II) intel(0): Printing DDC gathered Modelines:
[    94.224] (II) intel(0): Modeline "1440x900"x0.0  105.06  1440 1488 1616 1920  900 906 909 912 -hsync -vsync (54.7 kHz)
[    96.816] (II) XKB: reuse xkmfile /var/lib/xkb/server-5550814D3DE81657FB75A6E398FC443242E652DD.xkm
```

---

### Post by matt_symes on 2011-11-21
Hi

It sounds like X is crashing or at least something in user space.

> Xorg.0.log in its entirety :That's a bit to read. I'll get back to you :D

Kind regards

---

### Post by minork on 2011-11-27
just installed Linux Mint 12 32-bit on my nc6400 and it freezes in the exact same way. I've been running 10.04.3 LTS for a couple of weeks without any problems.

---

### Post by matt_symes on 2011-11-28
Hi

I can see nothing in the logs posted that would cause a freeze. Are there any clues in the other logs ?

Kind regards

---

### Post by Gonz_91 on 2011-12-05
I don't mean to hijack this thread, but I read through it, and it seems appropriate to post here.

I'm running oneiric (32-bit) on a Toshiba Qosmio F60-118, and am experiencing these crashes/freezes as well, sometimes eve with the flashing caps-lock light (which, as I read earlier, indicates a kernel panic).

I can't even imagine what such a thing is, so I'm asking for someone's help.

I have been using, or trying to use, oneiric for the last few days, but can't get any work done because of this =|

Thanks a lot in advance!

---

### Post by ZootHornRollo on 2012-02-05
Hi,

Still having problems with this so if anyone has any further suggestions it would be appreciated.

Same symptoms are also present in Fedora 16 but not in OpenSUSE 12.1.

Would prefer to run Ubuntu but looks likte ill be forced onto OpenSUSE until the next release.

---

### Post by ZootHornRollo on 2012-05-05
i have now installed 12.04 and experience very similar problems.

However, now before a lockup there is a period of a minute or two where the mouse pointer can still be moved around the screen but clicking on anything does not have any effect.  alt-f2 etc also has no effect.

Any idea what the issue could be?

---

