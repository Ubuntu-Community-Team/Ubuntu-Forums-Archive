---
title: "System freeze: &quot;Marking TSC unstable due to cpufreq changes&quot;"
date: 2010-10-03
forum: General Help
---

### Post by barbex on 2010-10-03
I'm running ubuntu 10.04 as a mythtv box and it works mostly fine. But occasionally the system will hang during booting and the last messages I can see are:

```
cpufreq-nforce2: FSB changing is maybe unstable and can lead to crashes and data loss.
cpufreq-nforce2: FSB currently at 166 MHz, FID 12.5
Marking TSC unstable due to cpufreq changes
```

That detected FSB is correct and that's what I set in the BIOS. There is no changing going on. The Mainboard and CPU have worked like that for years, this install of ubuntu is the first time that I have a problem with booting it.

Sooo, I don't know. What is the problem? This system is supposed to run mostly unattended, I can't check all the time whether it booted allright. 

So what can I do?

---

### Post by coffee412 on 2010-10-03
> **barbex said:**
> I'm running ubuntu 10.04 as a mythtv box and it works mostly fine. But occasionally the system will hang during booting and the last messages I can see are:

```
cpufreq-nforce2: FSB changing is maybe unstable and can lead to crashes and data loss.
cpufreq-nforce2: FSB currently at 166 MHz, FID 12.5
Marking TSC unstable due to cpufreq changes
```That detected FSB is correct and that's what I set in the BIOS. There is no changing going on. The Mainboard and CPU have worked like that for years, this install of ubuntu is the first time that I have a problem with booting it.

Sooo, I don't know. What is the problem? This system is supposed to run mostly unattended, I can't check all the time whether it booted allright. 

So what can I do?

Got you covered here ....

What you need to do is change your clock source. This is not that hard but is accomplished thru a term window.

From your error message your current clock source is TSC. We need to find other available clock sources. So, Open a term window (applications/accessories/term window) and take a look at the contents of your available_clocksource file with the command below:

 > cat /sys/devices/system/clocksource/clocksource0/available_clocksourceNow choose one of the other clock sources and edit your /etc/default/grub file like so:

sudo nano /etc/default/grub

Change the following line:

> GRUB_CMDLINE_LINUX=""to:
> GRUB_CMDLINE_LINUX="acpi=hpet"
In this case Im just using hpet. Your available clocksources could be different.

Now save the file (control-x) and run grub update:

> sudo grub-updatereboot.

If the clocksource you choose doesnt work then try another. I had an emachine that had lockups and displayed the same error message. Changing it solved it.

:)

---

### Post by barbex on 2010-10-03
Huh, how interesting!

So let's see:
```

cat /sys/devices/system/clocksource/clocksource0/available_clocksource
acpi_pm 
```

Not much to choose from. I don't understand how it could ever work with TSC if that is not even listed.

By the way it is ```
sudo update-grub
``` for grub to make the new config.

I'm trying that now and we'll see.

---

### Post by barbex on 2010-10-03
Yeah, no hang on boot but dmesg still shows the same message. Weird.

---

### Post by coffee412 on 2010-10-03
> **barbex said:**
> Yeah, no hang on boot but dmesg still shows the same message. Weird.

What kind of computer or motherboard is this?

Oh, I stand corrected update-grub I guess :)

---

### Post by barbex on 2010-10-05
Well I can give you the whole list but the short version is that this is an Asus board with the nforce2 chipset, the CPU is a singlecore AMD Athlon with something like 2 GHz and I have 1,5 GB RAM.

So far I have not had a another freeze, so maybe it actually fixed it but it is still confusing that that error message is still there and I absolutely do not understand how that TSC can even show up, as it not listed as a clocksource.

I thought I understood what the clocksource is but maybe I didn't.

Now wonder if I should also do the noalpic boot option...

Thanks for your help anyway!


```
lshw
digitus
   description: Desktop Computer
   product: A7N8X-X
   vendor: ASUSTeK Computer INC.
   version: REV 2.xx
   serial: xxxxxxxxxxx
   width: 32 bits
   capabilities: smbios-2.2 dmi-2.2 smp
   configuration: boot=normal chassis=desktop
 *-core
      description: Motherboard
      product: A7N8X-X
      vendor: ASUSTeK Computer INC.
      physical id: 0
      version: REV 2.xx
      serial: xxxxxxxxxxx
    *-firmware
         description: BIOS
         vendor: Phoenix Technologies, LTD
         physical id: 0
         version: ASUS A7N8X-X ACPI BIOS Rev 1009 (02/03/2004)
         size: 64KiB
         capacity: 192KiB
         capabilities: pci pnp apm upgrade shadowing cdboot
bootselect socketedrom edd int13floppy360 int13floppy1200
int13floppy720 int13floppy2880 int5printscreen int9keyboard
int14serial int17printer int10video acpi usb agp ls120boot zipboot
    *-cpu
         description: CPU
         product: AMD Athlon(tm) XP 2800+
         vendor: Advanced Micro Devices [AMD]
         physical id: 4
         bus info: cpu@0
         version: 6.10.0
         slot: Socket A
         size: 2087MHz
         capacity: 3GHz
         width: 32 bits
         clock: 166MHz
         capabilities: fpu fpu_exception wp vme de pse tsc msr pae
mce cx8 apic mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext
3dnowext 3dnow up cpufreq
       *-cache:0
            description: L1 cache
            physical id: 9
            slot: L1 Cache
            size: 128KiB
            capacity: 128KiB
            capabilities: pipeline-burst synchronous internal write-back data
       *-cache:1
            description: L2 cache
            physical id: a
            slot: L2 Cache
            size: 512KiB
            capacity: 512KiB
            capabilities: pipeline-burst synchronous external write-back data
    *-memory
         description: System Memory
         physical id: 26
         slot: System board or motherboard
         size: 1536MiB
         capacity: 1536MiB
       *-bank:0
            description: DIMM DRAM Synchronous
            physical id: 0
            slot: DDR1
            size: 1GiB
            width: 64 bits
       *-bank:1
            description: DIMM DRAM Synchronous
            physical id: 1
            slot: DDR2
            size: 512MiB
            width: 64 bits
       *-bank:2
            description: DIMM DRAM Synchronous [empty]
            physical id: 2
            slot: DDR3
            width: 64 bits
    *-pci
         description: Host bridge
         product: nForce2 IGP2
         vendor: nVidia Corporation
         physical id: 100
         bus info: pci@0000:00:00.0
         version: c1
         width: 32 bits
         clock: 66MHz
         configuration: driver=agpgart-nvidia
         resources: irq:0 memory:d8000000-dbffffff(prefetchable)
       *-memory:0 UNCLAIMED
            description: RAM memory
            product: nForce2 Memory Controller 0
            vendor: nVidia Corporation
            physical id: 0.1
            bus info: pci@0000:00:00.1
            version: c1
            width: 32 bits
            clock: 66MHz (15.2ns)
            configuration: latency=0
       *-memory:1 UNCLAIMED
            description: RAM memory
            product: nForce2 Memory Controller 4
            vendor: nVidia Corporation
            physical id: 0.2
            bus info: pci@0000:00:00.2
            version: c1
            width: 32 bits
            clock: 66MHz (15.2ns)
            configuration: latency=0
       *-memory:2 UNCLAIMED
            description: RAM memory
            product: nForce2 Memory Controller 3
            vendor: nVidia Corporation
            physical id: 0.3
            bus info: pci@0000:00:00.3
            version: c1
            width: 32 bits
            clock: 66MHz (15.2ns)
            configuration: latency=0
       *-memory:3 UNCLAIMED
            description: RAM memory
            product: nForce2 Memory Controller 2
            vendor: nVidia Corporation
            physical id: 0.4
            bus info: pci@0000:00:00.4
            version: c1
            width: 32 bits
            clock: 66MHz (15.2ns)
            configuration: latency=0
       *-memory:4 UNCLAIMED
            description: RAM memory
            product: nForce2 Memory Controller 5
            vendor: nVidia Corporation
            physical id: 0.5
            bus info: pci@0000:00:00.5
            version: c1
            width: 32 bits
            clock: 66MHz (15.2ns)
            configuration: latency=0
       *-isa
            description: ISA bridge
            product: nForce2 ISA Bridge
            vendor: nVidia Corporation
            physical id: 1
            bus info: pci@0000:00:01.0
            version: a4
            width: 32 bits
            clock: 66MHz
            capabilities: isa ht bus_master cap_list
            configuration: latency=0
       *-serial
            description: SMBus
            product: nForce2 SMBus (MCP)
            vendor: nVidia Corporation
            physical id: 1.1
            bus info: pci@0000:00:01.1
            version: a2
            width: 32 bits
            clock: 66MHz
            capabilities: pm cap_list
            configuration: driver=nForce2_smbus latency=0 maxlatency=1 mingnt=3
            resources: irq:11 ioport:d000(size=32)
       *-usb:0
            description: USB Controller
            product: nForce2 USB Controller
            vendor: nVidia Corporation
            physical id: 2
            bus info: pci@0000:00:02.0
            version: a4
            width: 32 bits
            clock: 66MHz
            capabilities: pm bus_master cap_list
            configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
            resources: irq:21 memory:df003000-df003fff
       *-usb:1
            description: USB Controller
            product: nForce2 USB Controller
            vendor: nVidia Corporation
            physical id: 2.1
            bus info: pci@0000:00:02.1
            version: a4
            width: 32 bits
            clock: 66MHz
            capabilities: pm bus_master cap_list
            configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
            resources: irq:20 memory:df004000-df004fff
       *-usb:2
            description: USB Controller
            product: nForce2 USB Controller
            vendor: nVidia Corporation
            physical id: 2.2
            bus info: pci@0000:00:02.2
            version: a4
            width: 32 bits
            clock: 66MHz
            capabilities: debug pm bus_master cap_list
            configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
            resources: irq:22 memory:df005000-df0050ff
       *-network
            description: Ethernet interface
            product: nForce2 Ethernet Controller
            vendor: nVidia Corporation
            physical id: 4
            bus info: pci@0000:00:04.0
            logical name: eth0
            version: a1
            serial: 00:0e:a6:e0:19:e0
            size: 100MB/s
            capacity: 100MB/s
            width: 32 bits
            clock: 66MHz
            capabilities: pm bus_master cap_list ethernet physical
mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
            configuration: autonegotiation=on broadcast=yes
driver=forcedeth driverversion=0.64 duplex=full ip=192.168.21.254
latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII
speed=100MB/s
            resources: irq:22 memory:df000000-df000fff ioport:d400(size=8)
       *-multimedia
            description: Multimedia audio controller
            product: nForce2 AC97 Audio Controler (MCP)
            vendor: nVidia Corporation
            physical id: 6
            bus info: pci@0000:00:06.0
            version: a1
            width: 32 bits
            clock: 66MHz
            capabilities: pm bus_master cap_list
            configuration: driver=Intel ICH latency=0 maxlatency=5 mingnt=2
            resources: irq:21 ioport:d800(size=256)
ioport:dc00(size=128) memory:df001000-df001fff
       *-pci:0
            description: PCI bridge
            product: nForce2 External PCI Bridge
            vendor: nVidia Corporation
            physical id: 8
            bus info: pci@0000:00:08.0
            version: a3
            width: 32 bits
            clock: 66MHz
            capabilities: pci bus_master
            resources: memory:d0000000-d7ffffff(prefetchable)
          *-multimedia:0
               description: Multimedia video controller
               product: iTVC15 MPEG-2 Encoder
               vendor: Internext Compression Inc
               physical id: 8
               bus info: pci@0000:01:08.0
               version: 01
               width: 32 bits
               clock: 33MHz
               capabilities: pm bus_master cap_list
               configuration: driver=ivtv latency=64 maxlatency=8 mingnt=128
               resources: irq:18 memory:d0000000-d3ffffff(prefetchable)
          *-multimedia:1
               description: Multimedia video controller
               product: Bt878 Video Capture
               vendor: Brooktree Corporation
               physical id: a
               bus info: pci@0000:01:0a.0
               version: 11
               width: 32 bits
               clock: 33MHz
               capabilities: vpd pm bus_master cap_list
               configuration: driver=bttv latency=32 maxlatency=40 mingnt=16
               resources: irq:16 memory:d4000000-d4000fff(prefetchable)
          *-multimedia:2
               description: Multimedia controller
               product: Bt878 Audio Capture
               vendor: Brooktree Corporation
               physical id: a.1
               bus info: pci@0000:01:0a.1
               version: 11
               width: 32 bits
               clock: 33MHz
               capabilities: vpd pm bus_master cap_list
               configuration: driver=bt878 latency=32 maxlatency=255 mingnt=4
               resources: irq:16 memory:d4001000-d4001fff(prefetchable)
       *-ide
            description: IDE interface
            product: nForce2 IDE
            vendor: nVidia Corporation
            physical id: 9
            bus info: pci@0000:00:09.0
            logical name: scsi0
            logical name: scsi1
            version: a2
            width: 32 bits
            clock: 66MHz
            capabilities: ide pm bus_master cap_list emulated
            configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
            resources: irq:0 ioport:1f0(size=8) ioport:3f6
ioport:170(size=8) ioport:376 ioport:f000(size=16)
          *-disk:0
               description: ATA Disk
               product: SAMSUNG SP1614N
               physical id: 0
               bus info: scsi@0:0.0.0
               logical name: /dev/sda
               version: TM10
               serial: S016J10X449125
               size: 149GiB (160GB)
               capabilities: partitioned partitioned:dos
               configuration: ansiversion=5 signature=000c994d
             *-volume:0
                  description: EXT4 volume
                  vendor: Linux
                  physical id: 1
                  bus info: scsi@0:0.0.0,1
                  logical name: /dev/sda1
                  logical name: /
                  version: 1.0
                  serial: fce9c4d1-6025-4201-96d7-29cc007bf392
                  size: 7668MiB
                  capacity: 7668MiB
                  capabilities: primary bootable journaled
extended_attributes large_files huge_files dir_nlink extents ext4 ext2
initialized
                  configuration: created=2010-09-17 10:48:00
filesystem=ext4 lastmountpoint=/P:&#65533;x&#65533;x&#65533;h%&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;h
&#65533;&#65533;h/&#65533;&#65533;&#65533;&#65533;!&#65533;&#65533;n&#65533;&#65533;&#65533;n&#65533;&#65533;&#65533;x&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;]k modified=2010-09-17 11:02:24
mount.fstype=ext4
mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered
mounted=2010-09-22 18:39:30 state=mounted
             *-volume:1
                  description: Extended partition
                  physical id: 2
                  bus info: scsi@0:0.0.0,2
                  logical name: /dev/sda2
                  size: 141GiB
                  capacity: 141GiB
                  capabilities: primary extended partitioned
partitioned:extended
                *-logicalvolume:0
                     description: Linux swap / Solaris partition
                     physical id: 5
                     logical name: /dev/sda5
                     capacity: 1906MiB
                     capabilities: nofs
                *-logicalvolume:1
                     description: Linux filesystem partition
                     physical id: 6
                     logical name: /dev/sda6
                     logical name: /home
                     capacity: 139GiB
                     configuration: mount.fstype=ext4
mount.options=rw,relatime,barrier=1,data=ordered state=mounted
          *-disk:1
               description: ATA Disk
               product: SAMSUNG SP2514N
               physical id: 0.1.0
               bus info: scsi@0:0.1.0
               logical name: /dev/sdb
               version: VF10
               serial: S08BJ1FLC21586
               size: 232GiB (250GB)
               capabilities: partitioned partitioned:dos
               configuration: ansiversion=5 signature=00042894
             *-volume
                  description: Linux filesystem partition
                  physical id: 1
                  bus info: scsi@0:0.1.0,1
                  logical name: /dev/sdb1
                  logical name: /store
                  capacity: 232GiB
                  capabilities: primary
                  configuration: mount.fstype=xfs
mount.options=rw,relatime,noquota state=mounted
          *-cdrom
               description: DVD writer
               product: DVD_RW ND-1300A
               vendor: _NEC
               physical id: 1
               bus info: scsi@1:0.0.0
               logical name: /dev/cdrom
               logical name: /dev/cdrw
               logical name: /dev/dvd
               logical name: /dev/dvdrw
               logical name: /dev/scd0
               logical name: /dev/sr0
               version: 1.0A
               serial: [_NEC    DVD_RW ND-1300A 1.0A03122200
               capabilities: removable audio cd-r cd-rw dvd dvd-r
               configuration: ansiversion=5 status=nodisc
       *-pci:1
            description: PCI bridge
            product: nForce2 AGP
            vendor: nVidia Corporation
            physical id: 1e
            bus info: pci@0000:00:1e.0
            version: c1
            width: 32 bits
            clock: 66MHz
            capabilities: pci bus_master
            resources: memory:dc000000-deffffff
memory:c0000000-cfffffff(prefetchable)
          *-display
               description: VGA compatible controller
               product: NV44A [GeForce 6200]
               vendor: nVidia Corporation
               physical id: 0
               bus info: pci@0000:02:00.0
               version: a1
               width: 32 bits
               clock: 66MHz
               capabilities: pm agp agp-3.0 bus_master cap_list rom
               configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5
               resources: irq:19 memory:dc000000-dcffffff
memory:c0000000-cfffffff(prefetchable) memory:dd000000-ddffffff
memory:de000000-de01ffff(prefetchable)
```

---

### Post by heyup on 2011-10-14
> **barbex said:**
> Huh, how interesting!

So let's see:
```

cat /sys/devices/system/clocksource/clocksource0/available_clocksource
acpi_pm 
```

Not much to choose from. I don't understand how it could ever work with TSC if that is not even listed.

I have the same problem with similar Asus motherboard. "Marking TSC unstable due to cpufreq changes", but tsc is not listed.

Did you ever find a solution to this problem?

---

### Post by barbex on 2011-10-14
Nope, it is still occasionally happening but rarely. I'm convinced by now that the message "Marking TSC unstable due to cpufreq changes" has actually nothing to do with the problem but just happens to be the last message that got posted before whatever made the system lock up. 
Sorry, I can't help you, I have given up on it.

---

### Post by heyup on 2011-10-15
Thank you for confirming no solution found.

Perhaps the problem is related to the motherboard/CPU/BIOS as I have ASUS A7N8X2 motherboard and AMD Athlon(tm) XP 2600+

The problem started with a clean install of 10.04 Lucid, but only occurs intermittently.

---

