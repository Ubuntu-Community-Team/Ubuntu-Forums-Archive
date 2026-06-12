---
title: "please help"
date: 2010-10-24
forum: General Help
---

### Post by IDontKnowWhatIAmDoing on 2010-10-24
I was just curious as to why my grub menu is so crowded. This is what it looks like...

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-25-generic
Found initrd image: /boot/initrd.img-2.6.32-25-generic
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda3
Found Ubuntu 10.04 LTS (10.04) on /dev/sda6
done

I would like to clean it up a bit if that is possible.  

I also am having problems with my system crashing randomly.
Any help would be greatly appreciated, thanks!

---

### Post by lindsay7 on 2010-10-25
Ubuntu will keep old kernal versions in grub, there are a number of ways to clean this up. One is to go to synapic package manager found under system/administration and deleting the old kernals there.  An other is to install "Ubuntu Tweak" and use its utility to delete the old versions there.  You should keep at least the last kernal in grub in case you need to load it to fix any problems that might come up with the version that you use every day.

Here is the info on this.

[http://ubuntuforums.org/showthread.php?t=1587462](http://ubuntuforums.org/showthread.php?t=1587462)

---

### Post by Moozillaaa on 2010-10-25
All good advice; but maybe don't install more stuff, especially if something is going wrong...

We need more crash details - is it while the same application/program is running? Can you pin it down to any function that you're doing?

If so, stop with that program, and see if any problems arise.

If there's NO clue at all what's causing it, try booting an older kernel (oldest first) from your GRUB menu, then do the same stuff, and see what happens.

---

### Post by lindsay7 on 2010-10-25
Also good advise, can you be more specific on what you mean by "system crashing"  there are a lot of definitions on what is meant by this.

---

### Post by IDontKnowWhatIAmDoing on 2010-10-25
well it seems it crashes anytime that i use chrome but when it crashes its very weird, it brings up text that says checking battery status and a bunch of other stuff i cant catch and then it starts flashing vertical white lines. i have had this problem ever since i installed ubuntu, i dont know if it is a physical problem with my computer because its a piece of garbage or what.  i have tried just not using chrome and using firefox but the problem still occurs

---

### Post by lindsay7 on 2010-10-25
Does it crash when you are in windows or ubuntu?

---

### Post by katykat on 2010-10-25
The grub stuff prolly has nothin to to with the crashes. 

Is this laptop or desktop?
How much memory?

Print out a listing of whats in /etc/init.d and post it. 

Alot of stuff insists on installing with daemons and they can conflict.

---

### Post by IDontKnowWhatIAmDoing on 2010-10-27
acpid            hwclock                     reboot
acpi-support     hwclock-save                rsync
alsa-mixer-save  irqbalance                  rsyslog
anacron          kerneloops                  saned
apparmor         killprocs                   screen-cleanup
apport           lm-sensors                  sendsigs
atd              module-init-tools           single
avahi-daemon     networking                  skeleton
binfmt-support   network-interface           speech-dispatcher
bluetooth        network-interface-security  stop-bootlogd
bootlogd         network-manager             stop-bootlogd-single
brltty           ondemand                    udev
console-setup    pcmciautils                 udev-finish
cron             plymouth                    udevmonitor
cups             plymouth-log                udevtrigger
dbus             plymouth-splash             ufw
dmesg            plymouth-stop               umountfs
dns-clean        pppd-dns                    umountnfs.sh
failsafe-x       procps                      umountroot
fancontrol       pulseaudio                  unattended-upgrades
gdm              rc                          urandom
grub-common      rc.local                    wpa-ifupdown
halt             rcS                         x11-common
hostname         README

that is the "/etc/init.d" and I am working with a Desktop PC. 
this is the ishw:
    description: Desktop Computer
    product: PX743AA-ABA a1110n
    vendor: HP Pavilion 061
    version: 0nx1211RE101GUPPY00
    serial: CNH5251Q8V NA530
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1 uuid=002B848F-B2E2-D911-8A99-8AE127278698
  *-core
       description: Motherboard
       product: Guppy
       vendor: ASUSTek Computer INC.
       physical id: 0
       version: 1.03
       serial: MB-1234567890
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 3.08 (05/09/2005)
          size: 128KiB
          capacity: 448KiB
          capabilities: pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) CPU 3.06GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.4.1
          serial: 0000-0F41-0000-0000-0000-0000
          slot: PGA 478
          size: 3066MHz
          capacity: 3066MHz
          width: 32 bits
          clock: 133MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc up pebs bts pni dtes64 monitor ds_cpl cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: L1 Cache
             size: 16KiB
             capacity: 16KiB
             capabilities: synchronous internal write-back data
        *-cache:1
             description: L1 cache
             physical id: 9
             slot: L2 Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: synchronous internal write-back unified
     *-memory
          description: System Memory
          physical id: 21
          slot: System board or motherboard
          size: 512MiB
          capacity: 2GiB
        *-bank:0
             description: DIMM DDR Synchronous 66 MHz (15.2 ns)
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 512MiB
             width: 64 bits
             clock: 66MHz (15.2ns)
        *-bank:1
             description: DIMM 41472 MHz (0.0 ns) [empty]
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
             clock: 2817MHz (0.4ns)
     *-pci
          description: Host bridge
          product: 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:d0000000-dfffffff(prefetchable)
        *-display UNCLAIMED
             description: VGA compatible controller
             product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:e0000000-e7ffffff(prefetchable) memory:e8100000-e817ffff
        *-usb:0
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:d800(size=32)
        *-usb:1
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:d000(size=32)
        *-usb:2
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:d400(size=32)
        *-usb:3
             description: USB Controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:e8180000-e81803ff
        *-pci
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 82
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
             resources: ioport:c000(size=4096) memory:e8000000-e80fffff
           *-communication UNCLAIMED
                description: Communication controller
                product: V.92 56K WinModem
                vendor: Agere Systems
                physical id: b
                bus info: pci@0000:01:0b.0
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=32 maxlatency=14 mingnt=252
                resources: memory:e8000000-e80000ff ioport:c000(size=8) ioport:c400(size=256)
           *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: d
                bus info: pci@0000:01:0d.0
                logical name: eth0
                version: 10
                serial: 00:13:d4:24:81:43
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.2.2 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
                resources: irq:17 ioport:c800(size=256) memory:e8001000-e80010ff
           *-firewire
                description: FireWire (IEEE 1394)
                product: VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller
                vendor: VIA Technologies, Inc.
                physical id: e
                bus info: pci@0000:01:0e.0
                version: 80
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=32 maxlatency=32
                resources: irq:18 memory:e8002000-e80027ff ioport:cc00(size=128)
        *-isa
             description: ISA bridge
             product: 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
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
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f000(size=16) memory:20000000-200003ff
           *-disk
                description: ATA Disk
                product: ST3160021A
                vendor: Seagate
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 8.11
                serial: 5LJ1GD7F
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0000505a
              *-volume:0
                   description: Linux swap volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 1
                   serial: 24af63d3-eb19-4063-8156-6e947f4baae7
                   size: 1430MiB
                   capacity: 1430MiB
                   capabilities: primary bootable nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 91GiB
                   capacity: 91GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /
                      capacity: 51GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 38GiB
                 *-logicalvolume:2
                      description: Linux swap / Solaris partition
                      physical id: 7
                      logical name: /dev/sda7
                      capacity: 1432MiB
                      capabilities: nofs
              *-volume:2
                   description: Windows NTFS volume
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   version: 3.1
                   serial: ea70f1b8-1e97-0247-8af4-7cc6631110e4
                   size: 56GiB
                   capacity: 56GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2010-08-12 01:57:10 filesystem=ntfs state=clean
           *-cdrom
                description: DVD writer
                product: DVD DD 2X16X4X16
                vendor: ATAPI
                physical id: 0.1.0
                bus info: scsi@1:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: B7C9
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:500(size=32)
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0
             resources: irq:17 ioport:e000(size=256) ioport:e400(size=64) memory:e8181000-e81811ff memory:e8182000-e81820ff
     *-scsi
          physical id: 1
          bus info: usb@4:1
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@2:0.0.1
             logical name: /dev/sdc
        *-disk:2
             description: SCSI Disk
             physical id: 0.0.2
             bus info: scsi@2:0.0.2
             logical name: /dev/sdd
        *-disk:3
             description: SCSI Disk
             physical id: 0.0.3
             bus info: scsi@2:0.0.3
             logical name: /dev/sde

i dont know if that helps but there it is.

---

