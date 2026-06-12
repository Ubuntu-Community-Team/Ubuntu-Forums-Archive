---
title: "Is 8GB enough for ubuntu usb install?"
date: 2012-06-29
forum: General Help
---

### Post by qwertyjjj on 2012-06-29
Is an 8GB stick enough space to install ubuntu on and have it running off the stick?

---

### Post by pe7er on 2012-06-29
I think so, but it depends on the other software you want to use.

What are you going to do with it? 
Which software would you like to use?

NB: I have read about limited read/write of USB sticks,
and that it's advisable to not use a SWAP partition on it.

---

### Post by prshah on 2012-06-29
> **qwertyjjj said:**
> Is an 8GB stick enough space to install ubuntu on and have it running off the stick?

Comfortably. You need only about 700mb (approx) to create the CD image on the stick. The rest can be allocated to "casper" for persistance (eg, changes made in a session are not lost).

Or you can even split it into multiple partitions, (Eg for the cd image, persistance and 1 for shared usage).

---

### Post by DJTIESTO19 on 2012-06-29
Generally, yes it is enough. It depends on how much space your computer/laptop has, as well as the usb stick carrying the ubuntu partition installation (that is, I hope you have enough space to partition your current OS with ubuntu).

---

### Post by idoitprone on 2012-06-29
> **qwertyjjj said:**
> Is an 8GB stick enough space to install ubuntu on and have it running off the stick?


i recommend puppy linux [http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm](http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm)

---

### Post by philinux on 2012-06-29
> **qwertyjjj said:**
> Is an 8GB stick enough space to install ubuntu on and have it running off the stick?

Yes. 4gig here no problems.

Obviously performance depends on machine it's used on.

---

### Post by oldfred on 2012-06-29
I assume you mean a full install.


Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

I have a full install of Ubuntu in an 8GB partition on my 16GB flash drive. I made some settings changes like on a SSD to reduce writes. Install was slower than on hard drive, but once an application is loaded and in RAM it works well. Some things are just slower loading as USB is not as fast as SATA and flash not as fast as hard drive.
I am  using it more to test new version on laptop as I do not have a lot of room for another partition and as a backup way to boot, so I am not using it a lot.

If you have a lower performance system Lubuntu may be an alternative as a full install.

Install has not changed much between versions, so this still helps:
It does not have to be encrypted BIOS based system, text based version for encryption:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory Installation using alternative text based installer
[http://members.iinet.net/~herman546/p19.html]("http://members.iinet.net/%7Eherman546/p19.html")
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)

---

### Post by elliotn on 2012-06-29
8gig is big enough.

---

### Post by Cheesemill on 2012-06-29
> **prshah said:**
> Comfortably. You need only about 700mb (approx) to create the CD image on the stick. The rest can be allocated to "casper" for persistance (eg, changes made in a session are not lost)..

I'm assuming the OP is talking about a full install, rather than a Live USB.

In which case the requirements are the same as the Ubuntu installation requirements, a minimum of 5GB.
[https://help.ubuntu.com/community/Installation/SystemRequirements/](https://help.ubuntu.com/community/Installation/SystemRequirements/)

---

### Post by philinux on 2012-06-29
> **Cheesemill said:**
> I'm assuming the OP is talking about a full install, rather than a Live USB.

In which case the requirements are the same as the Ubuntu installation requirements, a minimum of 5GB.
[https://help.ubuntu.com/community/Installation/SystemRequirements/](https://help.ubuntu.com/community/Installation/SystemRequirements/)

Seems like qwertyjjj is not explaing his needs in detail.

Original post could mean many things.

---

### Post by prshah on 2012-06-29
> **Cheesemill said:**
> I'm assuming the OP is talking about a full install, rather than a Live USB.

Maybe. However, when I hear hooves, I think of horses, not zebras. :D

I absolutely don't see "installing" ubuntu to a USB as any level of advantage. A live USB with persistance makes more sense than an install "to" a USB pendrive.

In either case, 8GB is enough. QED.

---

### Post by qwertyjjj on 2012-06-29
> **prshah said:**
> Maybe. However, when I hear hooves, I think of horses, not zebras. :D

I absolutely don't see "installing" ubuntu to a USB as any level of advantage. A live USB with persistance makes more sense than an install "to" a USB pendrive.

In either case, 8GB is enough. QED.

I am installing wityh persistance to a usb so that I can run ubuntu on any computer I like. I wuld then have an extra 500Gb USB hard drive that I also move around for videos music...
Really, it's just for travelling so it doesn't need to hold too much data.

---

### Post by idoitprone on 2012-06-29
> **qwertyjjj said:**
> I am installing wityh persistance to a usb so that I can run ubuntu on any computer I like. I wuld then have an extra 500Gb USB hard drive that I also move around for videos music...
Really, it's just for travelling so it doesn't need to hold too much data.

puppy linux is better suited because ubuntu is a little too bloated for a usb. Puppy linux is however designed for slow computer, so you will always get acceptable performance everywhere

---

### Post by qwertyjjj on 2012-06-30
> **idoitprone said:**
> puppy linux is better suited because ubuntu is a little too bloated for a usb. Puppy linux is however designed for slow computer, so you will always get acceptable performance everywhere

Performance doesn;t seem too bad on ubuntu, I'll try it for a while and see how it goes.

---

### Post by kurt18947 on 2012-06-30
I'm creating a 'regular' install on a USB drive as we speak.  For me, the advantage of a 'real' install vs. live USB is the ability to install updates.  I tried security updates once on a live USB install.  The results were less than hoped for :tongue:.  I'm planning to use this just for secure type transactions.  No flash, no java if I can avoid it.  Don't start a 'real' USB install if you're time limited.  To install and run updates on Xubuntu 12.04 will probably take about 3 hours.  Once created, the USB install runs acceptably fast - for me at least.

---

### Post by qwertyjjj on 2012-06-30
Are there some tricks to make PERFORMANCE on ub bETTER?
Separate swap space or loading something in RAM?

---

### Post by bogan on 2012-06-30
Hi! **All,**

Using the then advised 'best' partition size of 4GB, for a full & updated installation, I installed 11.10 in a 4.5GB partiton, with 2GB Swap and  the rest an sdx1 NTFS Switch partition; this on an 8GB USB stick.

All went well until the other day when a kernal update crashed with a 'not enough space'.

The Kernal-image file did not get installed which stopped the usual remedies working, and there was not enough space to install a means of deleting the  huge collection of kernal-headers and kernal-images, from the multiple updates.

In the end I had to reduce the Swap partition and extend the root. After a clean up with Ubuntu-Tweak I now have a root partition of 5.5GB and enough space to avoid a repetition. 

So I can confirm with some certainty,  given that 12.04 LTS is somewhat larger, that the advised 5GB minimum is correct, and an 8GB USB certainly enough.

Chao!, **bogan.**

---

### Post by uRock on 2012-06-30
I use lubuntu on my USB with persistance. It loads and runs much faster than ubuntu, because it uses much lighter, but not as pretty, software.

---

### Post by efflandt on 2012-06-30
I just did a fresh full install of 64-bit 12.04 on another drive, and then did all updates.

efflandt@XPS-8100-1110:~$ df -h /media/029ce074-e30a-4351-8652-a566f2fdaf4d/
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda4              97G  3.6G   88G   4% /media/029ce074-e30a-4351-8652-a566f2fdaf4d

But what is confusing is that if I right click on that directory in the file manager and select Properties, that says:

Contents 3.3 GB (some contents unreadable)

9.1 GB used
94.2 GB free
Total Capacity 103.2 GB

So maybe many small files take up much more space than file size due to partition size.

On the other hand, bootable live/install iso takes up about 700 MB plus persistent data (limited to 4 GB due to FAT32 file system).  There is supposed to be a way to use a separate partition with "casper-rw" label for persistent data instead of a file, but I never figured out how to do that.

---

### Post by qwertyjjj on 2012-07-01
> **qwertyjjj said:**
> Are there some tricks to make PERFORMANCE on ub bETTER?
Separate swap space or loading something in RAM?

any options?

---

### Post by idoitprone on 2012-07-01
> **qwertyjjj said:**
> any options?


your tweaking something that is not worth the benfit. 

An internal harddrive will almost always out perform an external usb. The best way to get acceptable performance everywhere is to install in on an internal hdd or to run it all in ram. 

Puppy Linux, which is a distro that I suggested, runs everything in ram. It is simple and easy to use. It only takes 150 MB for a base installation.

Seriously, tweaking Ubuntu is not really worth the benefit, when you can use puppy linux and access ubuntu programs

---

### Post by qwertyjjj on 2012-07-28
> **idoitprone said:**
> your tweaking something that is not worth the benfit. 

An internal harddrive will almost always out perform an external usb. The best way to get acceptable performance everywhere is to install in on an internal hdd or to run it all in ram. 

Puppy Linux, which is a distro that I suggested, runs everything in ram. It is simple and easy to use. It only takes 150 MB for a base installation.

Seriously, tweaking Ubuntu is not really worth the benefit, when you can use puppy linux and access ubuntu programs

I've been running Ubuntu on a stick for a few weeks now and in general it runs well but the only annoyingthing is that sometimes when too much is going on, the window goes dim/grey for 20 seconds and thenback again.

So, I'd like to try out Puppy Linux but won;t it suffer from the same problem? I think the greing out happens in Ubuntu when the CPU doesn't respond quickly enough or maybe writes to the drive aren't quick enough?

Also, is there a way to get a list of my installed applications in Ubuntu and install them in Puppy Linux?

---

### Post by qwertyjjj on 2012-07-30
've been running Ubuntu on a stick for a few weeks now and in general it runs well but the only annoyingthing is that sometimes when too much is going on, the window goes dim/grey for 20 seconds and thenback again.

So, I'd like to try out Puppy Linux but won;t it suffer from the same problem? I think the greing out happens in Ubuntu when the CPU doesn't respond quickly enough or maybe writes to the drive aren't quick enough?

Also, is there a way to get a list of my installed applications in Ubuntu and install them in Puppy Linux?

---

### Post by idoitprone on 2012-07-30
> **qwertyjjj said:**
> 've been running Ubuntu on a stick for a few weeks now and in general it runs well but the only annoyingthing is that sometimes when too much is going on, the window goes dim/grey for 20 seconds and thenback again.

So, I'd like to try out Puppy Linux but won;t it suffer from the same problem? I think the greing out happens in Ubuntu when the CPU doesn't respond quickly enough or maybe writes to the drive aren't quick enough?

Also, is there a way to get a list of my installed applications in Ubuntu and install them in Puppy Linux?


it is hard to say without you posting specs of your hardware

dim/grey should like a graphic driver problem

---

### Post by qwertyjjj on 2012-07-31
> **idoitprone said:**
> it is hard to say without you posting specs of your hardware

dim/grey should like a graphic driver problem

I don;t think it's that as it doesn;t happen when running off the hard drive:

```

usb@usb-Inspiron-9300:~$ sudo lshw
[sudo] password for usb: 
usb-inspiron-9300         
    description: Notebook
    product: 4236PA8 ()
    vendor: LENOVO
    version: ThinkPad T420
    serial: R8DB5F9
    width: 32 bits
    capabilities: smbios-2.6 dmi-2.6
    configuration: administrator_password=disabled chassis=notebook family=ThinkPad T420 power-on_password=disabled uuid=811C78BE-4F51-CB11-AE7C-DEDF766CB271
  *-core
       description: Motherboard
       product: 4236PA8
       vendor: LENOVO
       physical id: 0
       version: Not Available
       serial: 1ZKCB18LBCX
       slot: Not Available
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i5-2520M CPU @ 2.50GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.10.7
          serial: 0002-06A7-0000-0000-0000-0000
          slot: CPU
          size: 800MHz
          capacity: 800MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx lahf_lm ida arat epb xsaveopt pln pts tpr_shadow vnmi flexpriority ept vpid cpufreq
          configuration: cores=2 enabledcores=2 id=0 threads=4
        *-cache:0
             description: L1 cache
             physical id: 2
             slot: L1-Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: synchronous internal write-through data
        *-cache:1
             description: L2 cache
             physical id: 3
             slot: L2-Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: synchronous internal write-through data
        *-cache:2
             description: L3 cache
             physical id: 4
             slot: L3-Cache
             size: 3MiB
             capacity: 3MiB
             capabilities: synchronous internal write-back unified
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
        *-logicalcpu:2
             description: Logical CPU
             physical id: 0.3
             width: 64 bits
             capabilities: logical
        *-logicalcpu:3
             description: Logical CPU
             physical id: 0.4
             width: 64 bits
             capabilities: logical
        *-logicalcpu:4
             description: Logical CPU
             physical id: 0.5
             width: 64 bits
             capabilities: logical
        *-logicalcpu:5
             description: Logical CPU
             physical id: 0.6
             width: 64 bits
             capabilities: logical
        *-logicalcpu:6
             description: Logical CPU
             physical id: 0.7
             width: 64 bits
             capabilities: logical
        *-logicalcpu:7
             description: Logical CPU
             physical id: 0.8
             width: 64 bits
             capabilities: logical
        *-logicalcpu:8
             description: Logical CPU
             physical id: 0.9
             width: 64 bits
             capabilities: logical
        *-logicalcpu:9
             description: Logical CPU
             physical id: 0.a
             width: 64 bits
             capabilities: logical
        *-logicalcpu:10
             description: Logical CPU
             physical id: 0.b
             width: 64 bits
             capabilities: logical
        *-logicalcpu:11
             description: Logical CPU
             physical id: 0.c
             width: 64 bits
             capabilities: logical
        *-logicalcpu:12
             description: Logical CPU
             physical id: 0.d
             width: 64 bits
             capabilities: logical
        *-logicalcpu:13
             description: Logical CPU
             physical id: 0.e
             width: 64 bits
             capabilities: logical
        *-logicalcpu:14
             description: Logical CPU
             physical id: 0.f
             width: 64 bits
             capabilities: logical
        *-logicalcpu:15
             description: Logical CPU
             physical id: 0.10
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 5
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: HMT351S6BFR8C-H9
             vendor: Hynix/Hyundai
             physical id: 0
             serial: 1E18DA32
             slot: ChannelA-DIMM0
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: DIMMProject-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2012-02-05 00:26+0000Last-Translator: Andi Chandler <Unknown>Language-Team: English (United Kingdom) <en_GB@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2012-05-08 10:38+0000X-Generator: Launchpad (build 15204) [empty]
             physical id: 1
             slot: ChannelB-DIMM0
     *-firmware
          description: BIOS
          vendor: LENOVO
          physical id: e
          version: 83ET67WW (1.37 )
          date: 11/28/2011
          size: 128KiB
          capacity: 8128KiB
          capabilities: pci pnp upgrade shadowing cdboot bootselect edd int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb biosbootspecification
     *-pci
          description: Host bridge
          product: 2nd Generation Core Processor Family DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: 2nd Generation Core Processor Family Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:41 memory:f0000000-f03fffff memory:e0000000-efffffff ioport:5000(size=64)
        *-communication:0
             description: Communication controller
             product: 6 Series/C200 Series Chipset Family MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei latency=0
             resources: irq:43 memory:f2525000-f252500f
        *-communication:1
             description: Serial controller
             product: 6 Series/C200 Series Chipset Family KT Controller
             vendor: Intel Corporation
             physical id: 16.3
             bus info: pci@0000:00:16.3
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: pm msi 16550 bus_master cap_list
             configuration: driver=serial latency=0
             resources: irq:19 ioport:50b0(size=8) memory:f252c000-f252cfff
        *-network
             description: Ethernet interface
             product: 82579LM Gigabit Network Connection
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: eth2
             version: 04
             serial: 00:21:cc:6a:17:11
             capacity: 1Gbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.5.1-k firmware=0.13-3 latency=0 link=no multicast=yes port=twisted pair
             resources: irq:42 memory:f2500000-f251ffff memory:f252b000-f252bfff ioport:5080(size=32)
        *-usb:0
             description: USB controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:f252a000-f252a3ff
        *-multimedia
             description: Audio device
             product: 6 Series/C200 Series Chipset Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:45 memory:f2520000-f2523fff
        *-pci:0
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: b4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16
        *-pci:1
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: b4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 memory:f2400000-f24fffff
           *-network
                description: Wireless interface
                product: Centrino Ultimate-N 6300
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlan0
                version: 35
                serial: 00:24:d7:e7:d5:20
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-26-generic-pae firmware=9.221.4.1 build 25532 ip=192.168.1.100 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
                resources: irq:44 memory:f2400000-f2401fff
        *-pci:2
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: b4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:19 ioport:4000(size=4096) memory:f1c00000-f23fffff ioport:f0400000(size=8388608)
        *-pci:3
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: b4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:3000(size=4096) memory:f1400000-f1bfffff ioport:f0c00000(size=8388608)
           *-generic
                description: System peripheral
                product: MMC/SD Host Controller
                vendor: Ricoh Co Ltd
                physical id: 0
                bus info: pci@0000:0d:00.0
                version: 08
                width: 32 bits
                clock: 33MHz
                capabilities: msi pm pciexpress bus_master cap_list
                configuration: driver=sdhci-pci latency=0
                resources: irq:16 memory:f1400000-f14000ff
        *-usb:1
             description: USB controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:f2529000-f25293ff
        *-isa
             description: ISA bridge
             product: QM67 Express Chipset Family LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:40 ioport:50a8(size=8) ioport:50bc(size=4) ioport:50a0(size=8) ioport:50b8(size=4) ioport:5060(size=32) memory:f2528000-f25287ff
           *-disk
                description: ATA Disk
                product: WDC WD3200BEKT-0
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 02.0
                serial: WD-WXG1A71K3710
                size: 298GiB (320GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=1979654a
              *-volume
                   description: HPFS/NTFS partition
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 298GiB
                   capabilities: primary bootable
           *-cdrom
                description: DVD-RAM writer
                product: DVD RW AD-7710H
                vendor: Optiarc
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/sr0
                version: 1.S0
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 6 Series/C200 Series Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 04
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f2524000-f25240ff ioport:efa0(size=32)
     *-scsi
          physical id: 0
          bus info: usb@1:1.1
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdb
             size: 7633MiB (8004MB)
             capabilities: partitioned partitioned:dos
             configuration: signature=0007e152
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@6:0.0.0,1
                logical name: /dev/sdb1
                logical name: /
                version: 1.0
                serial: 14fdd9cd-6ea2-4fbd-9ab7-79b5b60c4f1d
                size: 7255MiB
                capacity: 7255MiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2012-06-29 12:46:48 filesystem=ext4 lastmountpoint=/ modified=2012-07-30 08:45:15 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,barrier=1,data=ordered mounted=2012-07-31 07:35:04 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@6:0.0.0,2
                logical name: /dev/sdb2
                size: 376MiB
                capacity: 376MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sdb5
                   capacity: 376MiB
                   capabilities: nofs
  *-battery
       product: 42T4793
       vendor: Panasonic
       physical id: 1
       slot: Rear
       capacity: 56160mWh
       configuration: voltage=10.8V
  *-network
       description: Ethernet interface
       physical id: 2
       bus info: usb@2:1.2
       logical name: eth0
       serial: da:a2:5e:a3:27:2c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=ipheth link=no multicast=yes

```

---

### Post by Dawnbandit on 2012-07-31
Yes. Well, if you dont plan on installing and downloading alot of stuff!

---

### Post by qwertyjjj on 2012-07-31
> **Dawnbandit said:**
> Yes. Well, if you dont plan on installing and downloading alot of stuff!

?
Not sure what that has to do with the greying out...

---

