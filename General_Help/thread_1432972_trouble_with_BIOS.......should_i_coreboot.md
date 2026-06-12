---
title: "trouble with BIOS.......should i coreboot?"
date: 2010-03-18
forum: General Help
---

### Post by justborn on 2010-03-18
i'm currently using the BIOS that came with my box....but i doesn't seem to go too well with linux...i have to manually reset date,time before every boot,otherwise it doesn't.....

i have read abt coreboot,and i think i'll do it.....but before that i would like to know if it is recommended to do so, by ppl who knw/have used it....

my second option: should i jus update the firmware to the next version?if so how?i literally have no idea....

third: or should i opt for some other alternative????

pls help....

---

### Post by Grenage on 2010-03-18
Are you sure it doesn't just need a new battery?

---

### Post by justborn on 2010-03-18
> **Grenage said:**
> Are you sure it doesn't just need a new battery?

ya,it's an old pc at work....

---

### Post by Grenage on 2010-03-18
I'd try upgrading to the manufacturer's latest BIOS revision for the board, they will have instructions on the site.

Coreboot does look interesting, I think I might salvage a spare BIOS chip and try it out.

---

### Post by justborn on 2010-03-18
> **Grenage said:**
> I'd try upgrading to the manufacturer's latest BIOS revision for the board, they will have instructions on the site.

Coreboot does look interesting, I think I might salvage a spare BIOS chip and try it out.

manufacturer,i don know??
```
sudo dmidecode --type 38
# dmidecode 2.9
SMBIOS 2.3 present.

```

is it SMBIOS?

---

### Post by Grenage on 2010-03-18
Are you able to open the case and look at the model number?

---

### Post by justborn on 2010-03-18
> **Grenage said:**
> Are you able to open the case and look at the model number?

open da case???i can do that....but i thought there was a command to find that.....

---

### Post by Grenage on 2010-03-18
There may or may not be, but if you're going to want to remove any room for error.  I trust a stamp on a PCB more than a terminal output (usually).

---

### Post by justborn on 2010-03-18
> **Grenage said:**
> There may or may not be, but if you're going to want to remove any room for error.  I trust a stamp on a PCB more than a terminal output (usually).

so it's to be done da hard way....no probo,i'll do it and revert

---

### Post by justborn on 2010-03-21
i coundn't find it....dude i just want to flash ma existing bios n get on with coreboot.....can someone help me with da prequestions,building packages,and installation......


plz.....

---

### Post by cascade9 on 2010-03-21
> **Grenage said:**
> Are you sure it doesn't just need a new battery?

I'm 99.99% sure this is the problem. 

> **Grenage said:**
> There may or may not be, but if you're going to want to remove any room for error.  I trust a stamp on a PCB more than a terminal output (usually).

+1. I'm yet to see any terminal output that will actually give you the brand of the manufacturer anyway....

---

### Post by jsriz on 2010-03-21
try both these commands these give info about your hardware and post the results
```

sudo lspci
sudo lshw


```

---

### Post by jsriz on 2010-03-21
As for coreboot 
i really wanted to try it on my lappi after hours and hours of searching i found out that my motherboard aint supported...............
i think the open bios program is still in core stages of development.....

---

### Post by jsriz on 2010-03-21
First step to coreboot find out if your motherboard is supported
so post your specs

---

### Post by justborn on 2010-03-24
here r the outputs for [COLOR="Red"]sudo lspci[/COLOR] ```
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (LOM) Ethernet Controller (rev 81)
```

and [COLOR="red"]sudo lshw[/COLOR]```
arpit-desktop             
    description: Computer
    product: BrkdleG-ICH4
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal cpus=1 uuid=F727E3BC-C2F7-11D9-AEB2-000EA62929EE
  *-core
       description: Motherboard
       product: D845GVSR
       vendor: Intel Corporation
       physical id: 0
       version: AAC45439-303
       serial: FCSR52100785
     *-firmware
          description: BIOS
          vendor: Intel Corp.
          physical id: 0
          version: VA84510A.86A.0056.P20.0605040337 (05/04/2006)
          size: 64KiB
          capacity: 448KiB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.40GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.4.1
          serial: 0000-0F41-0000-0000-0000-0000
          slot: X1
          size: 2400MHz
          capacity: 2800MHz
          width: 32 bits
          clock: 133MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc up pebs bts pni dtes64 monitor ds_cpl cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: None
             size: 16KiB
             capacity: 16KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: None
             size: 1MiB
             capacity: 1MiB
             capabilities: pipeline-burst internal varies unified
     *-memory
          description: System Memory
          physical id: 2f
          slot: System board or motherboard
          size: 512MiB
          capacity: 3GiB
        *-bank:0
             description: DIMM DDR Synchronous 266 MHz (3.8 ns)
             product: PartNum1
             vendor: Manufacturer1
             physical id: 0
             serial: SerNum1
             slot: J6G1
             size: 256MiB
             width: 64 bits
             clock: 266MHz (3.8ns)
        *-bank:1
             description: DIMM DDR Synchronous 266 MHz (3.8 ns)
             product: PartNum2
             vendor: Manufacturer2
             physical id: 1
             serial: SerNum2
             slot: J6G2
             size: 256MiB
             width: 64 bits
             clock: 266MHz (3.8ns)
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
          resources: irq:0 memory:f8000000-fbffffff(prefetchable)
        *-display
             description: VGA compatible controller
             product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:f0000000-f7ffffff(prefetchable) memory:ffa80000-ffafffff
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
             resources: irq:16 ioport:e800(size=32)
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
             resources: irq:19 ioport:e880(size=32)
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
             resources: irq:18 ioport:ec00(size=32)
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
             resources: irq:23 memory:ffa7fc00-ffa7ffff
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
             resources: ioport:d000(size=4096) memory:ff800000-ff8fffff memory:e6a00000-e6afffff(prefetchable)
           *-network
                description: Ethernet interface
                product: 82801DB PRO/100 VE (LOM) Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:01:08.0
                logical name: eth0
                version: 81
                serial: 00:13:20:22:f8:6d
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.1.2 latency=32 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
                resources: irq:20 memory:ff8ff000-ff8fffff ioport:dc00(size=64)
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
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16) memory:20000000-200003ff
           *-cdrom
                description: CD-R/CD-RW writer
                product: CD-R/RW SH-R522C
                vendor: TSSTcorp
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: TS01
                serial: [TSSTcorpCD-R/RW SH-R522CTS01
                capabilities: removable audio cd-r cd-rw
                configuration: ansiversion=5 status=nodisc
           *-disk
                description: ATA Disk
                product: SAMSUNG SP0802N
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/sda
                version: TK20
                serial: S00JJ60Y405444
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000e700d
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: bea1dea5-9b97-42a8-b287-44010ebeb35f
                   size: 73GiB
                   capacity: 73GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2009-10-09 19:02:51 filesystem=ext4 lastmountpoint=/T j&#65533;.0&#65533;d&#1984;q&#1940;^)&#1877;6 &#65533;&#65533;40*/&#65533;&#65533;^)&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;.0&#65533;&#65533;^)&#1904;^)&#65533;=9 modified=2010-03-24 04:36:38 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-03-25 00:10:02 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@1:0.0.0,2
                   logical name: /dev/sda2
                   size: 1451MiB
                   capacity: 1451MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1451MiB
                      capabilities: nofs
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
             resources: ioport:e000(size=32)#-o
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
             resources: irq:17 ioport:e400(size=256) ioport:e080(size=64) memory:ffa7f800-ffa7f9ff memory:ffa7f400-ffa7f4ff
```


n sorry for the late reply..........

---

### Post by jsriz on 2010-03-24
you have a INTEL-D845GVSR which is not officially supported
source:[http://www.coreboot.org/Supported_Motherboards](http://www.coreboot.org/Supported_Motherboards)
you can find sites giving open bios packages for your system but running these will only return that :"A newer version of bios is already installed".......

---

### Post by jsriz on 2010-03-24
well according to me the best that you can do for your system is to upgrade its proprietary bios
to the latest version given on the intel site (release date 2008--yours is in 2006)

---

### Post by justborn on 2010-03-25
jsriz,thanks for looking it up for me......

i'll try da intel site and revert....

---

### Post by jsriz on 2010-03-25
> **justborn said:**
> jsriz,thanks for looking it up for me......

i'll try da intel site and revert....
any time dude 
well I personally want to try coreboot on my laptop if you strike upon something please contact me.......

---

### Post by justborn on 2010-03-25
the link [http://aiedownload.intel.com/df-support/9730/eng/FDOEMCD.source.zip]("http://aiedownload.intel.com/df-support/9730/eng/FDOEMCD.source.zip.") for BIOS update is no longer available,can anyone else suggest an alternative link....


or should i try the exe in wine??

---

### Post by jsriz on 2010-03-27
No Don't try it on WINE 
I Guess you should post it on new thread

---

### Post by jsriz on 2010-03-27
I get my bios upgrades from Dell which also gives linux versions....

---

### Post by jocko on 2010-03-27
> **justborn said:**
> i'm currently using the BIOS that came with my box....but i doesn't seem to go too well with linux...i have to manually reset date,time before every boot,otherwise it doesn't.....
That's because the cmos battery on the motherboard has run out, so that the bios can no longer keep the date, time and other settings.
Replace the battery before you do anything else. A new bios will not solve that problem. Without a battery the bios will never remember the correct time, and will have to be set on each boot.

And as far as I know coreboot is still highly experimental and may very well transform your pc into a paperweight.

---

### Post by justborn on 2010-03-28
> **jocko said:**
> That's because the cmos battery on the motherboard has run out, so that the bios can no longer keep the date, time and other settings.
Replace the battery before you do anything else. A new bios will not solve that problem. Without a battery the bios will never remember the correct time, and will have to be set on each boot.

And as far as I know coreboot is still highly experimental and may very well transform your pc into a paperweight.

ohk!.....so what do ask for ,at the pc store,"cmos battery"?n how much will it cost??

thanks for da explanation....all this time when ppl said, "battery" in da thread ,i thought they meant a lappy battery or something,and i ignored em coz mine is a pc.....

thanks again!

---

### Post by cascade9 on 2010-03-28
Take out your old battery, then take that to the store. They should know what you mean if you say 'cmos battery', 'motherboard battery', or 'coin cell battery' but its best to be sure ;) 

It will almost certainly look like this- 

[IMG]http://img.diytrade.com/cdimg/712195/5661686/0/1241830983/CR2032_lithium_coin_cell_button_cell_battery_dry_battery_primary_battery.jpg[/IMG]

---

### Post by justborn on 2010-04-29
oh,da coin cell battery!so stupid of me not to get that in da first place itself......



anyways thank u guys, especially cascade9 for uploading da image.....

---

