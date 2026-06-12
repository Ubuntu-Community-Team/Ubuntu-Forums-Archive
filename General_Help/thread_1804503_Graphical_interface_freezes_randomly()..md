---
title: "Graphical interface freezes randomly(?)."
date: 2011-07-14
forum: General Help
---

### Post by sea52020 on 2011-07-14
Hi guys, 
I'm having some problems that seems occurs randomly...

Direct to the problem:
I recently upgraded to 11.04, sometimes suddenly everything freezes except mouse.
by freezes i mean totally not responding any more. cannot move windows, cannot open unity menu(press super key..i think it's called unity menu?)

Mostlikely, it happens when I try to run something. For example, last time when i tried to run skype, i started from unity search and pressed enter. nothing happened but the world stopped(except mouse). skype window doesn't open yet the search menu and unity dock is grey and stayed there. I cannot do anything. 
HOWEVER, I re-installed skype then I can do exactly the same after.

The problem isn't just skype. I installed netbean the day before yesterday, trying to open it and it happened again.
10 minutes ago I tried to open 'about:config', it happened.
In general word I would say, re-install doesn't always solve the problem and it is happening when trying to start an app, no matter it's from command line or search or just click on the icon on the dock.


The system doesn't freeze though, I can switch to other terminals(ctrl+alt+Fx) without any difficulty.

Since I'm dual booting with win7(for starcraft2...), and there's sometime the system report that the graphical card stopped responding when the system starts, and sometime i got a black screen after loading a map when running startcraft2, I think it may be a problem with the graphic card? That's just a personal thought..
I'm using NVidia GTX465 with the latest driver in win7 and recommended driver in ubuntu.

I searched for the problem but it seems most people are having graphic issues when the system starts, while I'm totally ok to use the system just sometimes it freezes when starting apps. In addition, I don't think certain apps causes this because I ran about:config before and it's ok but today it freezes my system.

It's really annoying since the only thing I can do is goto terminal and use reboot to get the interface back to work...

Is there any other info you guys need to know?

Any thing helps, I really appreciate, or even a way to restart the graphics without rebooting will be really great to me.

Thanks.


Update: 
 found that whenever I want to modify(i tried move files in and out only, so i guess it's modify) the home folder, the graphic will freeze. the file moving process is done though.
and I can use sudo killall Xorg to get the gui work again.
still wondering why is that and how to fix it.
thank you.

Another update:
So I tired creating folder, and it is ture that the home folder cannot have any modification or the gui freezes.
Ran the System Test, when it goes to the application test to open OpenOffice, it freezes when the loading bar is like half way.

---

### Post by wildmanne39 on 2011-07-14
Hi, here is a link on freezing.
[https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)

---

### Post by sea52020 on 2011-07-17
> **wildmanne39 said:**
> Hi, here is a link on freezing.
[https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)

Thank you.

The guild explains the problem.
and in the beginning of the guild, it says "X stops responding to input (sometimes mouse cursor can still move, but clicking has no effect)" (that's exactly what i got) is covered in the guild.
However, non of the solution there helps... 
I now have the logs it mentions yet I didn't find anything the guild describes..

it's even getting worse tonight seems, i got black screen twice tonight and the freeze still occur sometime(one when i was opening this form and the other one was when i trying to sftp to get the log files from my phone storage, i stored them there when the freeze occured).

I'm trying to reinstall the driver now to see what happens...

---

### Post by sea52020 on 2011-07-17
any help?

---

### Post by wildmanne39 on 2011-07-17
> **sea52020 said:**
> any help?
Hi, run these commands in a terminal
```
sudo lshw
```
```
lsmod
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.

---

### Post by sea52020 on 2011-07-17
this is the output of ```
lsmod
```


```
Module                  Size  Used by
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
snd_hda_codec_nvhdmi    13615  4 
nvidia              10678255  50 
snd_hda_codec_via      51851  1 
snd_hda_intel          22235  2 
snd_hda_codec          87552  3 snd_hda_codec_nvhdmi,snd_hda_codec_via,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
joydev                  8767  0 
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
rt2870sta             406690  1 
snd_seq_midi_event      6047  1 snd_seq_midi
crc_ccitt               1351  1 rt2870sta
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                59033  0 
serio_raw               4022  0 
asus_atk0110           11423  0 
snd                    49102  13 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
agpgart                32011  1 nvidia
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
hid_logitech            8971  0 
ff_memless              4393  1 hid_logitech
usbhid                 36882  1 hid_logitech
ahci                   19326  0 
hid                    67742  2 hid_logitech,usbhid
pata_jmicron            1855  0 
usb_storage            40492  0 
libahci                21728  1 ahci
xhci_hcd               54269  0 
firewire_ohci          21234  0 
firewire_core          46643  1 firewire_ohci
crc_itu_t               1383  1 firewire_core
r8169                  36553  0 
mii                     4425  1 r8169

```

---

### Post by sea52020 on 2011-07-17
and ```
lshw
```:

```
~$ sudo lshw
[sudo] password for acedia: 
acedia-ubuntu             
    description: Desktop Computer
    product: System Product Name (To Be Filled By O.E.M.)
    vendor: System manufacturer
    version: System Version
    serial: System Serial Number
    width: 32 bits
    capabilities: smbios-2.6 dmi-2.6 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=4 family=To Be Filled By O.E.M. sku=To Be Filled By O.E.M. uuid=20B5001E-8C00-00D6-20DA-485B3959815A
  *-core
       description: Motherboard
       product: P7P55D-E PRO
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: Rev 1.xx
       serial: 104812470000198
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 0806
          date: 03/25/2010
          size: 64KiB
          capacity: 1984KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Core(TM) i5 CPU         750  @ 2.67GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.14.5
          serial: 0001-06E5-0000-0000-0000-0000
          slot: LGA1156
          size: 2533MHz
          capacity: 3800MHz
          width: 64 bits
          clock: 133MHz
          capabilities: x86-64 boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm ida tpr_shadow vnmi flexpriority ept vpid cpufreq
          configuration: cores=4 enabledcores=4 id=2 threads=4
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: internal write-through instruction
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: internal write-through unified
        *-cache:2
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             size: 8MiB
             capacity: 8MiB
             capabilities: internal write-back unified
        *-logicalcpu:0
             description: Logical CPU
             physical id: 2.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 2.2
             width: 64 bits
             capabilities: logical
        *-logicalcpu:2
             description: Logical CPU
             physical id: 2.3
             width: 64 bits
             capabilities: logical
        *-logicalcpu:3
             description: Logical CPU
             physical id: 2.4
             width: 64 bits
             capabilities: logical
        *-logicalcpu:4
             description: Logical CPU
             physical id: 2.5
             width: 64 bits
             capabilities: logical
        *-logicalcpu:5
             description: Logical CPU
             physical id: 2.6
             width: 64 bits
             capabilities: logical
        *-logicalcpu:6
             description: Logical CPU
             physical id: 2.7
             width: 64 bits
             capabilities: logical
        *-logicalcpu:7
             description: Logical CPU
             physical id: 2.8
             width: 64 bits
             capabilities: logical
        *-logicalcpu:8
             description: Logical CPU
             physical id: 2.9
             width: 64 bits
             capabilities: logical
        *-logicalcpu:9
             description: Logical CPU
             physical id: 2.a
             width: 64 bits
             capabilities: logical
        *-logicalcpu:10
             description: Logical CPU
             physical id: 2.b
             width: 64 bits
             capabilities: logical
        *-logicalcpu:11
             description: Logical CPU
             physical id: 2.c
             width: 64 bits
             capabilities: logical
        *-logicalcpu:12
             description: Logical CPU
             physical id: 2.d
             width: 64 bits
             capabilities: logical
        *-logicalcpu:13
             description: Logical CPU
             physical id: 2.e
             width: 64 bits
             capabilities: logical
        *-logicalcpu:14
             description: Logical CPU
             physical id: 2.f
             width: 64 bits
             capabilities: logical
        *-logicalcpu:15
             description: Logical CPU
             physical id: 2.10
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 35
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: DIMM DDR Synchronous 1333 MHz (0.8 ns)
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 2GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: DIMM DDR Synchronous 1333 MHz (0.8 ns)
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
             size: 2GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:2
             description: DIMM DDR Synchronous 1333 MHz (0.8 ns)
             product: PartNum2
             vendor: Manufacturer2
             physical id: 2
             serial: SerNum2
             slot: DIMM2
             size: 2GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:3
             description: DIMM DDR Synchronous 1333 MHz (0.8 ns)
             product: PartNum3
             vendor: Manufacturer3
             physical id: 3
             serial: SerNum3
             slot: DIMM3
             size: 2GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.14.5
          serial: 0001-06E5-0000-0000-0000-0000
          size: 1200MHz
          capacity: 1200MHz
          capabilities: vmx ht cpufreq
          configuration: id=2
        *-logicalcpu:0
             description: Logical CPU
             physical id: 2.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 2.2
             capabilities: logical
        *-logicalcpu:2
             description: Logical CPU
             physical id: 2.3
             capabilities: logical
        *-logicalcpu:3
             description: Logical CPU
             physical id: 2.4
             capabilities: logical
        *-logicalcpu:4
             description: Logical CPU
             physical id: 2.5
             capabilities: logical
        *-logicalcpu:5
             description: Logical CPU
             physical id: 2.6
             capabilities: logical
        *-logicalcpu:6
             description: Logical CPU
             physical id: 2.7
             capabilities: logical
        *-logicalcpu:7
             description: Logical CPU
             physical id: 2.8
             capabilities: logical
        *-logicalcpu:8
             description: Logical CPU
             physical id: 2.9
             capabilities: logical
        *-logicalcpu:9
             description: Logical CPU
             physical id: 2.a
             capabilities: logical
        *-logicalcpu:10
             description: Logical CPU
             physical id: 2.b
             capabilities: logical
        *-logicalcpu:11
             description: Logical CPU
             physical id: 2.c
             capabilities: logical
        *-logicalcpu:12
             description: Logical CPU
             physical id: 2.d
             capabilities: logical
        *-logicalcpu:13
             description: Logical CPU
             physical id: 2.e
             capabilities: logical
        *-logicalcpu:14
             description: Logical CPU
             physical id: 2.f
             capabilities: logical
        *-logicalcpu:15
             description: Logical CPU
             physical id: 2.10
             capabilities: logical
     *-cpu:2
          physical id: 2
          bus info: cpu@2
          version: 6.14.5
          serial: 0001-06E5-0000-0000-0000-0000
          size: 1200MHz
          capacity: 1200MHz
          capabilities: vmx ht cpufreq
          configuration: id=2
        *-logicalcpu:0
             description: Logical CPU
             physical id: 2.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 2.2
             capabilities: logical
        *-logicalcpu:2
             description: Logical CPU
             physical id: 2.3
             capabilities: logical
        *-logicalcpu:3
             description: Logical CPU
             physical id: 2.4
             capabilities: logical
        *-logicalcpu:4
             description: Logical CPU
             physical id: 2.5
             capabilities: logical
        *-logicalcpu:5
             description: Logical CPU
             physical id: 2.6
             capabilities: logical
        *-logicalcpu:6
             description: Logical CPU
             physical id: 2.7
             capabilities: logical
        *-logicalcpu:7
             description: Logical CPU
             physical id: 2.8
             capabilities: logical
        *-logicalcpu:8
             description: Logical CPU
             physical id: 2.9
             capabilities: logical
        *-logicalcpu:9
             description: Logical CPU
             physical id: 2.a
             capabilities: logical
        *-logicalcpu:10
             description: Logical CPU
             physical id: 2.b
             capabilities: logical
        *-logicalcpu:11
             description: Logical CPU
             physical id: 2.c
             capabilities: logical
        *-logicalcpu:12
             description: Logical CPU
             physical id: 2.d
             capabilities: logical
        *-logicalcpu:13
             description: Logical CPU
             physical id: 2.e
             capabilities: logical
        *-logicalcpu:14
             description: Logical CPU
             physical id: 2.f
             capabilities: logical
        *-logicalcpu:15
             description: Logical CPU
             physical id: 2.10
             capabilities: logical
     *-cpu:3
          physical id: 3
          bus info: cpu@3
          version: 6.14.5
          serial: 0001-06E5-0000-0000-0000-0000
          size: 2533MHz
          capacity: 2533MHz
          capabilities: vmx ht cpufreq
          configuration: id=2
        *-logicalcpu:0
             description: Logical CPU
             physical id: 2.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 2.2
             capabilities: logical
        *-logicalcpu:2
             description: Logical CPU
             physical id: 2.3
             capabilities: logical
        *-logicalcpu:3
             description: Logical CPU
             physical id: 2.4
             capabilities: logical
        *-logicalcpu:4
             description: Logical CPU
             physical id: 2.5
             capabilities: logical
        *-logicalcpu:5
             description: Logical CPU
             physical id: 2.6
             capabilities: logical
        *-logicalcpu:6
             description: Logical CPU
             physical id: 2.7
             capabilities: logical
        *-logicalcpu:7
             description: Logical CPU
             physical id: 2.8
             capabilities: logical
        *-logicalcpu:8
             description: Logical CPU
             physical id: 2.9
             capabilities: logical
        *-logicalcpu:9
             description: Logical CPU
             physical id: 2.a
             capabilities: logical
        *-logicalcpu:10
             description: Logical CPU
             physical id: 2.b
             capabilities: logical
        *-logicalcpu:11
             description: Logical CPU
             physical id: 2.c
             capabilities: logical
        *-logicalcpu:12
             description: Logical CPU
             physical id: 2.d
             capabilities: logical
        *-logicalcpu:13
             description: Logical CPU
             physical id: 2.e
             capabilities: logical
        *-logicalcpu:14
             description: Logical CPU
             physical id: 2.f
             capabilities: logical
        *-logicalcpu:15
             description: Logical CPU
             physical id: 2.10
             capabilities: logical
     *-pci
          description: Host bridge
          product: Core Processor DMI
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 11
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Core Processor PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: pci msi pciexpress pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:45 ioport:a000(size=4096) memory:f8000000-fb8fffff ioport:d4000000(size=201326592)
           *-display
                description: VGA compatible controller
                product: nVidia Corporation
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a3
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:f8000000-f9ffffff memory:d8000000-dfffffff memory:d4000000-d7ffffff ioport:ac00(size=128) memory:fb800000-fb87ffff
           *-multimedia
                description: Audio device
                product: GF100 High Definition Audio Controller
                vendor: nVidia Corporation
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=HDA Intel latency=0
                resources: irq:17 memory:fb8fc000-fb8fffff
        *-generic:0 UNCLAIMED
             description: System peripheral
             product: Core Processor System Management Registers
             vendor: Intel Corporation
             physical id: 8
             bus info: pci@0000:00:08.0
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: pciexpress cap_list
             configuration: latency=0
        *-generic:1 UNCLAIMED
             description: System peripheral
             product: Core Processor Semaphore and Scratchpad Registers
             vendor: Intel Corporation
             physical id: 8.1
             bus info: pci@0000:00:08.1
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: pciexpress cap_list
             configuration: latency=0
        *-generic:2 UNCLAIMED
             description: System peripheral
             product: Core Processor System Control and Status Registers
             vendor: Intel Corporation
             physical id: 8.2
             bus info: pci@0000:00:08.2
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: pciexpress cap_list
             configuration: latency=0
        *-generic:3 UNCLAIMED
             description: System peripheral
             product: Core Processor Miscellaneous Registers
             vendor: Intel Corporation
             physical id: 8.3
             bus info: pci@0000:00:08.3
             version: 11
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-generic:4 UNCLAIMED
             description: System peripheral
             product: Core Processor QPI Link
             vendor: Intel Corporation
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 11
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-generic:5 UNCLAIMED
             description: System peripheral
             product: Core Processor QPI Routing and Protocol Registers
             vendor: Intel Corporation
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: 11
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-usb:0
             description: USB Controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:f7ffe000-f7ffe3ff
        *-multimedia
             description: Audio device
             product: 5 Series/3400 Series Chipset High Definition Audio
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:57 memory:f7ff8000-f7ffbfff
        *-pci:1
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:46 ioport:d000(size=4096) memory:fbb00000-fbdfffff
           *-pci
                description: PCI bridge
                product: PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch
                vendor: PLX Technology, Inc.
                physical id: 0
                bus info: pci@0000:06:00.0
                version: ba
                width: 32 bits
                clock: 33MHz
                capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
                configuration: driver=pcieport
                resources: irq:51 memory:fbbe0000-fbbfffff ioport:d000(size=4096) memory:fbc00000-fbdfffff
              *-pci:0
                   description: PCI bridge
                   product: PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch
                   vendor: PLX Technology, Inc.
                   physical id: 1
                   bus info: pci@0000:07:01.0
                   version: ba
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
                   configuration: driver=pcieport
                   resources: irq:52 memory:fbc00000-fbcfffff
                 *-usb
                      description: USB Controller
                      product: uPD720200 USB 3.0 Host Controller
                      vendor: NEC Corporation
                      physical id: 0
                      bus info: pci@0000:08:00.0
                      version: 03
                      width: 64 bits
                      clock: 33MHz
                      capabilities: pm msi msix pciexpress xhci bus_master cap_list
                      configuration: driver=xhci_hcd latency=0
                      resources: irq:17 memory:fbcfe000-fbcfffff
              *-pci:1
                   description: PCI bridge
                   product: PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch
                   vendor: PLX Technology, Inc.
                   physical id: 5
                   bus info: pci@0000:07:05.0
                   version: ba
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
                   configuration: driver=pcieport
                   resources: irq:53 ioport:d000(size=4096) memory:fbd00000-fbdfffff
                 *-ide UNCLAIMED
                      description: IDE interface
                      product: Marvell Technology Group Ltd.
                      vendor: Marvell Technology Group Ltd.
                      physical id: 0
                      bus info: pci@0000:09:00.0
                      version: 10
                      width: 32 bits
                      clock: 33MHz
                      capabilities: ide pm msi pciexpress cap_list
                      configuration: latency=0
                      resources: ioport:dc00(size=8) ioport:d880(size=4) ioport:d800(size=8) ioport:d480(size=4) ioport:d400(size=16) memory:fbdff000-fbdff7ff memory:fbde0000-fbdeffff
              *-pci:2
                   description: PCI bridge
                   product: PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch
                   vendor: PLX Technology, Inc.
                   physical id: 7
                   bus info: pci@0000:07:07.0
                   version: ba
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
                   configuration: driver=pcieport
                   resources: irq:54
              *-pci:3
                   description: PCI bridge
                   product: PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch
                   vendor: PLX Technology, Inc.
                   physical id: 9
                   bus info: pci@0000:07:09.0
                   version: ba
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
                   configuration: driver=pcieport
                   resources: irq:55
        *-pci:2
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:47 ioport:c000(size=4096) memory:fba00000-fbafffff ioport:f6f00000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:05:00.0
                logical name: eth0
                version: 03
                serial: 48:5b:39:59:81:5a
                size: 10Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:56 ioport:c800(size=256) memory:f6fff000-f6ffffff memory:f6ff8000-f6ffbfff memory:fbaf0000-fbafffff
        *-pci:3
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:48
        *-pci:4
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 7
             vendor: Intel Corporation
             physical id: 1c.6
             bus info: pci@0000:00:1c.6
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:49 ioport:b000(size=4096) memory:fb900000-fb9fffff
           *-storage
                description: SATA controller
                product: JMB362/JMB363 Serial ATA Controller
                vendor: JMicron Technology Corp.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm pciexpress ahci_1.0 bus_master cap_list
                configuration: driver=ahci latency=0
                resources: irq:18 memory:fb9fe000-fb9fffff
           *-ide
                description: IDE interface
                product: JMB362/JMB363 Serial ATA Controller
                vendor: JMicron Technology Corp.
                physical id: 0.1
                bus info: pci@0000:03:00.1
                logical name: scsi5
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: ide pm bus_master cap_list emulated
                configuration: driver=pata_jmicron latency=0
                resources: irq:19 ioport:bc00(size=8) ioport:b880(size=4) ioport:b800(size=8) ioport:b480(size=4) ioport:b400(size=16)
              *-cdrom
                   description: DVD-RAM writer
                   product: DVD-RAM GH22NP20
                   vendor: HL-DT-ST
                   physical id: 0.0.0
                   bus info: scsi@5:0.0.0
                   logical name: /dev/cdrom
                   logical name: /dev/cdrw
                   logical name: /dev/dvd
                   logical name: /dev/dvdrw
                   logical name: /dev/scd0
                   logical name: /dev/sr0
                   version: 2.00
                   capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                   configuration: ansiversion=5 status=nodisc
        *-pci:5
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 8
             vendor: Intel Corporation
             physical id: 1c.7
             bus info: pci@0000:00:1c.7
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:50 ioport:1000(size=4096) memory:c0000000-c01fffff ioport:c0200000(size=2097152)
        *-usb:1
             description: USB Controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:f7ffd000-f7ffd3ff
        *-pci:6
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: a6
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:e000(size=4096) memory:fbe00000-fbefffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller
                vendor: VIA Technologies, Inc.
                physical id: 3
                bus info: pci@0000:0c:03.0
                version: c0
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=64 maxlatency=32
                resources: irq:18 memory:fbeff000-fbeff7ff ioport:ec00(size=128)
        *-isa
             description: ISA bridge
             product: 5 Series Chipset LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 5 Series/3400 Series Chipset 4 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 06
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:21 ioport:8c00(size=8) ioport:8880(size=4) ioport:8800(size=8) ioport:8480(size=4) ioport:8400(size=16) ioport:8080(size=16)
           *-disk:0
                description: ATA Disk
                product: WDC WD10EARS-00Z
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 80.0
                serial: WD-WMAVU1345923
                size: 931GiB (1TB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=63ff5887
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 3a20-2a87
                   size: 98MiB
                   capacity: 100MiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2010-08-14 15:07:46 filesystem=ntfs label=System Reserved state=clean
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 3.1
                   serial: 2aa6d6b0-2d6b-d64c-b9e2-e135bd39ef3a
                   size: 52GiB
                   capacity: 52GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2010-08-14 15:09:36 filesystem=ntfs label=WindowsSystem modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
              *-volume:2
                   description: Windows NTFS volume
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   version: 3.1
                   serial: ca252aa0-57ab-0846-b80d-4c7847f18809
                   size: 97GiB
                   capacity: 97GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2010-08-14 01:29:34 filesystem=ntfs label=Datas(WIN) state=clean
              *-volume:3
                   description: Windows NTFS volume
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   version: 3.1
                   serial: 3e62d0f1-f0aa-0240-8c77-21ea4cdf2674
                   size: 781GiB
                   capacity: 781GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2010-08-14 01:30:04 filesystem=ntfs label=Others state=clean
           *-disk:1
                description: ATA Disk
                product: WDC WD10EARS-00Y
                vendor: Western Digital
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/sdb
                version: 80.0
                serial: WD-WCAV58952607
                size: 931GiB (1TB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=864680d4
              *-volume:0
                   description: HPFS/NTFS partition
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: /dev/sdb1
                   capacity: 83GiB
                   capabilities: primary
              *-volume:1
                   description: Linux swap volume
                   physical id: 2
                   bus info: scsi@1:0.0.0,2
                   logical name: /dev/sdb2
                   version: 1
                   serial: 2f2a0aa8-274c-46d9-a2a6-ef105d99a9ee
                   size: 488GiB
                   capacity: 488GiB
                   capabilities: primary nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
              *-volume:2
                   description: Extended partition
                   physical id: 3
                   bus info: scsi@1:0.0.0,3
                   logical name: /dev/sdb3
                   size: 262GiB
                   capacity: 262GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: HPFS/NTFS partition
                      physical id: 5
                      logical name: /dev/sdb5
                      capacity: 262GiB
              *-volume:3
                   description: Linux filesystem partition
                   vendor: Linux
                   physical id: 4
                   bus info: scsi@1:0.0.0,4
                   logical name: /dev/sdb4
                   logical name: /
                   version: 1.0
                   serial: 56fc7a7f-d6e2-40d2-9e6b-d06b715b7b15
                   size: 97GiB
                   capacity: 97GiB
                   capabilities: primary ext2 initialized
                   configuration: filesystem=ext2 modified=2011-07-17 17:06:40 mount.fstype=ext2 mount.options=rw,relatime,errors=remount-ro mounted=2011-07-17 17:06:40 state=mounted
        *-serial UNCLAIMED
             description: SMBus
             product: 5 Series/3400 Series Chipset SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 06
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f7ffc000-f7ffc0ff ioport:ffe0(size=32)
        *-ide:1
             description: IDE interface
             product: 5 Series/3400 Series Chipset 2 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 06
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:21 ioport:9c00(size=8) ioport:9880(size=4) ioport:9800(size=8) ioport:9480(size=4) ioport:9400(size=16) ioport:9080(size=16)
     *-scsi
          physical id: 5
          bus info: usb@1:1.1
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdc
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@4:0.0.1
             logical name: /dev/sdd
        *-disk:2
             description: SCSI Disk
             physical id: 0.0.2
             bus info: scsi@4:0.0.2
             logical name: /dev/sde
        *-disk:3
             description: SCSI Disk
             product: MS/MS-Pro
             vendor: Generic-
             physical id: 0.0.3
             bus info: scsi@4:0.0.3
             logical name: /dev/sdf
             version: 1.03
             serial: 3
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdf
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:08:10:76:13:36
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.25 multicast=yes wireless=Ralink STA

```

---

### Post by wildmanne39 on 2011-07-17
Hi, I saw somethings that I have never seen before in the information that you gave me, I am not sure that there is anything wrong though with what I saw.

The next time you have a freeze as soon as you get back into your system open log file viewer and see what  dmesg log tells you, if you need help with it post the information here.

---

### Post by sea52020 on 2011-07-18
> **wildmanne39 said:**
> Hi, I saw somethings that I have never seen before in the information that you gave me, I am not sure that there is anything wrong though with what I saw.

The next time you have a freeze as soon as you get back into your system open log file viewer and see what  dmesg log tells you, if you need help with it post the information here.

Hi.
I have a Xorg.0.log file copy that I got it when the freeze occurs by ssh into it.
I can make it freeze now and get the dmesg. (actually i had one but it's "missing" somehow..)

---

### Post by sea52020 on 2011-07-18
> **wildmanne39 said:**
> Hi, I saw somethings that I have never seen before in the information that you gave me, I am not sure that there is anything wrong though with what I saw.

The next time you have a freeze as soon as you get back into your system open log file viewer and see what  dmesg log tells you, if you need help with it post the information here.


dmesg
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.35-30-generic (buildd@rothera) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #54-Ubuntu SMP Tue Jun 7 18:40:23 UTC 2011 (Ubuntu 2.6.35-30.54-generic 2.6.35.13)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bf770000 (usable)
[    0.000000]  BIOS-e820: 00000000bf770000 - 00000000bf788000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bf788000 - 00000000bf7dc000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bf7dc000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000240000000 (usable)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI 2.6 present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0xbf770 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-D3FFF write-protect
[    0.000000]   D4000-DFFFF uncachable
[    0.000000]   E0000-E7FFF write-through
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask E00000000 write-back
[    0.000000]   1 base 200000000 mask FC0000000 write-back
[    0.000000]   2 base 0C0000000 mask FC0000000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000c0000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000bf770000 (usable)
[    0.000000]  modified: 00000000bf770000 - 00000000bf788000 (ACPI data)
[    0.000000]  modified: 00000000bf788000 - 00000000bf7dc000 (ACPI NVS)
[    0.000000]  modified: 00000000bf7dc000 - 00000000c0000000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000240000000 (usable)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 15000-1a000
[    0.000000] RAMDISK: 3686e000 - 3742f000
[    0.000000] ACPI: RSDP 000fbb00 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT bf770000 00048 (v01 032510 RSDT2140 20100325 MSFT 00000097)
[    0.000000] ACPI: FACP bf770200 00084 (v01 032510 FACP2140 20100325 MSFT 00000097)
[    0.000000] ACPI: DSDT bf7704a0 0EDBE (v01  A1513 A1513003 00000003 INTL 20060113)
[    0.000000] ACPI: FACS bf788000 00040
[    0.000000] ACPI: APIC bf770390 000CC (v01 032510 APIC2140 20100325 MSFT 00000097)
[    0.000000] ACPI: MCFG bf770460 0003C (v01 032510 OEMMCFG  20100325 MSFT 00000097)
[    0.000000] ACPI: OEMB bf788040 00072 (v01 032510 OEMB2140 20100325 MSFT 00000097)
[    0.000000] ACPI: HPET bf77f7a0 00038 (v01 032510 OEMHPET  20100325 MSFT 00000097)
[    0.000000] ACPI: DMAR bf7880c0 00090 (v01    AMI  OEMDMAR 00000001 MSFT 00000097)
[    0.000000] ACPI: ASPT bf77fa40 00034 (v06 032510 PerfTune 20100325 MSFT 00000097)
[    0.000000] ACPI: OSFR bf77fa80 000B0 (v01 032510 OEMOSFR  20100325 MSFT 00000097)
[    0.000000] ACPI: SSDT bf789070 00363 (v01 DpgPmm    CpuPm 00000012 INTL 20060113)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 2175MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x000bf770
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000bf770
[    0.000000] On node 0 totalpages: 784127
[    0.000000] free_area_init_node: node 0, pgdat c0802000, node_mem_map c1001200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 4351 pages used for memmap
[    0.000000]   HighMem zone: 552563 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x84] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x85] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x86] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x87] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x09] lapic_id[0x88] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0a] lapic_id[0x89] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0b] lapic_id[0x8a] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0c] lapic_id[0x8b] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0d] lapic_id[0x8c] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0e] lapic_id[0x8d] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0f] lapic_id[0x8e] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x10] lapic_id[0x8f] disabled)
[    0.000000] ACPI: IOAPIC (id[0x07] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 7, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] 16 Processors exceeds NR_CPUS limit of 8
[    0.000000] SMP: Allowing 8 CPUs, 4 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] early_res array is doubled to 64 at [16000 - 167ff]
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:3ee00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c2c00000 s36416 r0 d20928 u524288
[    0.000000] pcpu-alloc: s36416 r0 d20928 u524288 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 778000
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-30-generic root=UUID=56fc7a7f-d6e2-40d2-9e6b-d06b715b7b15 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 15684480 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Subtract (55 early reservations)
[    0.000000]   #1 [0000001000 - 0000002000]   EX TRAMPOLINE
[    0.000000]   #2 [0000100000 - 00009a4adc]   TEXT DATA BSS
[    0.000000]   #3 [003686e000 - 003742f000]         RAMDISK
[    0.000000]   #4 [00009a5000 - 00009a824c]             BRK
[    0.000000]   #5 [00000ff790 - 0000100000]   BIOS reserved
[    0.000000]   #6 [00000ff780 - 00000ff790]    MP-table mpf
[    0.000000]   #7 [000009fc00 - 00000f1310]   BIOS reserved
[    0.000000]   #8 [00000f1514 - 00000ff780]   BIOS reserved
[    0.000000]   #9 [00000f1310 - 00000f1514]    MP-table mpc
[    0.000000]   #10 [0000010000 - 0000011000]      TRAMPOLINE
[    0.000000]   #11 [0000011000 - 0000015000]     ACPI WAKEUP
[    0.000000]   #12 [0000015000 - 0000016000]         PGTABLE
[    0.000000]   #13 [0001000000 - 0001001000]         BOOTMEM
[    0.000000]   #14 [0001001000 - 00027f1000]         BOOTMEM
[    0.000000]   #15 [00027f1000 - 00027f1004]         BOOTMEM
[    0.000000]   #16 [00027f1040 - 00027f1100]         BOOTMEM
[    0.000000]   #17 [00027f1100 - 00027f1154]         BOOTMEM
[    0.000000]   #18 [00027f1180 - 00027f4180]         BOOTMEM
[    0.000000]   #19 [00027f4180 - 00027f424c]         BOOTMEM
[    0.000000]   #20 [00027f4280 - 0002800280]         BOOTMEM
[    0.000000]   #21 [0002800280 - 00028002a5]         BOOTMEM
[    0.000000]   #22 [00028002c0 - 00028002e7]         BOOTMEM
[    0.000000]   #23 [0002800300 - 0002800434]         BOOTMEM
[    0.000000]   #24 [0002800440 - 0002800480]         BOOTMEM
[    0.000000]   #25 [0002800480 - 00028004c0]         BOOTMEM
[    0.000000]   #26 [00028004c0 - 0002800500]         BOOTMEM
[    0.000000]   #27 [0002800500 - 0002800540]         BOOTMEM
[    0.000000]   #28 [0002800540 - 0002800580]         BOOTMEM
[    0.000000]   #29 [0002800580 - 00028005c0]         BOOTMEM
[    0.000000]   #30 [00028005c0 - 0002800600]         BOOTMEM
[    0.000000]   #31 [0002800600 - 0002800640]         BOOTMEM
[    0.000000]   #32 [0002800640 - 0002800680]         BOOTMEM
[    0.000000]   #33 [0002800680 - 00028006c0]         BOOTMEM
[    0.000000]   #34 [00028006c0 - 00028006d0]         BOOTMEM
[    0.000000]   #35 [0002800700 - 0002800777]         BOOTMEM
[    0.000000]   #36 [0002800780 - 00028007f7]         BOOTMEM
[    0.000000]   #37 [0002c00000 - 0002c0e000]         BOOTMEM
[    0.000000]   #38 [0002c80000 - 0002c8e000]         BOOTMEM
[    0.000000]   #39 [0002d00000 - 0002d0e000]         BOOTMEM
[    0.000000]   #40 [0002d80000 - 0002d8e000]         BOOTMEM
[    0.000000]   #41 [0002e00000 - 0002e0e000]         BOOTMEM
[    0.000000]   #42 [0002e80000 - 0002e8e000]         BOOTMEM
[    0.000000]   #43 [0002f00000 - 0002f0e000]         BOOTMEM
[    0.000000]   #44 [0002f80000 - 0002f8e000]         BOOTMEM
[    0.000000]   #45 [0002802800 - 0002802804]         BOOTMEM
[    0.000000]   #46 [0002802840 - 0002802844]         BOOTMEM
[    0.000000]   #47 [0002802880 - 00028028a0]         BOOTMEM
[    0.000000]   #48 [00028028c0 - 00028028e0]         BOOTMEM
[    0.000000]   #49 [0002802900 - 0002802998]         BOOTMEM
[    0.000000]   #50 [00028029c0 - 00028029f8]         BOOTMEM
[    0.000000]   #51 [0002802a00 - 0002806a00]         BOOTMEM
[    0.000000]   #52 [0002806a00 - 0002886a00]         BOOTMEM
[    0.000000]   #53 [0002886a00 - 00028c6a00]         BOOTMEM
[    0.000000]   #54 [0002f8e000 - 0003e83380]         BOOTMEM
[    0.000000] Initializing HighMem for node 0 (000377fe:000bf770)
[    0.000000] Memory: 3074444k/3136960k available (4941k kernel code, 62064k reserved, 2332k data, 688k init, 2227656k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc081b000 - 0xc08c7000   ( 688 kB)
[    0.000000]       .data : 0xc05d344e - 0xc081a7e8   (2332 kB)
[    0.000000]       .text : 0xc0100000 - 0xc05d344e   (4941 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU-based detection of stalled CPUs is disabled.
[    0.000000]     Verbose stalled-CPUs detection is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:744
[    0.000000] vt handoff: transparent VT on 7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.004000] Detected 2540.779 MHz processor.
[    0.000003] Calibrating delay loop (skipped), value calculated using timer frequency.. 5081.55 BogoMIPS (lpj=10163116)
[    0.000006] pid_max: default: 32768 minimum: 301
[    0.000020] Security Framework initialized
[    0.000031] AppArmor: AppArmor initialized
[    0.000032] Yama: becoming mindful.
[    0.000070] Mount-cache hash table entries: 512
[    0.000157] Initializing cgroup subsys ns
[    0.000160] Initializing cgroup subsys cpuacct
[    0.000164] Initializing cgroup subsys memory
[    0.000170] Initializing cgroup subsys devices
[    0.000172] Initializing cgroup subsys freezer
[    0.000173] Initializing cgroup subsys net_cls
[    0.000190] CPU: Physical Processor ID: 0
[    0.000192] CPU: Processor Core ID: 0
[    0.000195] mce: CPU supports 9 MCE banks
[    0.000204] CPU0: Thermal monitoring enabled (TM1)
[    0.000210] using mwait in idle threads.
[    0.000213] Performance Events: PEBS fmt1+, Nehalem events, Intel PMU driver.
[    0.000220] ... version:                3
[    0.000221] ... bit width:              48
[    0.000222] ... generic registers:      4
[    0.000224] ... value mask:             0000ffffffffffff
[    0.000225] ... max period:             000000007fffffff
[    0.000226] ... fixed-purpose events:   3
[    0.000228] ... event mask:             000000070000000f
[    0.002287] ACPI: Core revision 20100428
[    0.116549] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.116553] ftrace: allocating 21775 entries in 43 pages
[    0.122438] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.122766] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.162447] CPU0: Intel(R) Core(TM) i5 CPU         750  @ 2.67GHz stepping 05
[    0.268708] Booting Node   0, Processors  #1
[    0.279144] Initializing CPU#1
[    0.376761]  #2
[    0.387039] Initializing CPU#2
[    0.484812]  #3
[    0.495089] Initializing CPU#3
[    0.592716] Brought up 4 CPUs
[    0.592718] Total of 4 processors activated (20328.05 BogoMIPS).
[    0.594633] devtmpfs: initialized
[    0.595600] regulator: core version 0.5
[    0.595623] Time: 17:07:26  Date: 07/17/11
[    0.595651] NET: Registered protocol family 16
[    0.595718] Trying to unpack rootfs image as initramfs...
[    0.595725] EISA bus registered
[    0.595731] ACPI: bus type pci registered
[    0.595782] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.595784] PCI: not using MMCONFIG
[    0.595867] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=12
[    0.595869] PCI: Using configuration type 1 for base access
[    0.596521] bio: create slab <bio-0> at 0
[    0.598217] ACPI: EC: Look up EC in DSDT
[    0.599901] ACPI: Executed 1 blocks of module-level executable AML code
[    0.614185] ACPI: SSDT bf788150 00F20 (v01 DpgPmm  P001Ist 00000011 INTL 20060113)
[    0.614667] ACPI: Dynamic OEM Table Load:
[    0.614670] ACPI: SSDT (null) 00F20 (v01 DpgPmm  P001Ist 00000011 INTL 20060113)
[    0.615228] ACPI: Interpreter enabled
[    0.615232] ACPI: (supports S0 S1 S3 S4 S5)
[    0.615251] ACPI: Using IOAPIC for interrupt routing
[    0.615298] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.617469] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.617471] PCI: Using MMCONFIG for extended config space
[    0.627053] ACPI: EC: GPE = 0x18, I/O: command/status = 0x66, data = 0x62
[    0.627255] ACPI: No dock devices found.
[    0.627258] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.627550] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.627814] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.627816] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.627818] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.627820] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000dffff]
[    0.627822] pci_root PNP0A08:00: host bridge window [mem 0xc0000000-0xdfffffff]
[    0.627824] pci_root PNP0A08:00: host bridge window [mem 0xf0000000-0xfed8ffff]
[    0.627906] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
[    0.627909] pci 0000:00:03.0: PME# disabled
[    0.628148] pci 0000:00:1a.0: reg 10: [mem 0xf7ffe000-0xf7ffe3ff]
[    0.628198] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.628202] pci 0000:00:1a.0: PME# disabled
[    0.628233] pci 0000:00:1b.0: reg 10: [mem 0xf7ff8000-0xf7ffbfff 64bit]
[    0.628270] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.628273] pci 0000:00:1b.0: PME# disabled
[    0.628331] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.628334] pci 0000:00:1c.0: PME# disabled
[    0.628396] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.628399] pci 0000:00:1c.4: PME# disabled
[    0.628459] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.628462] pci 0000:00:1c.5: PME# disabled
[    0.628520] pci 0000:00:1c.6: PME# supported from D0 D3hot D3cold
[    0.628524] pci 0000:00:1c.6: PME# disabled
[    0.628583] pci 0000:00:1c.7: PME# supported from D0 D3hot D3cold
[    0.628586] pci 0000:00:1c.7: PME# disabled
[    0.628624] pci 0000:00:1d.0: reg 10: [mem 0xf7ffd000-0xf7ffd3ff]
[    0.628678] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.628682] pci 0000:00:1d.0: PME# disabled
[    0.628827] pci 0000:00:1f.2: reg 10: [io  0x8c00-0x8c07]
[    0.628832] pci 0000:00:1f.2: reg 14: [io  0x8880-0x8883]
[    0.628837] pci 0000:00:1f.2: reg 18: [io  0x8800-0x8807]
[    0.628842] pci 0000:00:1f.2: reg 1c: [io  0x8480-0x8483]
[    0.628847] pci 0000:00:1f.2: reg 20: [io  0x8400-0x840f]
[    0.628852] pci 0000:00:1f.2: reg 24: [io  0x8080-0x808f]
[    0.628892] pci 0000:00:1f.3: reg 10: [mem 0xf7ffc000-0xf7ffc0ff 64bit]
[    0.628904] pci 0000:00:1f.3: reg 20: [io  0xffe0-0xffff]
[    0.628938] pci 0000:00:1f.5: reg 10: [io  0x9c00-0x9c07]
[    0.628943] pci 0000:00:1f.5: reg 14: [io  0x9880-0x9883]
[    0.628948] pci 0000:00:1f.5: reg 18: [io  0x9800-0x9807]
[    0.628952] pci 0000:00:1f.5: reg 1c: [io  0x9480-0x9483]
[    0.628957] pci 0000:00:1f.5: reg 20: [io  0x9400-0x940f]
[    0.628962] pci 0000:00:1f.5: reg 24: [io  0x9080-0x908f]
[    0.629031] pci 0000:01:00.0: reg 10: [mem 0xf8000000-0xf9ffffff]
[    0.629039] pci 0000:01:00.0: reg 14: [mem 0xd8000000-0xdfffffff 64bit pref]
[    0.629047] pci 0000:01:00.0: reg 1c: [mem 0xd4000000-0xd7ffffff 64bit pref]
[    0.629052] pci 0000:01:00.0: reg 24: [io  0xac00-0xac7f]
[    0.629057] pci 0000:01:00.0: reg 30: [mem 0xfb800000-0xfb87ffff pref]
[    0.629102] pci 0000:01:00.1: reg 10: [mem 0xfb8fc000-0xfb8fffff]
[    0.636657] pci 0000:00:03.0: PCI bridge to [bus 01-01]
[    0.636661] pci 0000:00:03.0:   bridge window [io  0xa000-0xafff]
[    0.636664] pci 0000:00:03.0:   bridge window [mem 0xf8000000-0xfb8fffff]
[    0.636668] pci 0000:00:03.0:   bridge window [mem 0xd4000000-0xdfffffff 64bit pref]
[    0.636728] pci 0000:06:00.0: reg 10: [mem 0xfbbe0000-0xfbbfffff]
[    0.636781] pci 0000:06:00.0: PME# supported from D0 D3hot D3cold
[    0.636785] pci 0000:06:00.0: PME# disabled
[    0.644653] pci 0000:00:1c.0: PCI bridge to [bus 06-0b]
[    0.644657] pci 0000:00:1c.0:   bridge window [io  0xd000-0xdfff]
[    0.644660] pci 0000:00:1c.0:   bridge window [mem 0xfbb00000-0xfbdfffff]
[    0.644666] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.644797] pci 0000:07:01.0: PME# supported from D0 D3hot D3cold
[    0.644801] pci 0000:07:01.0: PME# disabled
[    0.644900] pci 0000:07:05.0: PME# supported from D0 D3hot D3cold
[    0.644904] pci 0000:07:05.0: PME# disabled
[    0.645001] pci 0000:07:07.0: PME# supported from D0 D3hot D3cold
[    0.645005] pci 0000:07:07.0: PME# disabled
[    0.645104] pci 0000:07:09.0: PME# supported from D0 D3hot D3cold
[    0.645108] pci 0000:07:09.0: PME# disabled
[    0.645159] pci 0000:06:00.0: PCI bridge to [bus 07-0b]
[    0.645165] pci 0000:06:00.0:   bridge window [io  0xd000-0xdfff]
[    0.645169] pci 0000:06:00.0:   bridge window [mem 0xfbc00000-0xfbdfffff]
[    0.645176] pci 0000:06:00.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.645274] pci 0000:08:00.0: reg 10: [mem 0xfbcfe000-0xfbcfffff 64bit]
[    0.645353] pci 0000:08:00.0: PME# supported from D0 D3hot D3cold
[    0.645358] pci 0000:08:00.0: PME# disabled
[    0.652657] pci 0000:07:01.0: PCI bridge to [bus 08-08]
[    0.652664] pci 0000:07:01.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.652669] pci 0000:07:01.0:   bridge window [mem 0xfbc00000-0xfbcfffff]
[    0.652675] pci 0000:07:01.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.652760] pci 0000:09:00.0: reg 10: [io  0xdc00-0xdc07]
[    0.652767] pci 0000:09:00.0: reg 14: [io  0xd880-0xd883]
[    0.652775] pci 0000:09:00.0: reg 18: [io  0xd800-0xd807]
[    0.652783] pci 0000:09:00.0: reg 1c: [io  0xd480-0xd483]
[    0.652790] pci 0000:09:00.0: reg 20: [io  0xd400-0xd40f]
[    0.652798] pci 0000:09:00.0: reg 24: [mem 0xfbdff000-0xfbdff7ff]
[    0.652806] pci 0000:09:00.0: reg 30: [mem 0xfbde0000-0xfbdeffff pref]
[    0.652841] pci 0000:09:00.0: PME# supported from D3hot
[    0.652846] pci 0000:09:00.0: PME# disabled
[    0.660656] pci 0000:07:05.0: PCI bridge to [bus 09-09]
[    0.660662] pci 0000:07:05.0:   bridge window [io  0xd000-0xdfff]
[    0.660666] pci 0000:07:05.0:   bridge window [mem 0xfbd00000-0xfbdfffff]
[    0.660673] pci 0000:07:05.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.660731] pci 0000:07:07.0: PCI bridge to [bus 0a-0a]
[    0.660737] pci 0000:07:07.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.660742] pci 0000:07:07.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.660748] pci 0000:07:07.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.660805] pci 0000:07:09.0: PCI bridge to [bus 0b-0b]
[    0.660812] pci 0000:07:09.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.660816] pci 0000:07:09.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.660823] pci 0000:07:09.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.660913] pci 0000:05:00.0: reg 10: [io  0xc800-0xc8ff]
[    0.660932] pci 0000:05:00.0: reg 18: [mem 0xf6fff000-0xf6ffffff 64bit pref]
[    0.660945] pci 0000:05:00.0: reg 20: [mem 0xf6ff8000-0xf6ffbfff 64bit pref]
[    0.660953] pci 0000:05:00.0: reg 30: [mem 0xfbaf0000-0xfbafffff pref]
[    0.660991] pci 0000:05:00.0: supports D1 D2
[    0.660992] pci 0000:05:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.660996] pci 0000:05:00.0: PME# disabled
[    0.668657] pci 0000:00:1c.4: PCI bridge to [bus 05-05]
[    0.668660] pci 0000:00:1c.4:   bridge window [io  0xc000-0xcfff]
[    0.668663] pci 0000:00:1c.4:   bridge window [mem 0xfba00000-0xfbafffff]
[    0.668669] pci 0000:00:1c.4:   bridge window [mem 0xf6f00000-0xf6ffffff 64bit pref]
[    0.668708] pci 0000:00:1c.5: PCI bridge to [bus 04-04]
[    0.668711] pci 0000:00:1c.5:   bridge window [io  0xf000-0x0000] (disabled)
[    0.668715] pci 0000:00:1c.5:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.668720] pci 0000:00:1c.5:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.668826] pci 0000:03:00.0: reg 24: [mem 0xfb9fe000-0xfb9fffff]
[    0.668863] pci 0000:03:00.0: PME# supported from D3hot
[    0.668868] pci 0000:03:00.0: PME# disabled
[    0.668912] pci 0000:03:00.1: reg 10: [io  0xbc00-0xbc07]
[    0.668921] pci 0000:03:00.1: reg 14: [io  0xb880-0xb883]
[    0.668929] pci 0000:03:00.1: reg 18: [io  0xb800-0xb807]
[    0.668937] pci 0000:03:00.1: reg 1c: [io  0xb480-0xb483]
[    0.668945] pci 0000:03:00.1: reg 20: [io  0xb400-0xb40f]
[    0.669003] pci 0000:03:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.669016] pci 0000:00:1c.6: PCI bridge to [bus 03-03]
[    0.669019] pci 0000:00:1c.6:   bridge window [io  0xb000-0xbfff]
[    0.669023] pci 0000:00:1c.6:   bridge window [mem 0xfb900000-0xfb9fffff]
[    0.669028] pci 0000:00:1c.6:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.669064] pci 0000:00:1c.7: PCI bridge to [bus 02-02]
[    0.669068] pci 0000:00:1c.7:   bridge window [io  0xf000-0x0000] (disabled)
[    0.669071] pci 0000:00:1c.7:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.669076] pci 0000:00:1c.7:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.669120] pci 0000:0c:03.0: reg 10: [mem 0xfbeff000-0xfbeff7ff]
[    0.669126] pci 0000:0c:03.0: reg 14: [io  0xec00-0xec7f]
[    0.669167] pci 0000:0c:03.0: supports D2
[    0.669169] pci 0000:0c:03.0: PME# supported from D2 D3hot D3cold
[    0.669173] pci 0000:0c:03.0: PME# disabled
[    0.669211] pci 0000:00:1e.0: PCI bridge to [bus 0c-0c] (subtractive decode)
[    0.669214] pci 0000:00:1e.0:   bridge window [io  0xe000-0xefff]
[    0.669218] pci 0000:00:1e.0:   bridge window [mem 0xfbe00000-0xfbefffff]
[    0.669223] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.669225] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.669227] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.669229] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.669231] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.669233] pci 0000:00:1e.0:   bridge window [mem 0xc0000000-0xdfffffff] (subtractive decode)
[    0.669235] pci 0000:00:1e.0:   bridge window [mem 0xf0000000-0xfed8ffff] (subtractive decode)
[    0.669261] pci_bus 0000:00: on NUMA node 0
[    0.669268] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.669489] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR1E._PRT]
[    0.669617] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[    0.669684] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR20._PRT]
[    0.669783] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR24._PRT]
[    0.669845] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR26._PRT]
[    0.669915] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR27._PRT]
[    0.693128] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12 14 15)
[    0.693245] ACPI: PCI Interrupt Link [LNKB] (IRQs *5)
[    0.693357] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 11 12 14 *15)
[    0.693471] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 *11 12 14 15)
[    0.693586] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12 14 15) *0, disabled.
[    0.693701] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12 *14 15)
[    0.693815] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 6 7 10 11 12 14 15)
[    0.693929] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 6 *7 10 11 12 14 15)
[    0.693977] HEST: Table is not found!
[    0.694032] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.694038] vgaarb: loaded
[    0.694148] SCSI subsystem initialized
[    0.694227] libata version 3.00 loaded.
[    0.694260] usbcore: registered new interface driver usbfs
[    0.694268] usbcore: registered new interface driver hub
[    0.694285] usbcore: registered new device driver usb
[    0.694399] ACPI: WMI: Mapper loaded
[    0.694400] PCI: Using ACPI for IRQ routing
[    0.694404] PCI: pci_cache_line_size set to 64 bytes
[    0.694506] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    0.694508] reserve RAM buffer: 00000000bf770000 - 00000000bfffffff 
[    0.694570] NetLabel: Initializing
[    0.694572] NetLabel:  domain hash size = 128
[    0.694573] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.694581] NetLabel:  unlabeled traffic allowed by default
[    0.694604]   alloc irq_desc for 40 on node -1
[    0.694606]   alloc kstat_irqs on node -1
[    0.694611]   alloc irq_desc for 41 on node -1
[    0.694612]   alloc kstat_irqs on node -1
[    0.694616]   alloc irq_desc for 42 on node -1
[    0.694617]   alloc kstat_irqs on node -1
[    0.694620]   alloc irq_desc for 43 on node -1
[    0.694621]   alloc kstat_irqs on node -1
[    0.694624]   alloc irq_desc for 44 on node -1
[    0.694626]   alloc kstat_irqs on node -1
[    0.694628] HPET: 8 timers in total, 5 timers will be used for per-cpu timer
[    0.694635] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 40, 41, 42, 43, 44, 0
[    0.694641] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.700661] hpet: hpet2 irq 40 for MSI
[    0.700746] hpet: hpet3 irq 41 for MSI
[    0.700867] hpet: hpet4 irq 42 for MSI
[    0.704743] hpet: hpet5 irq 43 for MSI
[    0.704766] Switching to clocksource tsc
[    0.712103] AppArmor: AppArmor Filesystem Enabled
[    0.712112] pnp: PnP ACPI init
[    0.712121] ACPI: bus type pnp registered
[    0.714521] pnp: PnP ACPI: found 14 devices
[    0.714523] ACPI: ACPI bus type pnp unregistered
[    0.714525] PnPBIOS: Disabled by ACPI PNP
[    0.714533] system 00:01: [mem 0xfc000000-0xfcffffff] has been reserved
[    0.714536] system 00:01: [mem 0xfd000000-0xfdffffff] has been reserved
[    0.714538] system 00:01: [mem 0xfe000000-0xfebfffff] has been reserved
[    0.714540] system 00:01: [mem 0xfed14000-0xfed19fff] has been reserved
[    0.714545] system 00:06: [io  0x0290-0x029f] has been reserved
[    0.714549] system 00:07: [io  0x04d0-0x04d1] has been reserved
[    0.714551] system 00:07: [io  0x0800-0x087f] has been reserved
[    0.714553] system 00:07: [io  0x0500-0x057f] has been reserved
[    0.714555] system 00:07: [io  0x0600-0x0607] has been reserved
[    0.714557] system 00:07: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.714559] system 00:07: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.714562] system 00:07: [mem 0xfed40000-0xfed8ffff] has been reserved
[    0.714566] system 00:0a: [mem 0xffc00000-0xffdfffff] has been reserved
[    0.714570] system 00:0b: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.714572] system 00:0b: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.714575] system 00:0c: [mem 0xe0000000-0xefffffff] has been reserved
[    0.714581] system 00:0d: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.714583] system 00:0d: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.714585] system 00:0d: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.714587] system 00:0d: [mem 0x00100000-0xbfffffff] could not be reserved
[    0.714590] system 00:0d: [mem 0xfed90000-0xffffffff] could not be reserved
[    0.750142] pci 0000:00:1c.7: BAR 14: assigned [mem 0xc0000000-0xc01fffff]
[    0.750146] pci 0000:00:1c.7: BAR 15: assigned [mem 0xc0200000-0xc03fffff 64bit pref]
[    0.750149] pci 0000:00:1c.7: BAR 13: assigned [io  0x1000-0x1fff]
[    0.750151] pci 0000:00:03.0: PCI bridge to [bus 01-01]
[    0.750153] pci 0000:00:03.0:   bridge window [io  0xa000-0xafff]
[    0.750157] pci 0000:00:03.0:   bridge window [mem 0xf8000000-0xfb8fffff]
[    0.750160] pci 0000:00:03.0:   bridge window [mem 0xd4000000-0xdfffffff 64bit pref]
[    0.750165] pci 0000:07:01.0: PCI bridge to [bus 08-08]
[    0.750166] pci 0000:07:01.0:   bridge window [io  disabled]
[    0.750171] pci 0000:07:01.0:   bridge window [mem 0xfbc00000-0xfbcfffff]
[    0.750175] pci 0000:07:01.0:   bridge window [mem pref disabled]
[    0.750182] pci 0000:07:05.0: PCI bridge to [bus 09-09]
[    0.750185] pci 0000:07:05.0:   bridge window [io  0xd000-0xdfff]
[    0.750190] pci 0000:07:05.0:   bridge window [mem 0xfbd00000-0xfbdfffff]
[    0.750194] pci 0000:07:05.0:   bridge window [mem pref disabled]
[    0.750201] pci 0000:07:07.0: PCI bridge to [bus 0a-0a]
[    0.750202] pci 0000:07:07.0:   bridge window [io  disabled]
[    0.750207] pci 0000:07:07.0:   bridge window [mem disabled]
[    0.750211] pci 0000:07:07.0:   bridge window [mem pref disabled]
[    0.750217] pci 0000:07:09.0: PCI bridge to [bus 0b-0b]
[    0.750218] pci 0000:07:09.0:   bridge window [io  disabled]
[    0.750224] pci 0000:07:09.0:   bridge window [mem disabled]
[    0.750227] pci 0000:07:09.0:   bridge window [mem pref disabled]
[    0.750234] pci 0000:06:00.0: PCI bridge to [bus 07-0b]
[    0.750237] pci 0000:06:00.0:   bridge window [io  0xd000-0xdfff]
[    0.750242] pci 0000:06:00.0:   bridge window [mem 0xfbc00000-0xfbdfffff]
[    0.750246] pci 0000:06:00.0:   bridge window [mem pref disabled]
[    0.750252] pci 0000:00:1c.0: PCI bridge to [bus 06-0b]
[    0.750255] pci 0000:00:1c.0:   bridge window [io  0xd000-0xdfff]
[    0.750259] pci 0000:00:1c.0:   bridge window [mem 0xfbb00000-0xfbdfffff]
[    0.750262] pci 0000:00:1c.0:   bridge window [mem pref disabled]
[    0.750267] pci 0000:00:1c.4: PCI bridge to [bus 05-05]
[    0.750270] pci 0000:00:1c.4:   bridge window [io  0xc000-0xcfff]
[    0.750274] pci 0000:00:1c.4:   bridge window [mem 0xfba00000-0xfbafffff]
[    0.750277] pci 0000:00:1c.4:   bridge window [mem 0xf6f00000-0xf6ffffff 64bit pref]
[    0.750282] pci 0000:00:1c.5: PCI bridge to [bus 04-04]
[    0.750284] pci 0000:00:1c.5:   bridge window [io  disabled]
[    0.750288] pci 0000:00:1c.5:   bridge window [mem disabled]
[    0.750291] pci 0000:00:1c.5:   bridge window [mem pref disabled]
[    0.750296] pci 0000:00:1c.6: PCI bridge to [bus 03-03]
[    0.750298] pci 0000:00:1c.6:   bridge window [io  0xb000-0xbfff]
[    0.750303] pci 0000:00:1c.6:   bridge window [mem 0xfb900000-0xfb9fffff]
[    0.750306] pci 0000:00:1c.6:   bridge window [mem pref disabled]
[    0.750311] pci 0000:00:1c.7: PCI bridge to [bus 02-02]
[    0.750313] pci 0000:00:1c.7:   bridge window [io  0x1000-0x1fff]
[    0.750317] pci 0000:00:1c.7:   bridge window [mem 0xc0000000-0xc01fffff]
[    0.750321] pci 0000:00:1c.7:   bridge window [mem 0xc0200000-0xc03fffff 64bit pref]
[    0.750326] pci 0000:00:1e.0: PCI bridge to [bus 0c-0c]
[    0.750328] pci 0000:00:1e.0:   bridge window [io  0xe000-0xefff]
[    0.750333] pci 0000:00:1e.0:   bridge window [mem 0xfbe00000-0xfbefffff]
[    0.750336] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.750348]   alloc irq_desc for 16 on node -1
[    0.750349]   alloc kstat_irqs on node -1
[    0.750354] pci 0000:00:03.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.750358] pci 0000:00:03.0: setting latency timer to 64
[    0.750364]   alloc irq_desc for 17 on node -1
[    0.750366]   alloc kstat_irqs on node -1
[    0.750369] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.750372] pci 0000:00:1c.0: setting latency timer to 64
[    0.750382] pci 0000:06:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.750386] pci 0000:06:00.0: setting latency timer to 64
[    0.750395] pci 0000:07:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.750399] pci 0000:07:01.0: setting latency timer to 64
[    0.750408] pci 0000:07:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.750412] pci 0000:07:05.0: setting latency timer to 64
[    0.750421]   alloc irq_desc for 19 on node -1
[    0.750422]   alloc kstat_irqs on node -1
[    0.750425] pci 0000:07:07.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.750429] pci 0000:07:07.0: setting latency timer to 64
[    0.750438] pci 0000:07:09.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.750442] pci 0000:07:09.0: setting latency timer to 64
[    0.750450] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.750453] pci 0000:00:1c.4: setting latency timer to 64
[    0.750460] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.750463] pci 0000:00:1c.5: setting latency timer to 64
[    0.750469]   alloc irq_desc for 18 on node -1
[    0.750471]   alloc kstat_irqs on node -1
[    0.750474] pci 0000:00:1c.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.750477] pci 0000:00:1c.6: setting latency timer to 64
[    0.750484] pci 0000:00:1c.7: enabling device (0104 -> 0107)
[    0.750487] pci 0000:00:1c.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.750490] pci 0000:00:1c.7: setting latency timer to 64
[    0.750495] pci 0000:00:1e.0: setting latency timer to 64
[    0.750499] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.750500] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.750502] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.750504] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.750506] pci_bus 0000:00: resource 8 [mem 0xc0000000-0xdfffffff]
[    0.750508] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfed8ffff]
[    0.750510] pci_bus 0000:01: resource 0 [io  0xa000-0xafff]
[    0.750511] pci_bus 0000:01: resource 1 [mem 0xf8000000-0xfb8fffff]
[    0.750513] pci_bus 0000:01: resource 2 [mem 0xd4000000-0xdfffffff 64bit pref]
[    0.750515] pci_bus 0000:06: resource 0 [io  0xd000-0xdfff]
[    0.750517] pci_bus 0000:06: resource 1 [mem 0xfbb00000-0xfbdfffff]
[    0.750519] pci_bus 0000:07: resource 0 [io  0xd000-0xdfff]
[    0.750521] pci_bus 0000:07: resource 1 [mem 0xfbc00000-0xfbdfffff]
[    0.750523] pci_bus 0000:08: resource 1 [mem 0xfbc00000-0xfbcfffff]
[    0.750524] pci_bus 0000:09: resource 0 [io  0xd000-0xdfff]
[    0.750526] pci_bus 0000:09: resource 1 [mem 0xfbd00000-0xfbdfffff]
[    0.750528] pci_bus 0000:05: resource 0 [io  0xc000-0xcfff]
[    0.750530] pci_bus 0000:05: resource 1 [mem 0xfba00000-0xfbafffff]
[    0.750532] pci_bus 0000:05: resource 2 [mem 0xf6f00000-0xf6ffffff 64bit pref]
[    0.750534] pci_bus 0000:03: resource 0 [io  0xb000-0xbfff]
[    0.750535] pci_bus 0000:03: resource 1 [mem 0xfb900000-0xfb9fffff]
[    0.750537] pci_bus 0000:02: resource 0 [io  0x1000-0x1fff]
[    0.750539] pci_bus 0000:02: resource 1 [mem 0xc0000000-0xc01fffff]
[    0.750541] pci_bus 0000:02: resource 2 [mem 0xc0200000-0xc03fffff 64bit pref]
[    0.750543] pci_bus 0000:0c: resource 0 [io  0xe000-0xefff]
[    0.750545] pci_bus 0000:0c: resource 1 [mem 0xfbe00000-0xfbefffff]
[    0.750546] pci_bus 0000:0c: resource 4 [io  0x0000-0x0cf7]
[    0.750548] pci_bus 0000:0c: resource 5 [io  0x0d00-0xffff]
[    0.750550] pci_bus 0000:0c: resource 6 [mem 0x000a0000-0x000bffff]
[    0.750552] pci_bus 0000:0c: resource 7 [mem 0x000d0000-0x000dffff]
[    0.750554] pci_bus 0000:0c: resource 8 [mem 0xc0000000-0xdfffffff]
[    0.750555] pci_bus 0000:0c: resource 9 [mem 0xf0000000-0xfed8ffff]
[    0.750578] NET: Registered protocol family 2
[    0.750621] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.750758] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.751335] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.751624] TCP: Hash tables configured (established 131072 bind 65536)
[    0.751625] TCP reno registered
[    0.751628] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.751636] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.751697] NET: Registered protocol family 1
[    0.751771] pci 0000:01:00.0: Boot video device
[    0.751817] PCI: CLS 32 bytes, default 64
[    0.752030] cpufreq-nforce2: No nForce2 chipset.
[    0.752048] Scanning for low memory corruption every 60 seconds
[    0.752119] audit: initializing netlink socket (disabled)
[    0.752125] type=2000 audit(1310922446.504:1): initialized
[    0.761178] highmem bounce pool size: 64 pages
[    0.761182] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.762239] VFS: Disk quotas dquot_6.5.2
[    0.762284] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.762700] fuse init (API version 7.14)
[    0.762764] msgmni has been set to 1653
[    0.847415] Freeing initrd memory: 12036k freed
[    0.851102] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.851105] io scheduler noop registered
[    0.851107] io scheduler deadline registered
[    0.851116] io scheduler cfq registered (default)
[    0.851211] pcieport 0000:00:03.0: setting latency timer to 64
[    0.851235]   alloc irq_desc for 45 on node -1
[    0.851237]   alloc kstat_irqs on node -1
[    0.851244] pcieport 0000:00:03.0: irq 45 for MSI/MSI-X
[    0.851296] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.851323]   alloc irq_desc for 46 on node -1
[    0.851324]   alloc kstat_irqs on node -1
[    0.851330] pcieport 0000:00:1c.0: irq 46 for MSI/MSI-X
[    0.851380] pcieport 0000:00:1c.4: setting latency timer to 64
[    0.851407]   alloc irq_desc for 47 on node -1
[    0.851408]   alloc kstat_irqs on node -1
[    0.851414] pcieport 0000:00:1c.4: irq 47 for MSI/MSI-X
[    0.851462] pcieport 0000:00:1c.5: setting latency timer to 64
[    0.851489]   alloc irq_desc for 48 on node -1
[    0.851490]   alloc kstat_irqs on node -1
[    0.851495] pcieport 0000:00:1c.5: irq 48 for MSI/MSI-X
[    0.851543] pcieport 0000:00:1c.6: setting latency timer to 64
[    0.851570]   alloc irq_desc for 49 on node -1
[    0.851571]   alloc kstat_irqs on node -1
[    0.851577] pcieport 0000:00:1c.6: irq 49 for MSI/MSI-X
[    0.851625] pcieport 0000:00:1c.7: setting latency timer to 64
[    0.851654]   alloc irq_desc for 50 on node -1
[    0.851655]   alloc kstat_irqs on node -1
[    0.851661] pcieport 0000:00:1c.7: irq 50 for MSI/MSI-X
[    0.851724] pcieport 0000:06:00.0: setting latency timer to 64
[    0.851765]   alloc irq_desc for 51 on node -1
[    0.851766]   alloc kstat_irqs on node -1
[    0.851775] pcieport 0000:06:00.0: irq 51 for MSI/MSI-X
[    0.851852] pcieport 0000:07:01.0: setting latency timer to 64
[    0.851893]   alloc irq_desc for 52 on node -1
[    0.851894]   alloc kstat_irqs on node -1
[    0.851903] pcieport 0000:07:01.0: irq 52 for MSI/MSI-X
[    0.851983] pcieport 0000:07:05.0: setting latency timer to 64
[    0.852024]   alloc irq_desc for 53 on node -1
[    0.852025]   alloc kstat_irqs on node -1
[    0.852033] pcieport 0000:07:05.0: irq 53 for MSI/MSI-X
[    0.852111] pcieport 0000:07:07.0: setting latency timer to 64
[    0.852152]   alloc irq_desc for 54 on node -1
[    0.852154]   alloc kstat_irqs on node -1
[    0.852162] pcieport 0000:07:07.0: irq 54 for MSI/MSI-X
[    0.852241] pcieport 0000:07:09.0: setting latency timer to 64
[    0.852283]   alloc irq_desc for 55 on node -1
[    0.852284]   alloc kstat_irqs on node -1
[    0.852292] pcieport 0000:07:09.0: irq 55 for MSI/MSI-X
[    0.852371] Firmware did not grant requested _OSC control
[    0.852374] aer 0000:00:03.0:pcie02: AER service couldn't init device: no _OSC support
[    0.852389] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.852399] Firmware did not grant requested _OSC control
[    0.852413] Firmware did not grant requested _OSC control
[    0.852419] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.852675] vesafb: framebuffer at 0xd5000000, mapped to 0xf8080000, using 3072k, total 3072k
[    0.852677] vesafb: mode is 1024x768x32, linelength=4096, pages=0
[    0.852679] vesafb: scrolling: redraw
[    0.852681] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    0.852752] Console: switching to colour frame buffer device 128x48
[    0.852773] fb0: VESA VGA frame buffer device
[    0.852789] intel_idle: MWAIT substates: 0x1120
[    0.852790] intel_idle: v0.4 model 0x1E
[    0.852791] intel_idle: lapic_timer_reliable_states 0x2
[    0.852880] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.852884] ACPI: Power Button [PWRB]
[    0.852916] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.852918] ACPI: Power Button [PWRF]
[    0.853274] ACPI: acpi_idle yielding to intel_idle
[    0.856004] ERST: Table is not found!
[    0.856020] isapnp: Scanning for PnP cards...
[    0.856150] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.857207] brd: module loaded
[    0.857590] loop: module loaded
[    0.857698] ata_piix 0000:00:1f.2: version 2.13
[    0.857709]   alloc irq_desc for 21 on node -1
[    0.857710]   alloc kstat_irqs on node -1
[    0.857715] ata_piix 0000:00:1f.2: PCI INT D -> GSI 21 (level, low) -> IRQ 21
[    0.857719] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.857747] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.857790] scsi0 : ata_piix
[    0.857850] scsi1 : ata_piix
[    0.859116] ata1: SATA max UDMA/133 cmd 0x8c00 ctl 0x8880 bmdma 0x8400 irq 21
[    0.859121] ata2: SATA max UDMA/133 cmd 0x8800 ctl 0x8480 bmdma 0x8408 irq 21
[    0.859138] ata_piix 0000:00:1f.5: PCI INT D -> GSI 21 (level, low) -> IRQ 21
[    0.859142] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    0.859169] ata_piix 0000:00:1f.5: setting latency timer to 64
[    0.859197] scsi2 : ata_piix
[    0.859235] scsi3 : ata_piix
[    0.860272] ata3: SATA max UDMA/133 cmd 0x9c00 ctl 0x9880 bmdma 0x9400 irq 21
[    0.860275] ata4: SATA max UDMA/133 cmd 0x9800 ctl 0x9480 bmdma 0x9408 irq 21
[    0.860322] pata_acpi 0000:09:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.860340] pata_acpi 0000:09:00.0: setting latency timer to 64
[    0.860351] pata_acpi 0000:09:00.0: PCI INT A disabled
[    0.860365] pata_acpi 0000:03:00.1: enabling device (0000 -> 0001)
[    0.860369] pata_acpi 0000:03:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.860385] pata_acpi 0000:03:00.1: setting latency timer to 64
[    0.860394] pata_acpi 0000:03:00.1: PCI INT B disabled
[    0.860595] Fixed MDIO Bus: probed
[    0.860619] PPP generic driver version 2.4.2
[    0.860648] tun: Universal TUN/TAP device driver, 1.6
[    0.860649] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.860698] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.860711] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.860720] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.860723] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    0.860747] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    0.860772] ehci_hcd 0000:00:1a.0: debug port 2
[    0.864667] ehci_hcd 0000:00:1a.0: cache line size of 32 is not supported
[    0.864679] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xf7ffe000
[    0.877041] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    0.877120] hub 1-0:1.0: USB hub found
[    0.877124] hub 1-0:1.0: 2 ports detected
[    0.877172]   alloc irq_desc for 23 on node -1
[    0.877173]   alloc kstat_irqs on node -1
[    0.877177] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.877185] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.877188] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    0.877213] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.877236] ehci_hcd 0000:00:1d.0: debug port 2
[    0.881116] ehci_hcd 0000:00:1d.0: cache line size of 32 is not supported
[    0.881128] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xf7ffd000
[    0.893039] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    0.893110] hub 2-0:1.0: USB hub found
[    0.893112] hub 2-0:1.0: 2 ports detected
[    0.893160] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.893173] uhci_hcd: USB Universal Host Controller Interface driver
[    0.893235] PNP: No PS/2 controller found. Probing ports directly.
[    0.896016] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.896025] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.896079] mice: PS/2 mouse device common for all mice
[    0.896150] rtc_cmos 00:03: RTC can wake from S4
[    0.896175] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.896200] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.896270] device-mapper: uevent: version 1.0.3
[    0.896343] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[    0.896414] device-mapper: multipath: version 1.1.1 loaded
[    0.896416] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.896495] EISA: Probing bus 0 at eisa.0
[    0.896496] EISA: Cannot allocate resource for mainboard
[    0.896498] Cannot allocate resource for EISA slot 1
[    0.896500] Cannot allocate resource for EISA slot 2
[    0.896501] Cannot allocate resource for EISA slot 3
[    0.896502] Cannot allocate resource for EISA slot 4
[    0.896504] Cannot allocate resource for EISA slot 5
[    0.896505] Cannot allocate resource for EISA slot 6
[    0.896506] Cannot allocate resource for EISA slot 7
[    0.896508] Cannot allocate resource for EISA slot 8
[    0.896509] EISA: Detected 0 cards.
[    0.896681] cpuidle: using governor ladder
[    0.896808] cpuidle: using governor menu
[    0.897002] TCP cubic registered
[    0.897101] NET: Registered protocol family 10
[    0.897354] lo: Disabled Privacy Extensions
[    0.897503] NET: Registered protocol family 17
[    0.898741] Using IPI No-Shortcut mode
[    0.898793] PM: Resume from disk failed.
[    0.898800] registered taskstats version 1
[    0.899214]   Magic number: 3:152:138
[    0.899220] block ram3: hash matches
[    0.899266] rtc_cmos 00:03: setting system clock to 2011-07-17 17:07:26 UTC (1310922446)
[    0.899269] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.899270] EDD information not available.
[    1.180850] isapnp: No Plug & Play device found
[    1.187673] ata3: SATA link down (SStatus 0 SControl 300)
[    1.198308] ata4: SATA link down (SStatus 0 SControl 300)
[    1.201020] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    1.321744] hub 1-1:1.0: USB hub found
[    1.321831] hub 1-1:1.0: 6 ports detected
[    1.433071] usb 2-1: new high speed USB device using ehci_hcd and address 2
[    1.565780] hub 2-1:1.0: USB hub found
[    1.565863] hub 2-1:1.0: 8 ports detected
[    1.637248] usb 1-1.1: new high speed USB device using ehci_hcd and address 3
[    1.653102] ata1.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.653114] ata1.01: SATA link down (SStatus 0 SControl 300)
[    1.657129] ata2.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.657140] ata2.01: SATA link down (SStatus 0 SControl 300)
[    1.665828] ata2.00: ATA-8: WDC WD10EARS-00Y5B1, 80.00A80, max UDMA/133
[    1.665831] ata2.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.673942] ata2.00: configured for UDMA/133
[    1.687133] ata1.00: ATA-8: WDC WD10EARS-00Z5B1, 80.00A80, max UDMA/133
[    1.687139] ata1.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.694235] ata1.00: configured for UDMA/133
[    1.694664] scsi 0:0:0:0: Direct-Access     ATA      WDC WD10EARS-00Z 80.0 PQ: 0 ANSI: 5
[    1.694806] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.694874] sd 0:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    1.694951] sd 0:0:0:0: [sda] Write Protect is off
[    1.694953] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.694970] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.695017] scsi 1:0:0:0: Direct-Access     ATA      WDC WD10EARS-00Y 80.0 PQ: 0 ANSI: 5
[    1.695082]  sda:
[    1.695109] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    1.695281] sd 1:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    1.695664] sd 1:0:0:0: [sdb] Write Protect is off
[    1.695670] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.695786] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.696519]  sdb: sdb1 sdb2 sdb3 < sda1 sda2 sda3 sda4
[    1.718432] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.730899]  sdb5 > sdb4
[    1.752890] sd 1:0:0:0: [sdb] Attached SCSI disk
[    1.753199] Freeing unused kernel memory: 688k freed
[    1.753633] Write protecting the kernel text: 4944k
[    1.753775] Write protecting the kernel read-only data: 1976k
[    1.772770] <30>udev[106]: starting version 167
[    1.795955] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.795973] r8169 0000:05:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.796004] r8169 0000:05:00.0: setting latency timer to 64
[    1.796044]   alloc irq_desc for 56 on node -1
[    1.796045]   alloc kstat_irqs on node -1
[    1.796056] r8169 0000:05:00.0: irq 56 for MSI/MSI-X
[    1.796405] r8169 0000:05:00.0: eth0: RTL8168d/8111d at 0xf803c000, 48:5b:39:59:81:5a, XID 083000c0 IRQ 56
[    1.801620] usb 1-1.5: new low speed USB device using ehci_hcd and address 4
[    1.803830] firewire_ohci 0000:0c:03.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.804580] xhci_hcd 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.804594] xhci_hcd 0000:08:00.0: setting latency timer to 64
[    1.804598] xhci_hcd 0000:08:00.0: xHCI Host Controller
[    1.804636] xhci_hcd 0000:08:00.0: new USB bus registered, assigned bus number 3
[    1.804800] xhci_hcd 0000:08:00.0: irq 17, io mem 0xfbcfe000
[    1.813559] usb usb3: No SuperSpeed endpoint companion for config 1  interface 0 altsetting 0 ep 129: using minimum values
[    1.813622] xHCI xhci_add_endpoint called for root hub
[    1.813623] xHCI xhci_check_bandwidth called for root hub
[    1.813645] hub 3-0:1.0: USB hub found
[    1.813648] hub 3-0:1.0: 4 ports detected
[    1.824510] Initializing USB Mass Storage driver...
[    1.825675] pata_jmicron 0000:03:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.825698] pata_jmicron 0000:03:00.1: setting latency timer to 64
[    1.825992] scsi4 : usb-storage 1-1.1:1.0
[    1.826051] usbcore: registered new interface driver usb-storage
[    1.826053] USB Mass Storage support registered.
[    1.826258] scsi5 : pata_jmicron
[    1.826304] scsi6 : pata_jmicron
[    1.826824] ata5: PATA max UDMA/100 cmd 0xbc00 ctl 0xb880 bmdma 0xb400 irq 19
[    1.826826] ata6: PATA max UDMA/100 cmd 0xb800 ctl 0xb480 bmdma 0xb408 irq 19
[    1.828078] ahci 0000:03:00.0: version 3.0
[    1.828092] ahci 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.841525] ahci 0000:03:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[    1.841529] ahci 0000:03:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[    1.841535] ahci 0000:03:00.0: setting latency timer to 64
[    1.848560] scsi7 : ahci
[    1.854928] scsi8 : ahci
[    1.855018] ata7: SATA max UDMA/133 abar m8192@0xfb9fe000 port 0xfb9fe100 irq 18
[    1.855022] ata8: SATA max UDMA/133 abar m8192@0xfb9fe000 port 0xfb9fe180 irq 18
[    1.904978] firewire_ohci: Added fw-ohci device 0000:0c:03.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x1
[    1.907315] usbcore: registered new interface driver hiddev
[    1.908279] generic-usb: probe of 0003:058F:6364.0001 failed with error -22
[    1.908335] usbcore: registered new interface driver usbhid
[    1.908336] usbhid: USB HID core driver
[    1.969715] usb 1-1.6: new high speed USB device using ehci_hcd and address 5
[    1.990214] ata5.00: ATAPI: HL-DT-STDVD-RAM GH22NP20, 2.00, max UDMA/66
[    2.005931] ata5.00: configured for UDMA/66
[    2.008757] scsi 5:0:0:0: CD-ROM            HL-DT-ST DVD-RAM GH22NP20 2.00 PQ: 0 ANSI: 5
[    2.012772] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.012777] Uniform CD-ROM driver Revision: 3.20
[    2.012869] sr 5:0:0:0: Attached scsi CD-ROM sr0
[    2.012914] sr 5:0:0:0: Attached scsi generic sg2 type 5
[    2.173526] ata8: SATA link down (SStatus 0 SControl 300)
[    2.177256] ata7: SATA link down (SStatus 0 SControl 300)
[    2.196814] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.0/input/input2
[    2.196876] logitech 0003:046D:C517.0002: input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1a.0-1.5/input0
[    2.201963] logitech 0003:046D:C517.0003: fixing up Logitech keyboard report descriptor
[    2.202362] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.1/input/input3
[    2.202478] logitech 0003:046D:C517.0003: input,hiddev96,hidraw1: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1a.0-1.5/input1
[    2.393863] firewire_core: created device fw0: GUID 001e8c0000d620da, S400
[    2.826431] scsi 4:0:0:0: Direct-Access     Generic- SD/MMC           1.00 PQ: 0 ANSI: 0
[    2.827180] scsi 4:0:0:1: Direct-Access     Generic- Compact Flash    1.01 PQ: 0 ANSI: 0
[    2.827929] scsi 4:0:0:2: Direct-Access     Generic- SM/xD-Picture    1.02 PQ: 0 ANSI: 0
[    2.828761] scsi 4:0:0:3: Direct-Access     Generic- MS/MS-Pro        1.03 PQ: 0 ANSI: 0 CCS
[    2.830432] sd 4:0:0:0: Attached scsi generic sg3 type 0
[    2.830544] sd 4:0:0:1: Attached scsi generic sg4 type 0
[    2.830627] sd 4:0:0:2: Attached scsi generic sg5 type 0
[    2.830709] sd 4:0:0:3: Attached scsi generic sg6 type 0
[    2.834984] sd 4:0:0:2: [sde] Attached SCSI removable disk
[    2.835714] sd 4:0:0:0: [sdc] Attached SCSI removable disk
[    2.836465] sd 4:0:0:1: [sdd] Attached SCSI removable disk
[    2.837266] sd 4:0:0:3: [sdf] Attached SCSI removable disk
[   17.891779] Adding 33554428k swap on /dev/sdb2.  Priority:-1 extents:1 across:33554428k 
[   17.907033] <30>udev[430]: starting version 167
[   17.926518] lp: driver loaded but no devices found
[   17.940433] Linux agpgart interface v0.103
[   18.018361] ATK0110 ATK0110:00: EC enabled
[   18.044356] nvidia: module license 'NVIDIA' taints kernel.
[   18.044359] Disabling lock debugging due to kernel taint
[   18.058120] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   18.062750] rtusb init --->
[   18.062822] === pAd = fa5c9000, size = 472668 ===
[   18.062824] <-- RTMPAllocAdapterBlock, Status=0
[   18.063925] usbcore: registered new interface driver rt2870
[   18.066338] type=1400 audit(1310947663.663:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=660 comm="apparmor_parser"
[   18.066908] type=1400 audit(1310947663.663:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=660 comm="apparmor_parser"
[   18.067275] type=1400 audit(1310947663.663:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=660 comm="apparmor_parser"
[   18.070500] type=1400 audit(1310947663.667:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=706 comm="apparmor_parser"
[   18.071071] type=1400 audit(1310947663.667:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=706 comm="apparmor_parser"
[   18.071438] type=1400 audit(1310947663.667:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=706 comm="apparmor_parser"
[   18.118884]   alloc irq_desc for 22 on node -1
[   18.118886]   alloc kstat_irqs on node -1
[   18.118891] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   18.118925]   alloc irq_desc for 57 on node -1
[   18.118927]   alloc kstat_irqs on node -1
[   18.118934] HDA Intel 0000:00:1b.0: irq 57 for MSI/MSI-X
[   18.118954] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   18.172134] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   18.172139] hda_intel: Disable MSI for Nvidia chipset
[   18.172160] HDA Intel 0000:01:00.1: setting latency timer to 64
[   18.972152] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   18.972159] nvidia 0000:01:00.0: setting latency timer to 64
[   18.972163] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   18.972247] NVRM: loading NVIDIA UNIX x86 Kernel Module  275.19  Tue Jul 12 18:29:18 PDT 2011
[   19.051329] type=1400 audit(1310947664.647:8): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=1099 comm="apparmor_parser"
[   19.052170] type=1400 audit(1310947664.651:9): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1100 comm="apparmor_parser"
[   19.052768] type=1400 audit(1310947664.651:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1100 comm="apparmor_parser"
[   19.052790] type=1400 audit(1310947664.651:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1103 comm="apparmor_parser"
[   19.155392] ppdev: user-space parallel port driver
[   19.450031] <-- RTMPAllocTxRxRingMemory, Status=0
[   19.451868] -->RTUSBVenderReset
[   19.451969] <--RTUSBVenderReset
[   19.735311] 1. Phy Mode = 0
[   19.735316] 2. Phy Mode = 0
[   19.776075] 3. Phy Mode = 0
[   19.781899] RTMPSetPhyMode: channel is out of range, use first channel=1 
[   19.781904] MCS Set = 00 00 00 00 00
[   19.853029] <==== rt28xx_init, Status=0
[   19.854527] 0x1300 = 000a4200
[   20.164257] ---> RTMPFreeTxRxRingMemory
[   20.164273] <--- RTMPFreeTxRxRingMemory
[   20.437035] <-- RTMPAllocTxRxRingMemory, Status=0
[   20.438505] -->RTUSBVenderReset
[   20.438632] <--RTUSBVenderReset
[   20.753695] 1. Phy Mode = 0
[   20.753697] 2. Phy Mode = 0
[   20.794793] 3. Phy Mode = 0
[   20.800669] MCS Set = 00 00 00 00 00
[   20.873434] <==== rt28xx_init, Status=0
[   20.874933] 0x1300 = 000a4200
[   20.876466] r8169 0000:05:00.0: eth0: link down
[   20.876614] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   23.213253] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   26.247690] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 826
[   31.075580] wlan0: no IPv6 routers present
[   31.275411] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 826
[   31.275581] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1)
[   45.593870] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1011
[   86.243584] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 875
[  146.239952] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 826
[  226.239210] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 826
[  302.008324] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 826
[  302.008440] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1)
[  326.226251] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 826
[  446.220274] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 586
[  566.213294] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 870
[  686.204731] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1011
[  806.198650] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 912
[  926.190161] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1011
[ 1046.180752] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1011
[ 1166.174964] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 826
[ 1286.166896] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 826
[ 1406.156386] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 826
[ 1526.151520] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1011
[ 1646.142507] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1011
[ 1766.134784] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1011
[ 1886.128938] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1011
[ 2006.117684] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 691
[ 2126.113126] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1011
[ 2246.105364] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 826
[ 2366.094231] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1011
[ 2486.086470] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 826
[ 2606.080262] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1011
[ 2726.074292] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 826
[ 2846.065950] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1011
[ 2966.055107] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1011
[ 3086.047099] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1011
[ 3206.042718] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1011
[ 3296.957837] show_signal_msg: 30 callbacks suppressed
[ 3296.957840] empathy-account[2485]: segfault at c ip 08092bbd sp bfd51ab0 error 4 in empathy-accounts[8048000+60000]
[ 3326.032396] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 826
[ 3446.024249] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 826
[ 3566.018047] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 826
[ 3686.010280] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 826
[ 3806.002493] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1011
[ 3925.994984] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1011
[ 4045.987742] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 826
[ 4165.978067] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 826
[ 4285.972149] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 826
[ 4405.963860] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1011
[ 4525.956071] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1011
[ 4645.946328] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 826
[ 4765.939947] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1011
[ 4885.930949] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 826
[ 5005.924983] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1011
[ 5125.916735] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 826
[ 5245.909450] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 826
[ 5248.325920] DeQueueRunning[0]= TRUE!
[ 5298.117460] 0:3 LTL=0 , TL=0 L:15084
[ 5300.126085] 0:3 LTL=0 , TL=0 L:22388
[ 5318.220545] 0:3 LTL=0 , TL=0 L:11340
[ 5324.243645] 0:3 LTL=0 , TL=0 L:18308
[ 5325.246877] 0:4 LTL=0 , TL=0 L:18308
[ 5352.378068] 0:3 LTL=0 , TL=0 L:18828
[ 5353.381989] 0:4 LTL=0 , TL=18432 L:18828
[ 5365.901649] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 727
[ 5485.894001] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1011
[ 5604.310043] 0:3 LTL=18432 , TL=0 L:24608
[ 5605.313567] 0:4 LTL=0 , TL=16896 L:24608
[ 5605.885401] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1011
[ 5698.732327] 0:3 LTL=16896 , TL=0 L:15916
[ 5710.802615] 0:3 LTL=0 , TL=0 L:10508
[ 5724.878266] 0:3 LTL=0 , TL=16384 L:24636
[ 5725.877335] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 912
[ 5845.869016] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1011
[ 5965.861052] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1011
[ 6085.853913] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1011
[ 6205.846398] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 826
[ 6325.838799] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1011
[ 6445.830440] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 826
[ 6565.822280] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1011
[ 6685.813491] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 826
[ 6805.807421] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1011
[ 6925.797859] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1011
[ 7045.791081] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1011
[ 7165.783216] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1011
[ 7285.775838] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1011
[ 7405.767924] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1011
[ 7525.759979] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 826
[ 7645.752032] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 826
[ 7765.744332] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 826
[ 7885.735827] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1011
[ 7939.734648] DeQueueRunning[0]= TRUE!
[ 8005.730589] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 826
[ 8125.725841] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 826
[ 8245.715823] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1011
[ 8365.707245] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1011
[ 8485.699404] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1011
[ 8605.689695] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 826
[ 8725.685369] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1011
[ 8845.675852] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 826
[ 8965.668565] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1011
[ 9085.662658] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1011
[ 9205.654667] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1011
[ 9325.646201] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 826
[ 9445.637435] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1011
[ 9565.629804] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1011
[ 9685.621899] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1011
[ 9805.613618] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 826
[ 9925.605843] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 826
[10045.598067] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1011
[10165.590289] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 826
[10285.582510] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 549
[10405.574735] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1011
[10525.566959] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 875
[10645.559184] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1011
[10765.551383] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1011
[10885.543609] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1011
[11005.535831] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 826
[11125.528053] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1011
[11245.520275] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1011
[11365.512520] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1011
[11485.504742] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1011
[11605.497447] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1011
[11725.489669] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 826
[11845.481907] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 876
[11965.474116] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 876
[12085.466338] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 876
[12205.458573] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 691
[12325.450799] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 691
[12445.443003] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 691
[12565.435230] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 691
[12685.427466] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 550
[12805.419673] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 691
[12925.411895] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 826
[13045.404133] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 691
[13165.396360] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 691
[13285.388083] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 691
[13405.380304] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 691
[13525.372530] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 691
[13645.364750] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 691
[13765.356973] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 691
[13885.349196] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 691
[14005.341421] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 691
[14125.333643] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 691
[14245.325866] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 691
[14365.318091] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 691
[14485.310317] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 691
[14605.302789] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 691
[14725.294735] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 691
[14845.286957] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 691
[14965.279957] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 691
```




BTW, i don't think dmesg requires root permission?
so there's an other thing i just found,
i cannot just use ```
dmesg > dmesg.txt
```
even```
 sudo dmesg > dmesg.txt
```
it tells me permission declined,
so I had to "su" first then use dmesg.

but running dmesg is fine,
so i think the home folder is locked, maybe because the the file system locks the folder when it's modifying and since it freezes, it's not unlocked?


what do you refer to by > somethings that I have never seen before

---

### Post by wildmanne39 on 2011-07-18
Hi, what I have never seen is this.
```
*-logicalcpu:0
             description: Logical CPU
             physical id: 2.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 2.2
             width: 64 bits
             capabilities: logical
        *-logicalcpu:2
             description: Logical CPU
             physical id: 2.3
             width: 64 bits
             capabilities: logical
        *-logicalcpu:3
             description: Logical CPU
             physical id: 2.4
             width: 64 bits
             capabilities: logical
        *-logicalcpu:4
             description: Logical CPU
             physical id: 2.5
             width: 64 bits
             capabilities: logical
        *-logicalcpu:5
             description: Logical CPU
             physical id: 2.6
             width: 64 bits
             capabilities: logical
        *-logicalcpu:6
             description: Logical CPU
             physical id: 2.7
             width: 64 bits
             capabilities: logical
        *-logicalcpu:7
             description: Logical CPU
             physical id: 2.8
             width: 64 bits
             capabilities: logical
        *-logicalcpu:8
             description: Logical CPU
             physical id: 2.9
             width: 64 bits
             capabilities: logical
        *-logicalcpu:9
             description: Logical CPU
             physical id: 2.a
             width: 64 bits
             capabilities: logical
        *-logicalcpu:10
             description: Logical CPU
             physical id: 2.b
             width: 64 bits
             capabilities: logical
        *-logicalcpu:11
             description: Logical CPU
             physical id: 2.c
             width: 64 bits
             capabilities: logical
        *-logicalcpu:12
             description: Logical CPU
             physical id: 2.d
             width: 64 bits
             capabilities: logical
        *-logicalcpu:13
             description: Logical CPU
             physical id: 2.e
             width: 64 bits
             capabilities: logical
        *-logicalcpu:14
             description: Logical CPU
             physical id: 2.f
             width: 64 bits
             capabilities: logical
        *-logicalcpu:15
             description: Logical CPU
             physical id: 2.10
             width: 64 bits
             capabilities: logical

```
And this.
```
*-generic:0 UNCLAIMED
             description: System peripheral
             product: Core Processor System Management Registers
             vendor: Intel Corporation
             physical id: 8
             bus info: pci@0000:00:08.0
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: pciexpress cap_list
             configuration: latency=0
        *-generic:1 UNCLAIMED
             description: System peripheral
             product: Core Processor Semaphore and Scratchpad Registers
             vendor: Intel Corporation
             physical id: 8.1
             bus info: pci@0000:00:08.1
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: pciexpress cap_list
             configuration: latency=0
        *-generic:2 UNCLAIMED
             description: System peripheral
             product: Core Processor System Control and Status Registers
             vendor: Intel Corporation
             physical id: 8.2
             bus info: pci@0000:00:08.2
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: pciexpress cap_list
             configuration: latency=0
        *-generic:3 UNCLAIMED
             description: System peripheral
             product: Core Processor Miscellaneous Registers
             vendor: Intel Corporation
             physical id: 8.3
             bus info: pci@0000:00:08.3
             version: 11
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-generic:4 UNCLAIMED
             description: System peripheral
             product: Core Processor QPI Link
             vendor: Intel Corporation
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 11
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-generic:5 UNCLAIMED
             description: System peripheral
             product: Core Processor QPI Routing and Protocol Registers
             vendor: Intel Corporation
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: 11
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
```
That may be because of the system you have.

The only thing that showed an error that I see in the log file is empathy. That may or may not be the problem, I guess you could uninstall it and see.

This dmesg file is from right after you start your system after the freeze correct?

Also hopefully someone else will look and see something that I did not see.

---

### Post by sea52020 on 2011-07-18
> **wildmanne39 said:**
> Hi, what I have never seen is this.
```
*-logicalcpu:0
             description: Logical CPU
             physical id: 2.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 2.2
             width: 64 bits
             capabilities: logical
        *-logicalcpu:2
             description: Logical CPU
             physical id: 2.3
             width: 64 bits
             capabilities: logical
        *-logicalcpu:3
             description: Logical CPU
             physical id: 2.4
             width: 64 bits
             capabilities: logical
        *-logicalcpu:4
             description: Logical CPU
             physical id: 2.5
             width: 64 bits
             capabilities: logical
        *-logicalcpu:5
             description: Logical CPU
             physical id: 2.6
             width: 64 bits
             capabilities: logical
        *-logicalcpu:6
             description: Logical CPU
             physical id: 2.7
             width: 64 bits
             capabilities: logical
        *-logicalcpu:7
             description: Logical CPU
             physical id: 2.8
             width: 64 bits
             capabilities: logical
        *-logicalcpu:8
             description: Logical CPU
             physical id: 2.9
             width: 64 bits
             capabilities: logical
        *-logicalcpu:9
             description: Logical CPU
             physical id: 2.a
             width: 64 bits
             capabilities: logical
        *-logicalcpu:10
             description: Logical CPU
             physical id: 2.b
             width: 64 bits
             capabilities: logical
        *-logicalcpu:11
             description: Logical CPU
             physical id: 2.c
             width: 64 bits
             capabilities: logical
        *-logicalcpu:12
             description: Logical CPU
             physical id: 2.d
             width: 64 bits
             capabilities: logical
        *-logicalcpu:13
             description: Logical CPU
             physical id: 2.e
             width: 64 bits
             capabilities: logical
        *-logicalcpu:14
             description: Logical CPU
             physical id: 2.f
             width: 64 bits
             capabilities: logical
        *-logicalcpu:15
             description: Logical CPU
             physical id: 2.10
             width: 64 bits
             capabilities: logical

```And this.
```
*-generic:0 UNCLAIMED
             description: System peripheral
             product: Core Processor System Management Registers
             vendor: Intel Corporation
             physical id: 8
             bus info: pci@0000:00:08.0
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: pciexpress cap_list
             configuration: latency=0
        *-generic:1 UNCLAIMED
             description: System peripheral
             product: Core Processor Semaphore and Scratchpad Registers
             vendor: Intel Corporation
             physical id: 8.1
             bus info: pci@0000:00:08.1
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: pciexpress cap_list
             configuration: latency=0
        *-generic:2 UNCLAIMED
             description: System peripheral
             product: Core Processor System Control and Status Registers
             vendor: Intel Corporation
             physical id: 8.2
             bus info: pci@0000:00:08.2
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: pciexpress cap_list
             configuration: latency=0
        *-generic:3 UNCLAIMED
             description: System peripheral
             product: Core Processor Miscellaneous Registers
             vendor: Intel Corporation
             physical id: 8.3
             bus info: pci@0000:00:08.3
             version: 11
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-generic:4 UNCLAIMED
             description: System peripheral
             product: Core Processor QPI Link
             vendor: Intel Corporation
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 11
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-generic:5 UNCLAIMED
             description: System peripheral
             product: Core Processor QPI Routing and Protocol Registers
             vendor: Intel Corporation
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: 11
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
```That may be because of the system you have.

The only thing that showed an error that I see in the log file is empathy. That may or may not be the problem, I guess you could uninstall it and see.

This dmesg file is from right after you start your system after the freeze correct?

Also hopefully someone else will look and see something that I did not see.

no, the dmesg file is when it is still freezing.
do you want one after reboot? or killall Xorg?

---

### Post by wildmanne39 on 2011-07-18
Hi, right after the freeze as soon as you get booted back up.

---

### Post by sea52020 on 2011-07-18
> **wildmanne39 said:**
> Hi, right after the freeze as soon as you get booted back up.
I'll get you one as soon as i get back home today,
is there any difference between a killall Xorg so that it recovers the graphic and a reboot?

---

### Post by wildmanne39 on 2011-07-18
> **sea52020 said:**
> I'll get you one as soon as i get back home today,
is there any difference between a killall Xorg so that it recovers the graphic and a reboot?Hi, I do not know I have never tried to kill xorg that way. Also Have a look at the system log as soon as you boot back up.

---

### Post by sea52020 on 2011-07-19
> **wildmanne39 said:**
> Hi, I do not know I have never tried to kill xorg that way. Also Have a look at the system log as soon as you boot back up.
here's the Xorg.0.log file after reboot.


```
[    19.041] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    19.041] X Protocol Version 11, Revision 0
[    19.041] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[    19.041] Current Operating System: Linux acedia-ubuntu 2.6.35-30-generic #54-Ubuntu SMP Tue Jun 7 18:40:23 UTC 2011 i686
[    19.041] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-30-generic root=UUID=56fc7a7f-d6e2-40d2-9e6b-d06b715b7b15 ro quiet splash vt.handoff=7
[    19.041] Build Date: 21 May 2011  11:38:35AM
[    19.041] xorg-server 2:1.10.1-1ubuntu1.1 (For technical support please see http://www.ubuntu.com/support) 
[    19.041] Current version of pixman: 0.20.2
[    19.041]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    19.041] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    19.041] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Jul 19 15:01:04 2011
[    19.041] (==) Using config file: "/etc/X11/xorg.conf"
[    19.041] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    19.041] (==) ServerLayout "Layout0"
[    19.041] (**) |-->Screen "Screen0" (0)
[    19.041] (**) |   |-->Monitor "Monitor0"
[    19.041] (**) |   |-->Device "Device0"
[    19.041] (**) |-->Input Device "Keyboard0"
[    19.041] (**) |-->Input Device "Mouse0"
[    19.041] (==) Automatically adding devices
[    19.041] (==) Automatically enabling devices
[    19.042] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    19.042]     Entry deleted from font path.
[    19.042] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    19.042] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    19.042] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    19.042] (WW) Disabling Keyboard0
[    19.042] (WW) Disabling Mouse0
[    19.042] (II) Loader magic: 0x81ffde0
[    19.042] (II) Module ABI versions:
[    19.042]     X.Org ANSI C Emulation: 0.4
[    19.042]     X.Org Video Driver: 10.0
[    19.042]     X.Org XInput driver : 12.3
[    19.042]     X.Org Server Extension : 5.0
[    19.043] (--) PCI:*(0:1:0:0) 10de:06c4:3842:1467 rev 163, Mem @ 0xf8000000/33554432, 0xd8000000/134217728, 0xd4000000/67108864, I/O @ 0x0000ac00/128, BIOS @ 0x????????/524288
[    19.043] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    19.043] (II) LoadModule: "extmod"
[    19.063] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    19.063] (II) Module extmod: vendor="X.Org Foundation"
[    19.063]     compiled for 1.10.1, module version = 1.0.0
[    19.063]     Module class: X.Org Server Extension
[    19.063]     ABI class: X.Org Server Extension, version 5.0
[    19.063] (II) Loading extension MIT-SCREEN-SAVER
[    19.063] (II) Loading extension XFree86-VidModeExtension
[    19.063] (II) Loading extension XFree86-DGA
[    19.063] (II) Loading extension DPMS
[    19.063] (II) Loading extension XVideo
[    19.063] (II) Loading extension XVideo-MotionCompensation
[    19.063] (II) Loading extension X-Resource
[    19.063] (II) LoadModule: "dbe"
[    19.063] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    19.063] (II) Module dbe: vendor="X.Org Foundation"
[    19.063]     compiled for 1.10.1, module version = 1.0.0
[    19.063]     Module class: X.Org Server Extension
[    19.063]     ABI class: X.Org Server Extension, version 5.0
[    19.063] (II) Loading extension DOUBLE-BUFFER
[    19.063] (II) LoadModule: "glx"
[    19.063] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    19.622] (II) Module glx: vendor="NVIDIA Corporation"
[    19.622]     compiled for 4.0.2, module version = 1.0.0
[    19.622]     Module class: X.Org Server Extension
[    19.622] (II) NVIDIA GLX Module  275.19  Tue Jul 12 18:48:27 PDT 2011
[    19.622] (II) Loading extension GLX
[    19.622] (II) LoadModule: "record"
[    19.622] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    19.622] (II) Module record: vendor="X.Org Foundation"
[    19.622]     compiled for 1.10.1, module version = 1.13.0
[    19.622]     Module class: X.Org Server Extension
[    19.622]     ABI class: X.Org Server Extension, version 5.0
[    19.622] (II) Loading extension RECORD
[    19.622] (II) LoadModule: "dri"
[    19.622] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    19.623] (II) Module dri: vendor="X.Org Foundation"
[    19.623]     compiled for 1.10.1, module version = 1.0.0
[    19.623]     ABI class: X.Org Server Extension, version 5.0
[    19.623] (II) Loading extension XFree86-DRI
[    19.623] (II) LoadModule: "dri2"
[    19.623] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    19.623] (II) Module dri2: vendor="X.Org Foundation"
[    19.623]     compiled for 1.10.1, module version = 1.2.0
[    19.623]     ABI class: X.Org Server Extension, version 5.0
[    19.623] (II) Loading extension DRI2
[    19.623] (II) LoadModule: "nvidia"
[    19.623] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    19.646] (II) Module nvidia: vendor="NVIDIA Corporation"
[    19.646]     compiled for 4.0.2, module version = 1.0.0
[    19.646]     Module class: X.Org Video Driver
[    19.646] (II) NVIDIA dlloader X Driver  275.19  Tue Jul 12 18:30:49 PDT 2011
[    19.655] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    19.655] (++) using VT number 7

[    19.655] (II) Loading sub module "fb"
[    19.655] (II) LoadModule: "fb"
[    19.656] (II) Loading /usr/lib/xorg/modules/libfb.so
[    19.656] (II) Module fb: vendor="X.Org Foundation"
[    19.656]     compiled for 1.10.1, module version = 1.0.0
[    19.656]     ABI class: X.Org ANSI C Emulation, version 0.4
[    19.656] (II) Loading sub module "wfb"
[    19.656] (II) LoadModule: "wfb"
[    19.656] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    19.656] (II) Module wfb: vendor="X.Org Foundation"
[    19.656]     compiled for 1.10.1, module version = 1.0.0
[    19.656]     ABI class: X.Org ANSI C Emulation, version 0.4
[    19.656] (II) Loading sub module "ramdac"
[    19.656] (II) LoadModule: "ramdac"
[    19.656] (II) Module "ramdac" already built-in
[    19.657] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    19.657] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    19.657] (II) Loading /usr/lib/xorg/modules/libfb.so
[    19.661] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    19.661] (==) NVIDIA(0): RGB weight 888
[    19.661] (==) NVIDIA(0): Default visual is TrueColor
[    19.661] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    20.375] (II) NVIDIA(GPU-0): Display (Gateway HX2000 (CRT-0)) does not support NVIDIA 3D
[    20.375] (II) NVIDIA(GPU-0):     Vision stereo.
[    20.376] (II) NVIDIA(0): NVIDIA GPU GeForce GTX 465 (GF100) at PCI:1:0:0 (GPU-0)
[    20.376] (--) NVIDIA(0): Memory: 1048576 kBytes
[    20.376] (--) NVIDIA(0): VideoBIOS: 70.00.21.00.62
[    20.376] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    20.376] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    20.376] (--) NVIDIA(0): Connected display device(s) on GeForce GTX 465 at PCI:1:0:0
[    20.376] (--) NVIDIA(0):     Gateway HX2000 (CRT-0)
[    20.376] (--) NVIDIA(0): Gateway HX2000 (CRT-0): 400.0 MHz maximum pixel clock
[    20.421] (II) NVIDIA(0): Assigned Display Device: CRT-0
[    20.421] (==) NVIDIA(0): 
[    20.421] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    20.421] (==) NVIDIA(0):     will be used as the requested mode.
[    20.421] (==) NVIDIA(0): 
[    20.421] (II) NVIDIA(0): Validated modes:
[    20.421] (II) NVIDIA(0):     "nvidia-auto-select"
[    20.421] (II) NVIDIA(0): Virtual screen size determined to be 1600 x 900
[    20.455] (--) NVIDIA(0): DPI set to (92, 91); computed from "UseEdidDpi" X config
[    20.455] (--) NVIDIA(0):     option
[    20.455] (--) Depth 24 pixmap format is 32 bpp
[    20.455] (II) NVIDIA: Using 1024.00 MB of virtual memory for indirect memory
[    20.456] (II) NVIDIA:     access.
[    20.463] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[    20.541] (II) Loading extension NV-GLX
[    20.593] (==) NVIDIA(0): Disabling shared memory pixmaps
[    20.593] (==) NVIDIA(0): Backing store disabled
[    20.593] (==) NVIDIA(0): Silken mouse enabled
[    20.594] (**) NVIDIA(0): DPMS enabled
[    20.594] (II) Loading extension NV-CONTROL
[    20.594] (II) Loading extension XINERAMA
[    20.594] (II) Loading sub module "dri2"
[    20.594] (II) LoadModule: "dri2"
[    20.594] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    20.594] (II) Module dri2: vendor="X.Org Foundation"
[    20.594]     compiled for 1.10.1, module version = 1.2.0
[    20.594]     ABI class: X.Org Server Extension, version 5.0
[    20.595] (II) NVIDIA(0): [DRI2] Setup complete
[    20.595] (==) RandR enabled
[    20.595] (II) Initializing built-in extension Generic Event Extension
[    20.595] (II) Initializing built-in extension SHAPE
[    20.595] (II) Initializing built-in extension MIT-SHM
[    20.595] (II) Initializing built-in extension XInputExtension
[    20.595] (II) Initializing built-in extension XTEST
[    20.595] (II) Initializing built-in extension BIG-REQUESTS
[    20.595] (II) Initializing built-in extension SYNC
[    20.595] (II) Initializing built-in extension XKEYBOARD
[    20.595] (II) Initializing built-in extension XC-MISC
[    20.595] (II) Initializing built-in extension SECURITY
[    20.595] (II) Initializing built-in extension XINERAMA
[    20.595] (II) Initializing built-in extension XFIXES
[    20.595] (II) Initializing built-in extension RENDER
[    20.595] (II) Initializing built-in extension RANDR
[    20.595] (II) Initializing built-in extension COMPOSITE
[    20.595] (II) Initializing built-in extension DAMAGE
[    20.595] (II) Initializing built-in extension GESTURE
[    20.597] (II) Initializing extension GLX
[    20.625] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    20.633] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    20.633] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    20.633] (II) LoadModule: "evdev"
[    20.633] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    20.633] (II) Module evdev: vendor="X.Org Foundation"
[    20.633]     compiled for 1.10.0.902, module version = 2.6.0
[    20.633]     Module class: X.Org XInput Driver
[    20.633]     ABI class: X.Org XInput driver, version 12.3
[    20.633] (II) Using input driver 'evdev' for 'Power Button'
[    20.633] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    20.633] (**) Power Button: always reports core events
[    20.633] (**) Power Button: Device: "/dev/input/event1"
[    20.660] (--) Power Button: Found keys
[    20.660] (II) Power Button: Configuring as keyboard
[    20.660] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    20.660] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    20.660] (**) Option "xkb_rules" "evdev"
[    20.660] (**) Option "xkb_model" "pc105"
[    20.660] (**) Option "xkb_layout" "us"
[    20.663] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    20.663] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    20.663] (II) Using input driver 'evdev' for 'Power Button'
[    20.663] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    20.663] (**) Power Button: always reports core events
[    20.663] (**) Power Button: Device: "/dev/input/event0"
[    20.692] (--) Power Button: Found keys
[    20.692] (II) Power Button: Configuring as keyboard
[    20.692] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    20.692] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    20.692] (**) Option "xkb_rules" "evdev"
[    20.692] (**) Option "xkb_model" "pc105"
[    20.692] (**) Option "xkb_layout" "us"
[    20.696] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event2)
[    20.696] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    20.696] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[    20.696] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    20.696] (**) Logitech USB Receiver: always reports core events
[    20.696] (**) Logitech USB Receiver: Device: "/dev/input/event2"
[    20.724] (--) Logitech USB Receiver: Found keys
[    20.724] (II) Logitech USB Receiver: Configuring as keyboard
[    20.724] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.0/input/input2/event2"
[    20.724] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[    20.724] (**) Option "xkb_rules" "evdev"
[    20.724] (**) Option "xkb_model" "pc105"
[    20.724] (**) Option "xkb_layout" "us"
[    20.725] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event3)
[    20.725] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[    20.725] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    20.725] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[    20.725] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    20.725] (**) Logitech USB Receiver: always reports core events
[    20.725] (**) Logitech USB Receiver: Device: "/dev/input/event3"
[    20.740] (--) Logitech USB Receiver: Found 12 mouse buttons
[    20.740] (--) Logitech USB Receiver: Found scroll wheel(s)
[    20.740] (--) Logitech USB Receiver: Found relative axes
[    20.740] (--) Logitech USB Receiver: Found x and y relative axes
[    20.740] (--) Logitech USB Receiver: Found absolute axes
[    20.740] (II) evdev-grail: failed to open grail, no gesture support
[    20.740] (--) Logitech USB Receiver: Found keys
[    20.740] (II) Logitech USB Receiver: Configuring as mouse
[    20.740] (II) Logitech USB Receiver: Configuring as keyboard
[    20.740] (II) Logitech USB Receiver: Adding scrollwheel support
[    20.740] (**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[    20.740] (**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    20.740] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.1/input/input3/event3"
[    20.740] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[    20.740] (**) Option "xkb_rules" "evdev"
[    20.740] (**) Option "xkb_model" "pc105"
[    20.740] (**) Option "xkb_layout" "us"
[    20.740] (II) Logitech USB Receiver: initialized for relative axes.
[    20.740] (WW) Logitech USB Receiver: ignoring absolute axes.
[    20.740] (**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
[    20.740] (**) Logitech USB Receiver: (accel) acceleration profile 0
[    20.740] (**) Logitech USB Receiver: (accel) acceleration factor: 2.000
[    20.740] (**) Logitech USB Receiver: (accel) acceleration threshold: 4
[    20.740] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse0)
[    20.740] (II) No input driver/identifier specified (ignoring)

```

and dmesg
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.35-30-generic (buildd@rothera) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #54-Ubuntu SMP Tue Jun 7 18:40:23 UTC 2011 (Ubuntu 2.6.35-30.54-generic 2.6.35.13)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bf770000 (usable)
[    0.000000]  BIOS-e820: 00000000bf770000 - 00000000bf788000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bf788000 - 00000000bf7dc000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bf7dc000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000240000000 (usable)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI 2.6 present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0xbf770 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-D3FFF write-protect
[    0.000000]   D4000-DFFFF uncachable
[    0.000000]   E0000-E7FFF write-through
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask E00000000 write-back
[    0.000000]   1 base 200000000 mask FC0000000 write-back
[    0.000000]   2 base 0C0000000 mask FC0000000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000c0000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000bf770000 (usable)
[    0.000000]  modified: 00000000bf770000 - 00000000bf788000 (ACPI data)
[    0.000000]  modified: 00000000bf788000 - 00000000bf7dc000 (ACPI NVS)
[    0.000000]  modified: 00000000bf7dc000 - 00000000c0000000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000240000000 (usable)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 15000-1a000
[    0.000000] RAMDISK: 3686e000 - 3742f000
[    0.000000] ACPI: RSDP 000fbb00 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT bf770000 00048 (v01 032510 RSDT2140 20100325 MSFT 00000097)
[    0.000000] ACPI: FACP bf770200 00084 (v01 032510 FACP2140 20100325 MSFT 00000097)
[    0.000000] ACPI: DSDT bf7704a0 0EDBE (v01  A1513 A1513003 00000003 INTL 20060113)
[    0.000000] ACPI: FACS bf788000 00040
[    0.000000] ACPI: APIC bf770390 000CC (v01 032510 APIC2140 20100325 MSFT 00000097)
[    0.000000] ACPI: MCFG bf770460 0003C (v01 032510 OEMMCFG  20100325 MSFT 00000097)
[    0.000000] ACPI: OEMB bf788040 00072 (v01 032510 OEMB2140 20100325 MSFT 00000097)
[    0.000000] ACPI: HPET bf77f7a0 00038 (v01 032510 OEMHPET  20100325 MSFT 00000097)
[    0.000000] ACPI: DMAR bf7880c0 00090 (v01    AMI  OEMDMAR 00000001 MSFT 00000097)
[    0.000000] ACPI: ASPT bf77fa40 00034 (v06 032510 PerfTune 20100325 MSFT 00000097)
[    0.000000] ACPI: OSFR bf77fa80 000B0 (v01 032510 OEMOSFR  20100325 MSFT 00000097)
[    0.000000] ACPI: SSDT bf789070 00363 (v01 DpgPmm    CpuPm 00000012 INTL 20060113)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 2175MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x000bf770
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000bf770
[    0.000000] On node 0 totalpages: 784127
[    0.000000] free_area_init_node: node 0, pgdat c0802000, node_mem_map c1001200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 4351 pages used for memmap
[    0.000000]   HighMem zone: 552563 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x84] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x85] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x86] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x87] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x09] lapic_id[0x88] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0a] lapic_id[0x89] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0b] lapic_id[0x8a] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0c] lapic_id[0x8b] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0d] lapic_id[0x8c] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0e] lapic_id[0x8d] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0f] lapic_id[0x8e] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x10] lapic_id[0x8f] disabled)
[    0.000000] ACPI: IOAPIC (id[0x07] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 7, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] 16 Processors exceeds NR_CPUS limit of 8
[    0.000000] SMP: Allowing 8 CPUs, 4 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] early_res array is doubled to 64 at [16000 - 167ff]
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:3ee00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c2c00000 s36416 r0 d20928 u524288
[    0.000000] pcpu-alloc: s36416 r0 d20928 u524288 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 778000
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-30-generic root=UUID=56fc7a7f-d6e2-40d2-9e6b-d06b715b7b15 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 15684480 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Subtract (55 early reservations)
[    0.000000]   #1 [0000001000 - 0000002000]   EX TRAMPOLINE
[    0.000000]   #2 [0000100000 - 00009a4adc]   TEXT DATA BSS
[    0.000000]   #3 [003686e000 - 003742f000]         RAMDISK
[    0.000000]   #4 [00009a5000 - 00009a824c]             BRK
[    0.000000]   #5 [00000ff790 - 0000100000]   BIOS reserved
[    0.000000]   #6 [00000ff780 - 00000ff790]    MP-table mpf
[    0.000000]   #7 [000009fc00 - 00000f1310]   BIOS reserved
[    0.000000]   #8 [00000f1514 - 00000ff780]   BIOS reserved
[    0.000000]   #9 [00000f1310 - 00000f1514]    MP-table mpc
[    0.000000]   #10 [0000010000 - 0000011000]      TRAMPOLINE
[    0.000000]   #11 [0000011000 - 0000015000]     ACPI WAKEUP
[    0.000000]   #12 [0000015000 - 0000016000]         PGTABLE
[    0.000000]   #13 [0001000000 - 0001001000]         BOOTMEM
[    0.000000]   #14 [0001001000 - 00027f1000]         BOOTMEM
[    0.000000]   #15 [00027f1000 - 00027f1004]         BOOTMEM
[    0.000000]   #16 [00027f1040 - 00027f1100]         BOOTMEM
[    0.000000]   #17 [00027f1100 - 00027f1154]         BOOTMEM
[    0.000000]   #18 [00027f1180 - 00027f4180]         BOOTMEM
[    0.000000]   #19 [00027f4180 - 00027f424c]         BOOTMEM
[    0.000000]   #20 [00027f4280 - 0002800280]         BOOTMEM
[    0.000000]   #21 [0002800280 - 00028002a5]         BOOTMEM
[    0.000000]   #22 [00028002c0 - 00028002e7]         BOOTMEM
[    0.000000]   #23 [0002800300 - 0002800434]         BOOTMEM
[    0.000000]   #24 [0002800440 - 0002800480]         BOOTMEM
[    0.000000]   #25 [0002800480 - 00028004c0]         BOOTMEM
[    0.000000]   #26 [00028004c0 - 0002800500]         BOOTMEM
[    0.000000]   #27 [0002800500 - 0002800540]         BOOTMEM
[    0.000000]   #28 [0002800540 - 0002800580]         BOOTMEM
[    0.000000]   #29 [0002800580 - 00028005c0]         BOOTMEM
[    0.000000]   #30 [00028005c0 - 0002800600]         BOOTMEM
[    0.000000]   #31 [0002800600 - 0002800640]         BOOTMEM
[    0.000000]   #32 [0002800640 - 0002800680]         BOOTMEM
[    0.000000]   #33 [0002800680 - 00028006c0]         BOOTMEM
[    0.000000]   #34 [00028006c0 - 00028006d0]         BOOTMEM
[    0.000000]   #35 [0002800700 - 0002800777]         BOOTMEM
[    0.000000]   #36 [0002800780 - 00028007f7]         BOOTMEM
[    0.000000]   #37 [0002c00000 - 0002c0e000]         BOOTMEM
[    0.000000]   #38 [0002c80000 - 0002c8e000]         BOOTMEM
[    0.000000]   #39 [0002d00000 - 0002d0e000]         BOOTMEM
[    0.000000]   #40 [0002d80000 - 0002d8e000]         BOOTMEM
[    0.000000]   #41 [0002e00000 - 0002e0e000]         BOOTMEM
[    0.000000]   #42 [0002e80000 - 0002e8e000]         BOOTMEM
[    0.000000]   #43 [0002f00000 - 0002f0e000]         BOOTMEM
[    0.000000]   #44 [0002f80000 - 0002f8e000]         BOOTMEM
[    0.000000]   #45 [0002802800 - 0002802804]         BOOTMEM
[    0.000000]   #46 [0002802840 - 0002802844]         BOOTMEM
[    0.000000]   #47 [0002802880 - 00028028a0]         BOOTMEM
[    0.000000]   #48 [00028028c0 - 00028028e0]         BOOTMEM
[    0.000000]   #49 [0002802900 - 0002802998]         BOOTMEM
[    0.000000]   #50 [00028029c0 - 00028029f8]         BOOTMEM
[    0.000000]   #51 [0002802a00 - 0002806a00]         BOOTMEM
[    0.000000]   #52 [0002806a00 - 0002886a00]         BOOTMEM
[    0.000000]   #53 [0002886a00 - 00028c6a00]         BOOTMEM
[    0.000000]   #54 [0002f8e000 - 0003e83380]         BOOTMEM
[    0.000000] Initializing HighMem for node 0 (000377fe:000bf770)
[    0.000000] Memory: 3074444k/3136960k available (4941k kernel code, 62064k reserved, 2332k data, 688k init, 2227656k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc081b000 - 0xc08c7000   ( 688 kB)
[    0.000000]       .data : 0xc05d344e - 0xc081a7e8   (2332 kB)
[    0.000000]       .text : 0xc0100000 - 0xc05d344e   (4941 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU-based detection of stalled CPUs is disabled.
[    0.000000]     Verbose stalled-CPUs detection is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:744
[    0.000000] vt handoff: transparent VT on 7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.004000] Detected 2541.486 MHz processor.
[    0.000003] Calibrating delay loop (skipped), value calculated using timer frequency.. 5082.97 BogoMIPS (lpj=10165944)
[    0.000006] pid_max: default: 32768 minimum: 301
[    0.000020] Security Framework initialized
[    0.000031] AppArmor: AppArmor initialized
[    0.000032] Yama: becoming mindful.
[    0.000070] Mount-cache hash table entries: 512
[    0.000157] Initializing cgroup subsys ns
[    0.000159] Initializing cgroup subsys cpuacct
[    0.000163] Initializing cgroup subsys memory
[    0.000169] Initializing cgroup subsys devices
[    0.000171] Initializing cgroup subsys freezer
[    0.000172] Initializing cgroup subsys net_cls
[    0.000189] CPU: Physical Processor ID: 0
[    0.000191] CPU: Processor Core ID: 0
[    0.000194] mce: CPU supports 9 MCE banks
[    0.000203] CPU0: Thermal monitoring enabled (TM1)
[    0.000209] using mwait in idle threads.
[    0.000212] Performance Events: PEBS fmt1+, Nehalem events, Intel PMU driver.
[    0.000219] ... version:                3
[    0.000220] ... bit width:              48
[    0.000221] ... generic registers:      4
[    0.000222] ... value mask:             0000ffffffffffff
[    0.000224] ... max period:             000000007fffffff
[    0.000225] ... fixed-purpose events:   3
[    0.000226] ... event mask:             000000070000000f
[    0.002285] ACPI: Core revision 20100428
[    0.147569] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.147572] ftrace: allocating 21775 entries in 43 pages
[    0.153437] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.153764] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.193358] CPU0: Intel(R) Core(TM) i5 CPU         750  @ 2.67GHz stepping 05
[    0.299963] Booting Node   0, Processors  #1
[    0.310373] Initializing CPU#1
[    0.407788]  #2
[    0.418043] Initializing CPU#2
[    0.515506]  #3
[    0.525760] Initializing CPU#3
[    0.623179] Brought up 4 CPUs
[    0.623181] Total of 4 processors activated (20329.44 BogoMIPS).
[    0.625089] devtmpfs: initialized
[    0.626054] regulator: core version 0.5
[    0.626077] Time: 15:00:45  Date: 07/19/11
[    0.626105] NET: Registered protocol family 16
[    0.626172] Trying to unpack rootfs image as initramfs...
[    0.626179] EISA bus registered
[    0.626185] ACPI: bus type pci registered
[    0.626235] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.626238] PCI: not using MMCONFIG
[    0.626321] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=12
[    0.626322] PCI: Using configuration type 1 for base access
[    0.626973] bio: create slab <bio-0> at 0
[    0.628669] ACPI: EC: Look up EC in DSDT
[    0.630351] ACPI: Executed 1 blocks of module-level executable AML code
[    0.644595] ACPI: SSDT bf788150 00F20 (v01 DpgPmm  P001Ist 00000011 INTL 20060113)
[    0.645076] ACPI: Dynamic OEM Table Load:
[    0.645078] ACPI: SSDT (null) 00F20 (v01 DpgPmm  P001Ist 00000011 INTL 20060113)
[    0.645634] ACPI: Interpreter enabled
[    0.645639] ACPI: (supports S0 S1 S3 S4 S5)
[    0.645658] ACPI: Using IOAPIC for interrupt routing
[    0.645705] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.647870] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.647872] PCI: Using MMCONFIG for extended config space
[    0.657435] ACPI: EC: GPE = 0x18, I/O: command/status = 0x66, data = 0x62
[    0.657637] ACPI: No dock devices found.
[    0.657639] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.657932] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.658194] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.658197] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.658199] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.658201] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000dffff]
[    0.658203] pci_root PNP0A08:00: host bridge window [mem 0xc0000000-0xdfffffff]
[    0.658205] pci_root PNP0A08:00: host bridge window [mem 0xf0000000-0xfed8ffff]
[    0.658287] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
[    0.658290] pci 0000:00:03.0: PME# disabled
[    0.658528] pci 0000:00:1a.0: reg 10: [mem 0xf7ffe000-0xf7ffe3ff]
[    0.658579] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.658582] pci 0000:00:1a.0: PME# disabled
[    0.658613] pci 0000:00:1b.0: reg 10: [mem 0xf7ff8000-0xf7ffbfff 64bit]
[    0.658650] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.658654] pci 0000:00:1b.0: PME# disabled
[    0.658712] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.658715] pci 0000:00:1c.0: PME# disabled
[    0.658776] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.658779] pci 0000:00:1c.4: PME# disabled
[    0.658839] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.658842] pci 0000:00:1c.5: PME# disabled
[    0.658901] pci 0000:00:1c.6: PME# supported from D0 D3hot D3cold
[    0.658904] pci 0000:00:1c.6: PME# disabled
[    0.658964] pci 0000:00:1c.7: PME# supported from D0 D3hot D3cold
[    0.658967] pci 0000:00:1c.7: PME# disabled
[    0.659009] pci 0000:00:1d.0: reg 10: [mem 0xf7ffd000-0xf7ffd3ff]
[    0.659059] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.659063] pci 0000:00:1d.0: PME# disabled
[    0.659208] pci 0000:00:1f.2: reg 10: [io  0x8c00-0x8c07]
[    0.659213] pci 0000:00:1f.2: reg 14: [io  0x8880-0x8883]
[    0.659218] pci 0000:00:1f.2: reg 18: [io  0x8800-0x8807]
[    0.659223] pci 0000:00:1f.2: reg 1c: [io  0x8480-0x8483]
[    0.659228] pci 0000:00:1f.2: reg 20: [io  0x8400-0x840f]
[    0.659233] pci 0000:00:1f.2: reg 24: [io  0x8080-0x808f]
[    0.659273] pci 0000:00:1f.3: reg 10: [mem 0xf7ffc000-0xf7ffc0ff 64bit]
[    0.659285] pci 0000:00:1f.3: reg 20: [io  0xffe0-0xffff]
[    0.659319] pci 0000:00:1f.5: reg 10: [io  0x9c00-0x9c07]
[    0.659324] pci 0000:00:1f.5: reg 14: [io  0x9880-0x9883]
[    0.659329] pci 0000:00:1f.5: reg 18: [io  0x9800-0x9807]
[    0.659333] pci 0000:00:1f.5: reg 1c: [io  0x9480-0x9483]
[    0.659338] pci 0000:00:1f.5: reg 20: [io  0x9400-0x940f]
[    0.659343] pci 0000:00:1f.5: reg 24: [io  0x9080-0x908f]
[    0.659412] pci 0000:01:00.0: reg 10: [mem 0xf8000000-0xf9ffffff]
[    0.659420] pci 0000:01:00.0: reg 14: [mem 0xd8000000-0xdfffffff 64bit pref]
[    0.659428] pci 0000:01:00.0: reg 1c: [mem 0xd4000000-0xd7ffffff 64bit pref]
[    0.659433] pci 0000:01:00.0: reg 24: [io  0xac00-0xac7f]
[    0.659438] pci 0000:01:00.0: reg 30: [mem 0xfb800000-0xfb87ffff pref]
[    0.659484] pci 0000:01:00.1: reg 10: [mem 0xfb8fc000-0xfb8fffff]
[    0.667000] pci 0000:00:03.0: PCI bridge to [bus 01-01]
[    0.667003] pci 0000:00:03.0:   bridge window [io  0xa000-0xafff]
[    0.667006] pci 0000:00:03.0:   bridge window [mem 0xf8000000-0xfb8fffff]
[    0.667011] pci 0000:00:03.0:   bridge window [mem 0xd4000000-0xdfffffff 64bit pref]
[    0.667071] pci 0000:06:00.0: reg 10: [mem 0xfbbe0000-0xfbbfffff]
[    0.667124] pci 0000:06:00.0: PME# supported from D0 D3hot D3cold
[    0.667128] pci 0000:06:00.0: PME# disabled
[    0.674976] pci 0000:00:1c.0: PCI bridge to [bus 06-0b]
[    0.674979] pci 0000:00:1c.0:   bridge window [io  0xd000-0xdfff]
[    0.674983] pci 0000:00:1c.0:   bridge window [mem 0xfbb00000-0xfbdfffff]
[    0.674988] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.675120] pci 0000:07:01.0: PME# supported from D0 D3hot D3cold
[    0.675124] pci 0000:07:01.0: PME# disabled
[    0.675223] pci 0000:07:05.0: PME# supported from D0 D3hot D3cold
[    0.675227] pci 0000:07:05.0: PME# disabled
[    0.675324] pci 0000:07:07.0: PME# supported from D0 D3hot D3cold
[    0.675328] pci 0000:07:07.0: PME# disabled
[    0.675427] pci 0000:07:09.0: PME# supported from D0 D3hot D3cold
[    0.675431] pci 0000:07:09.0: PME# disabled
[    0.675482] pci 0000:06:00.0: PCI bridge to [bus 07-0b]
[    0.675488] pci 0000:06:00.0:   bridge window [io  0xd000-0xdfff]
[    0.675492] pci 0000:06:00.0:   bridge window [mem 0xfbc00000-0xfbdfffff]
[    0.675499] pci 0000:06:00.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.675597] pci 0000:08:00.0: reg 10: [mem 0xfbcfe000-0xfbcfffff 64bit]
[    0.675676] pci 0000:08:00.0: PME# supported from D0 D3hot D3cold
[    0.675681] pci 0000:08:00.0: PME# disabled
[    0.682960] pci 0000:07:01.0: PCI bridge to [bus 08-08]
[    0.682967] pci 0000:07:01.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.682971] pci 0000:07:01.0:   bridge window [mem 0xfbc00000-0xfbcfffff]
[    0.682978] pci 0000:07:01.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.683063] pci 0000:09:00.0: reg 10: [io  0xdc00-0xdc07]
[    0.683070] pci 0000:09:00.0: reg 14: [io  0xd880-0xd883]
[    0.683078] pci 0000:09:00.0: reg 18: [io  0xd800-0xd807]
[    0.683086] pci 0000:09:00.0: reg 1c: [io  0xd480-0xd483]
[    0.683093] pci 0000:09:00.0: reg 20: [io  0xd400-0xd40f]
[    0.683101] pci 0000:09:00.0: reg 24: [mem 0xfbdff000-0xfbdff7ff]
[    0.683109] pci 0000:09:00.0: reg 30: [mem 0xfbde0000-0xfbdeffff pref]
[    0.683144] pci 0000:09:00.0: PME# supported from D3hot
[    0.683149] pci 0000:09:00.0: PME# disabled
[    0.690939] pci 0000:07:05.0: PCI bridge to [bus 09-09]
[    0.690946] pci 0000:07:05.0:   bridge window [io  0xd000-0xdfff]
[    0.690950] pci 0000:07:05.0:   bridge window [mem 0xfbd00000-0xfbdfffff]
[    0.690957] pci 0000:07:05.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.691014] pci 0000:07:07.0: PCI bridge to [bus 0a-0a]
[    0.691021] pci 0000:07:07.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.691025] pci 0000:07:07.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.691032] pci 0000:07:07.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.691089] pci 0000:07:09.0: PCI bridge to [bus 0b-0b]
[    0.691096] pci 0000:07:09.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.691100] pci 0000:07:09.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.691107] pci 0000:07:09.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.691197] pci 0000:05:00.0: reg 10: [io  0xc800-0xc8ff]
[    0.691216] pci 0000:05:00.0: reg 18: [mem 0xf6fff000-0xf6ffffff 64bit pref]
[    0.691230] pci 0000:05:00.0: reg 20: [mem 0xf6ff8000-0xf6ffbfff 64bit pref]
[    0.691237] pci 0000:05:00.0: reg 30: [mem 0xfbaf0000-0xfbafffff pref]
[    0.691275] pci 0000:05:00.0: supports D1 D2
[    0.691277] pci 0000:05:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.691281] pci 0000:05:00.0: PME# disabled
[    0.698920] pci 0000:00:1c.4: PCI bridge to [bus 05-05]
[    0.698924] pci 0000:00:1c.4:   bridge window [io  0xc000-0xcfff]
[    0.698927] pci 0000:00:1c.4:   bridge window [mem 0xfba00000-0xfbafffff]
[    0.698932] pci 0000:00:1c.4:   bridge window [mem 0xf6f00000-0xf6ffffff 64bit pref]
[    0.698971] pci 0000:00:1c.5: PCI bridge to [bus 04-04]
[    0.698975] pci 0000:00:1c.5:   bridge window [io  0xf000-0x0000] (disabled)
[    0.698978] pci 0000:00:1c.5:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.698983] pci 0000:00:1c.5:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.699090] pci 0000:03:00.0: reg 24: [mem 0xfb9fe000-0xfb9fffff]
[    0.699128] pci 0000:03:00.0: PME# supported from D3hot
[    0.699132] pci 0000:03:00.0: PME# disabled
[    0.699177] pci 0000:03:00.1: reg 10: [io  0xbc00-0xbc07]
[    0.699185] pci 0000:03:00.1: reg 14: [io  0xb880-0xb883]
[    0.699193] pci 0000:03:00.1: reg 18: [io  0xb800-0xb807]
[    0.699202] pci 0000:03:00.1: reg 1c: [io  0xb480-0xb483]
[    0.699210] pci 0000:03:00.1: reg 20: [io  0xb400-0xb40f]
[    0.699268] pci 0000:03:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.699281] pci 0000:00:1c.6: PCI bridge to [bus 03-03]
[    0.699284] pci 0000:00:1c.6:   bridge window [io  0xb000-0xbfff]
[    0.699288] pci 0000:00:1c.6:   bridge window [mem 0xfb900000-0xfb9fffff]
[    0.699293] pci 0000:00:1c.6:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.699329] pci 0000:00:1c.7: PCI bridge to [bus 02-02]
[    0.699333] pci 0000:00:1c.7:   bridge window [io  0xf000-0x0000] (disabled)
[    0.699336] pci 0000:00:1c.7:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.699342] pci 0000:00:1c.7:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.699385] pci 0000:0c:03.0: reg 10: [mem 0xfbeff000-0xfbeff7ff]
[    0.699392] pci 0000:0c:03.0: reg 14: [io  0xec00-0xec7f]
[    0.699432] pci 0000:0c:03.0: supports D2
[    0.699434] pci 0000:0c:03.0: PME# supported from D2 D3hot D3cold
[    0.699438] pci 0000:0c:03.0: PME# disabled
[    0.699476] pci 0000:00:1e.0: PCI bridge to [bus 0c-0c] (subtractive decode)
[    0.699479] pci 0000:00:1e.0:   bridge window [io  0xe000-0xefff]
[    0.699483] pci 0000:00:1e.0:   bridge window [mem 0xfbe00000-0xfbefffff]
[    0.699488] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.699490] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.699492] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.699494] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.699496] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.699498] pci 0000:00:1e.0:   bridge window [mem 0xc0000000-0xdfffffff] (subtractive decode)
[    0.699500] pci 0000:00:1e.0:   bridge window [mem 0xf0000000-0xfed8ffff] (subtractive decode)
[    0.699526] pci_bus 0000:00: on NUMA node 0
[    0.699534] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.699753] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR1E._PRT]
[    0.699880] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[    0.699947] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR20._PRT]
[    0.700045] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR24._PRT]
[    0.700106] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR26._PRT]
[    0.700177] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR27._PRT]
[    0.723338] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12 14 15)
[    0.723454] ACPI: PCI Interrupt Link [LNKB] (IRQs *5)
[    0.723566] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 11 12 14 *15)
[    0.723680] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 *11 12 14 15)
[    0.723794] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12 14 15) *0, disabled.
[    0.723908] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12 *14 15)
[    0.724023] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 6 7 10 11 12 14 15)
[    0.724137] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 6 *7 10 11 12 14 15)
[    0.724184] HEST: Table is not found!
[    0.724239] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.724245] vgaarb: loaded
[    0.724354] SCSI subsystem initialized
[    0.724433] libata version 3.00 loaded.
[    0.724466] usbcore: registered new interface driver usbfs
[    0.724474] usbcore: registered new interface driver hub
[    0.724491] usbcore: registered new device driver usb
[    0.724604] ACPI: WMI: Mapper loaded
[    0.724606] PCI: Using ACPI for IRQ routing
[    0.724609] PCI: pci_cache_line_size set to 64 bytes
[    0.724712] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    0.724714] reserve RAM buffer: 00000000bf770000 - 00000000bfffffff 
[    0.724776] NetLabel: Initializing
[    0.724778] NetLabel:  domain hash size = 128
[    0.724779] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.724787] NetLabel:  unlabeled traffic allowed by default
[    0.724810]   alloc irq_desc for 40 on node -1
[    0.724812]   alloc kstat_irqs on node -1
[    0.724817]   alloc irq_desc for 41 on node -1
[    0.724818]   alloc kstat_irqs on node -1
[    0.724821]   alloc irq_desc for 42 on node -1
[    0.724823]   alloc kstat_irqs on node -1
[    0.724826]   alloc irq_desc for 43 on node -1
[    0.724827]   alloc kstat_irqs on node -1
[    0.724830]   alloc irq_desc for 44 on node -1
[    0.724831]   alloc kstat_irqs on node -1
[    0.724834] HPET: 8 timers in total, 5 timers will be used for per-cpu timer
[    0.724841] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 40, 41, 42, 43, 44, 0
[    0.724846] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.730845] hpet: hpet2 irq 40 for MSI
[    0.730970] hpet: hpet3 irq 41 for MSI
[    0.735207] hpet: hpet4 irq 42 for MSI
[    0.738919] hpet: hpet5 irq 43 for MSI
[    0.738942] Switching to clocksource tsc
[    0.746072] AppArmor: AppArmor Filesystem Enabled
[    0.746081] pnp: PnP ACPI init
[    0.746090] ACPI: bus type pnp registered
[    0.748488] pnp: PnP ACPI: found 14 devices
[    0.748490] ACPI: ACPI bus type pnp unregistered
[    0.748492] PnPBIOS: Disabled by ACPI PNP
[    0.748501] system 00:01: [mem 0xfc000000-0xfcffffff] has been reserved
[    0.748503] system 00:01: [mem 0xfd000000-0xfdffffff] has been reserved
[    0.748505] system 00:01: [mem 0xfe000000-0xfebfffff] has been reserved
[    0.748507] system 00:01: [mem 0xfed14000-0xfed19fff] has been reserved
[    0.748512] system 00:06: [io  0x0290-0x029f] has been reserved
[    0.748516] system 00:07: [io  0x04d0-0x04d1] has been reserved
[    0.748518] system 00:07: [io  0x0800-0x087f] has been reserved
[    0.748520] system 00:07: [io  0x0500-0x057f] has been reserved
[    0.748522] system 00:07: [io  0x0600-0x0607] has been reserved
[    0.748525] system 00:07: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.748527] system 00:07: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.748529] system 00:07: [mem 0xfed40000-0xfed8ffff] has been reserved
[    0.748533] system 00:0a: [mem 0xffc00000-0xffdfffff] has been reserved
[    0.748537] system 00:0b: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.748539] system 00:0b: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.748543] system 00:0c: [mem 0xe0000000-0xefffffff] has been reserved
[    0.748548] system 00:0d: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.748551] system 00:0d: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.748553] system 00:0d: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.748555] system 00:0d: [mem 0x00100000-0xbfffffff] could not be reserved
[    0.748557] system 00:0d: [mem 0xfed90000-0xffffffff] could not be reserved
[    0.784025] pci 0000:00:1c.7: BAR 14: assigned [mem 0xc0000000-0xc01fffff]
[    0.784028] pci 0000:00:1c.7: BAR 15: assigned [mem 0xc0200000-0xc03fffff 64bit pref]
[    0.784031] pci 0000:00:1c.7: BAR 13: assigned [io  0x1000-0x1fff]
[    0.784033] pci 0000:00:03.0: PCI bridge to [bus 01-01]
[    0.784035] pci 0000:00:03.0:   bridge window [io  0xa000-0xafff]
[    0.784039] pci 0000:00:03.0:   bridge window [mem 0xf8000000-0xfb8fffff]
[    0.784042] pci 0000:00:03.0:   bridge window [mem 0xd4000000-0xdfffffff 64bit pref]
[    0.784047] pci 0000:07:01.0: PCI bridge to [bus 08-08]
[    0.784048] pci 0000:07:01.0:   bridge window [io  disabled]
[    0.784053] pci 0000:07:01.0:   bridge window [mem 0xfbc00000-0xfbcfffff]
[    0.784057] pci 0000:07:01.0:   bridge window [mem pref disabled]
[    0.784064] pci 0000:07:05.0: PCI bridge to [bus 09-09]
[    0.784067] pci 0000:07:05.0:   bridge window [io  0xd000-0xdfff]
[    0.784072] pci 0000:07:05.0:   bridge window [mem 0xfbd00000-0xfbdfffff]
[    0.784076] pci 0000:07:05.0:   bridge window [mem pref disabled]
[    0.784083] pci 0000:07:07.0: PCI bridge to [bus 0a-0a]
[    0.784084] pci 0000:07:07.0:   bridge window [io  disabled]
[    0.784089] pci 0000:07:07.0:   bridge window [mem disabled]
[    0.784093] pci 0000:07:07.0:   bridge window [mem pref disabled]
[    0.784099] pci 0000:07:09.0: PCI bridge to [bus 0b-0b]
[    0.784101] pci 0000:07:09.0:   bridge window [io  disabled]
[    0.784106] pci 0000:07:09.0:   bridge window [mem disabled]
[    0.784109] pci 0000:07:09.0:   bridge window [mem pref disabled]
[    0.784116] pci 0000:06:00.0: PCI bridge to [bus 07-0b]
[    0.784119] pci 0000:06:00.0:   bridge window [io  0xd000-0xdfff]
[    0.784124] pci 0000:06:00.0:   bridge window [mem 0xfbc00000-0xfbdfffff]
[    0.784128] pci 0000:06:00.0:   bridge window [mem pref disabled]
[    0.784134] pci 0000:00:1c.0: PCI bridge to [bus 06-0b]
[    0.784137] pci 0000:00:1c.0:   bridge window [io  0xd000-0xdfff]
[    0.784141] pci 0000:00:1c.0:   bridge window [mem 0xfbb00000-0xfbdfffff]
[    0.784144] pci 0000:00:1c.0:   bridge window [mem pref disabled]
[    0.784149] pci 0000:00:1c.4: PCI bridge to [bus 05-05]
[    0.784152] pci 0000:00:1c.4:   bridge window [io  0xc000-0xcfff]
[    0.784156] pci 0000:00:1c.4:   bridge window [mem 0xfba00000-0xfbafffff]
[    0.784159] pci 0000:00:1c.4:   bridge window [mem 0xf6f00000-0xf6ffffff 64bit pref]
[    0.784165] pci 0000:00:1c.5: PCI bridge to [bus 04-04]
[    0.784166] pci 0000:00:1c.5:   bridge window [io  disabled]
[    0.784170] pci 0000:00:1c.5:   bridge window [mem disabled]
[    0.784173] pci 0000:00:1c.5:   bridge window [mem pref disabled]
[    0.784178] pci 0000:00:1c.6: PCI bridge to [bus 03-03]
[    0.784180] pci 0000:00:1c.6:   bridge window [io  0xb000-0xbfff]
[    0.784185] pci 0000:00:1c.6:   bridge window [mem 0xfb900000-0xfb9fffff]
[    0.784188] pci 0000:00:1c.6:   bridge window [mem pref disabled]
[    0.784193] pci 0000:00:1c.7: PCI bridge to [bus 02-02]
[    0.784195] pci 0000:00:1c.7:   bridge window [io  0x1000-0x1fff]
[    0.784199] pci 0000:00:1c.7:   bridge window [mem 0xc0000000-0xc01fffff]
[    0.784203] pci 0000:00:1c.7:   bridge window [mem 0xc0200000-0xc03fffff 64bit pref]
[    0.784208] pci 0000:00:1e.0: PCI bridge to [bus 0c-0c]
[    0.784211] pci 0000:00:1e.0:   bridge window [io  0xe000-0xefff]
[    0.784215] pci 0000:00:1e.0:   bridge window [mem 0xfbe00000-0xfbefffff]
[    0.784218] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.784229]   alloc irq_desc for 16 on node -1
[    0.784230]   alloc kstat_irqs on node -1
[    0.784235] pci 0000:00:03.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.784239] pci 0000:00:03.0: setting latency timer to 64
[    0.784245]   alloc irq_desc for 17 on node -1
[    0.784247]   alloc kstat_irqs on node -1
[    0.784250] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.784253] pci 0000:00:1c.0: setting latency timer to 64
[    0.784263] pci 0000:06:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.784267] pci 0000:06:00.0: setting latency timer to 64
[    0.784276] pci 0000:07:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.784280] pci 0000:07:01.0: setting latency timer to 64
[    0.784289] pci 0000:07:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.784293] pci 0000:07:05.0: setting latency timer to 64
[    0.784302]   alloc irq_desc for 19 on node -1
[    0.784303]   alloc kstat_irqs on node -1
[    0.784306] pci 0000:07:07.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.784310] pci 0000:07:07.0: setting latency timer to 64
[    0.784319] pci 0000:07:09.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.784323] pci 0000:07:09.0: setting latency timer to 64
[    0.784330] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.784333] pci 0000:00:1c.4: setting latency timer to 64
[    0.784340] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.784343] pci 0000:00:1c.5: setting latency timer to 64
[    0.784350]   alloc irq_desc for 18 on node -1
[    0.784351]   alloc kstat_irqs on node -1
[    0.784354] pci 0000:00:1c.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.784357] pci 0000:00:1c.6: setting latency timer to 64
[    0.784364] pci 0000:00:1c.7: enabling device (0104 -> 0107)
[    0.784367] pci 0000:00:1c.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.784370] pci 0000:00:1c.7: setting latency timer to 64
[    0.784375] pci 0000:00:1e.0: setting latency timer to 64
[    0.784379] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.784381] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.784383] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.784384] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.784386] pci_bus 0000:00: resource 8 [mem 0xc0000000-0xdfffffff]
[    0.784388] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfed8ffff]
[    0.784390] pci_bus 0000:01: resource 0 [io  0xa000-0xafff]
[    0.784392] pci_bus 0000:01: resource 1 [mem 0xf8000000-0xfb8fffff]
[    0.784394] pci_bus 0000:01: resource 2 [mem 0xd4000000-0xdfffffff 64bit pref]
[    0.784396] pci_bus 0000:06: resource 0 [io  0xd000-0xdfff]
[    0.784397] pci_bus 0000:06: resource 1 [mem 0xfbb00000-0xfbdfffff]
[    0.784399] pci_bus 0000:07: resource 0 [io  0xd000-0xdfff]
[    0.784401] pci_bus 0000:07: resource 1 [mem 0xfbc00000-0xfbdfffff]
[    0.784403] pci_bus 0000:08: resource 1 [mem 0xfbc00000-0xfbcfffff]
[    0.784405] pci_bus 0000:09: resource 0 [io  0xd000-0xdfff]
[    0.784406] pci_bus 0000:09: resource 1 [mem 0xfbd00000-0xfbdfffff]
[    0.784408] pci_bus 0000:05: resource 0 [io  0xc000-0xcfff]
[    0.784410] pci_bus 0000:05: resource 1 [mem 0xfba00000-0xfbafffff]
[    0.784412] pci_bus 0000:05: resource 2 [mem 0xf6f00000-0xf6ffffff 64bit pref]
[    0.784414] pci_bus 0000:03: resource 0 [io  0xb000-0xbfff]
[    0.784416] pci_bus 0000:03: resource 1 [mem 0xfb900000-0xfb9fffff]
[    0.784418] pci_bus 0000:02: resource 0 [io  0x1000-0x1fff]
[    0.784419] pci_bus 0000:02: resource 1 [mem 0xc0000000-0xc01fffff]
[    0.784421] pci_bus 0000:02: resource 2 [mem 0xc0200000-0xc03fffff 64bit pref]
[    0.784423] pci_bus 0000:0c: resource 0 [io  0xe000-0xefff]
[    0.784425] pci_bus 0000:0c: resource 1 [mem 0xfbe00000-0xfbefffff]
[    0.784427] pci_bus 0000:0c: resource 4 [io  0x0000-0x0cf7]
[    0.784428] pci_bus 0000:0c: resource 5 [io  0x0d00-0xffff]
[    0.784430] pci_bus 0000:0c: resource 6 [mem 0x000a0000-0x000bffff]
[    0.784432] pci_bus 0000:0c: resource 7 [mem 0x000d0000-0x000dffff]
[    0.784434] pci_bus 0000:0c: resource 8 [mem 0xc0000000-0xdfffffff]
[    0.784436] pci_bus 0000:0c: resource 9 [mem 0xf0000000-0xfed8ffff]
[    0.784460] NET: Registered protocol family 2
[    0.784502] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.784642] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.785218] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.785505] TCP: Hash tables configured (established 131072 bind 65536)
[    0.785507] TCP reno registered
[    0.785509] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.785517] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.785579] NET: Registered protocol family 1
[    0.785653] pci 0000:01:00.0: Boot video device
[    0.785699] PCI: CLS 32 bytes, default 64
[    0.785912] cpufreq-nforce2: No nForce2 chipset.
[    0.785930] Scanning for low memory corruption every 60 seconds
[    0.786002] audit: initializing netlink socket (disabled)
[    0.786007] type=2000 audit(1311087645.500:1): initialized
[    0.795040] highmem bounce pool size: 64 pages
[    0.795044] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.796091] VFS: Disk quotas dquot_6.5.2
[    0.796136] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.796549] fuse init (API version 7.14)
[    0.796612] msgmni has been set to 1653
[    0.877228] Freeing initrd memory: 12036k freed
[    0.880898] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.880901] io scheduler noop registered
[    0.880902] io scheduler deadline registered
[    0.880912] io scheduler cfq registered (default)
[    0.881008] pcieport 0000:00:03.0: setting latency timer to 64
[    0.881032]   alloc irq_desc for 45 on node -1
[    0.881033]   alloc kstat_irqs on node -1
[    0.881040] pcieport 0000:00:03.0: irq 45 for MSI/MSI-X
[    0.881092] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.881120]   alloc irq_desc for 46 on node -1
[    0.881121]   alloc kstat_irqs on node -1
[    0.881127] pcieport 0000:00:1c.0: irq 46 for MSI/MSI-X
[    0.881176] pcieport 0000:00:1c.4: setting latency timer to 64
[    0.881203]   alloc irq_desc for 47 on node -1
[    0.881205]   alloc kstat_irqs on node -1
[    0.881210] pcieport 0000:00:1c.4: irq 47 for MSI/MSI-X
[    0.881258] pcieport 0000:00:1c.5: setting latency timer to 64
[    0.881285]   alloc irq_desc for 48 on node -1
[    0.881287]   alloc kstat_irqs on node -1
[    0.881292] pcieport 0000:00:1c.5: irq 48 for MSI/MSI-X
[    0.881340] pcieport 0000:00:1c.6: setting latency timer to 64
[    0.881367]   alloc irq_desc for 49 on node -1
[    0.881369]   alloc kstat_irqs on node -1
[    0.881374] pcieport 0000:00:1c.6: irq 49 for MSI/MSI-X
[    0.881423] pcieport 0000:00:1c.7: setting latency timer to 64
[    0.881451]   alloc irq_desc for 50 on node -1
[    0.881452]   alloc kstat_irqs on node -1
[    0.881458] pcieport 0000:00:1c.7: irq 50 for MSI/MSI-X
[    0.881521] pcieport 0000:06:00.0: setting latency timer to 64
[    0.881562]   alloc irq_desc for 51 on node -1
[    0.881564]   alloc kstat_irqs on node -1
[    0.881572] pcieport 0000:06:00.0: irq 51 for MSI/MSI-X
[    0.881649] pcieport 0000:07:01.0: setting latency timer to 64
[    0.881690]   alloc irq_desc for 52 on node -1
[    0.881691]   alloc kstat_irqs on node -1
[    0.881700] pcieport 0000:07:01.0: irq 52 for MSI/MSI-X
[    0.881780] pcieport 0000:07:05.0: setting latency timer to 64
[    0.881821]   alloc irq_desc for 53 on node -1
[    0.881822]   alloc kstat_irqs on node -1
[    0.881831] pcieport 0000:07:05.0: irq 53 for MSI/MSI-X
[    0.881908] pcieport 0000:07:07.0: setting latency timer to 64
[    0.881949]   alloc irq_desc for 54 on node -1
[    0.881951]   alloc kstat_irqs on node -1
[    0.881959] pcieport 0000:07:07.0: irq 54 for MSI/MSI-X
[    0.882038] pcieport 0000:07:09.0: setting latency timer to 64
[    0.882080]   alloc irq_desc for 55 on node -1
[    0.882081]   alloc kstat_irqs on node -1
[    0.882089] pcieport 0000:07:09.0: irq 55 for MSI/MSI-X
[    0.882168] Firmware did not grant requested _OSC control
[    0.882170] aer 0000:00:03.0:pcie02: AER service couldn't init device: no _OSC support
[    0.882185] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.882195] Firmware did not grant requested _OSC control
[    0.882210] Firmware did not grant requested _OSC control
[    0.882215] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.882471] vesafb: framebuffer at 0xd5000000, mapped to 0xf8080000, using 3072k, total 3072k
[    0.882473] vesafb: mode is 1024x768x32, linelength=4096, pages=0
[    0.882474] vesafb: scrolling: redraw
[    0.882477] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    0.882548] Console: switching to colour frame buffer device 128x48
[    0.882569] fb0: VESA VGA frame buffer device
[    0.882584] intel_idle: MWAIT substates: 0x1120
[    0.882586] intel_idle: v0.4 model 0x1E
[    0.882587] intel_idle: lapic_timer_reliable_states 0x2
[    0.882675] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.882679] ACPI: Power Button [PWRB]
[    0.882718] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.882720] ACPI: Power Button [PWRF]
[    0.883067] ACPI: acpi_idle yielding to intel_idle
[    0.885787] ERST: Table is not found!
[    0.885802] isapnp: Scanning for PnP cards...
[    0.885932] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.886978] brd: module loaded
[    0.887359] loop: module loaded
[    0.887467] ata_piix 0000:00:1f.2: version 2.13
[    0.887478]   alloc irq_desc for 21 on node -1
[    0.887480]   alloc kstat_irqs on node -1
[    0.887484] ata_piix 0000:00:1f.2: PCI INT D -> GSI 21 (level, low) -> IRQ 21
[    0.887488] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.887516] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.887560] scsi0 : ata_piix
[    0.887619] scsi1 : ata_piix
[    0.888883] ata1: SATA max UDMA/133 cmd 0x8c00 ctl 0x8880 bmdma 0x8400 irq 21
[    0.888888] ata2: SATA max UDMA/133 cmd 0x8800 ctl 0x8480 bmdma 0x8408 irq 21
[    0.888904] ata_piix 0000:00:1f.5: PCI INT D -> GSI 21 (level, low) -> IRQ 21
[    0.888908] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    0.888936] ata_piix 0000:00:1f.5: setting latency timer to 64
[    0.888964] scsi2 : ata_piix
[    0.889002] scsi3 : ata_piix
[    0.890037] ata3: SATA max UDMA/133 cmd 0x9c00 ctl 0x9880 bmdma 0x9400 irq 21
[    0.890040] ata4: SATA max UDMA/133 cmd 0x9800 ctl 0x9480 bmdma 0x9408 irq 21
[    0.890084] pata_acpi 0000:09:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.890103] pata_acpi 0000:09:00.0: setting latency timer to 64
[    0.890114] pata_acpi 0000:09:00.0: PCI INT A disabled
[    0.890127] pata_acpi 0000:03:00.1: enabling device (0000 -> 0001)
[    0.890132] pata_acpi 0000:03:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.890147] pata_acpi 0000:03:00.1: setting latency timer to 64
[    0.890156] pata_acpi 0000:03:00.1: PCI INT B disabled
[    0.890357] Fixed MDIO Bus: probed
[    0.890381] PPP generic driver version 2.4.2
[    0.890409] tun: Universal TUN/TAP device driver, 1.6
[    0.890411] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.890460] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.890473] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.890482] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.890485] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    0.890509] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    0.890534] ehci_hcd 0000:00:1a.0: debug port 2
[    0.894404] ehci_hcd 0000:00:1a.0: cache line size of 32 is not supported
[    0.894416] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xf7ffe000
[    0.906658] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    0.906737] hub 1-0:1.0: USB hub found
[    0.906741] hub 1-0:1.0: 2 ports detected
[    0.906788]   alloc irq_desc for 23 on node -1
[    0.906790]   alloc kstat_irqs on node -1
[    0.906794] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.906802] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.906805] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    0.906828] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.906851] ehci_hcd 0000:00:1d.0: debug port 2
[    0.910722] ehci_hcd 0000:00:1d.0: cache line size of 32 is not supported
[    0.910734] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xf7ffd000
[    0.922620] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    0.922690] hub 2-0:1.0: USB hub found
[    0.922695] hub 2-0:1.0: 2 ports detected
[    0.922742] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.922756] uhci_hcd: USB Universal Host Controller Interface driver
[    0.922817] PNP: No PS/2 controller found. Probing ports directly.
[    0.925297] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.925306] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.925361] mice: PS/2 mouse device common for all mice
[    0.925431] rtc_cmos 00:03: RTC can wake from S4
[    0.925456] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.925480] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.925551] device-mapper: uevent: version 1.0.3
[    0.925623] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[    0.925693] device-mapper: multipath: version 1.1.1 loaded
[    0.925695] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.925773] EISA: Probing bus 0 at eisa.0
[    0.925775] EISA: Cannot allocate resource for mainboard
[    0.925776] Cannot allocate resource for EISA slot 1
[    0.925778] Cannot allocate resource for EISA slot 2
[    0.925779] Cannot allocate resource for EISA slot 3
[    0.925780] Cannot allocate resource for EISA slot 4
[    0.925782] Cannot allocate resource for EISA slot 5
[    0.925783] Cannot allocate resource for EISA slot 6
[    0.925784] Cannot allocate resource for EISA slot 7
[    0.925786] Cannot allocate resource for EISA slot 8
[    0.925787] EISA: Detected 0 cards.
[    0.925958] cpuidle: using governor ladder
[    0.926085] cpuidle: using governor menu
[    0.926278] TCP cubic registered
[    0.926370] NET: Registered protocol family 10
[    0.926629] lo: Disabled Privacy Extensions
[    0.926778] NET: Registered protocol family 17
[    0.928012] Using IPI No-Shortcut mode
[    0.928063] PM: Resume from disk failed.
[    0.928070] registered taskstats version 1
[    0.928483]   Magic number: 3:984:32
[    0.928535] rtc_cmos 00:03: setting system clock to 2011-07-19 15:00:46 UTC (1311087646)
[    0.928537] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.928538] EDD information not available.
[    1.209714] isapnp: No Plug & Play device found
[    1.216608] ata3: SATA link down (SStatus 0 SControl 300)
[    1.227220] ata4: SATA link down (SStatus 0 SControl 300)
[    1.229925] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    1.350345] hub 1-1:1.0: USB hub found
[    1.350434] hub 1-1:1.0: 6 ports detected
[    1.461437] usb 2-1: new high speed USB device using ehci_hcd and address 2
[    1.593622] hub 2-1:1.0: USB hub found
[    1.593749] hub 2-1:1.0: 8 ports detected
[    1.665068] usb 1-1.1: new high speed USB device using ehci_hcd and address 3
[    1.681026] ata2.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.681038] ata2.01: SATA link down (SStatus 0 SControl 300)
[    1.685237] ata1.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.685248] ata1.01: SATA link down (SStatus 0 SControl 300)
[    1.689494] ata2.00: ATA-8: WDC WD10EARS-00Y5B1, 80.00A80, max UDMA/133
[    1.689497] ata2.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.689771] ata1.00: ATA-8: WDC WD10EARS-00Z5B1, 80.00A80, max UDMA/133
[    1.689774] ata1.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.705537] ata2.00: configured for UDMA/133
[    1.705729] ata1.00: configured for UDMA/133
[    1.706153] scsi 0:0:0:0: Direct-Access     ATA      WDC WD10EARS-00Z 80.0 PQ: 0 ANSI: 5
[    1.706301] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.706473] sd 0:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    1.706541] scsi 1:0:0:0: Direct-Access     ATA      WDC WD10EARS-00Y 80.0 PQ: 0 ANSI: 5
[    1.706646] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    1.706763] sd 1:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    1.706965] sd 0:0:0:0: [sda] Write Protect is off
[    1.706971] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.707138] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.707183] sd 1:0:0:0: [sdb] Write Protect is off
[    1.707189] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.707375] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.707970]  sda:
[    1.708146]  sdb: sdb1 sdb2 sdb3 < sda1 sda2 sda3 sda4
[    1.725884] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.730372]  sdb5 > sdb4
[    1.752538] sd 1:0:0:0: [sdb] Attached SCSI disk
[    1.752882] Freeing unused kernel memory: 688k freed
[    1.753309] Write protecting the kernel text: 4944k
[    1.753455] Write protecting the kernel read-only data: 1976k
[    1.772665] <30>udev[106]: starting version 167
[    1.808311] pata_jmicron 0000:03:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.808335] pata_jmicron 0000:03:00.1: setting latency timer to 64
[    1.810917] scsi4 : pata_jmicron
[    1.810971] scsi5 : pata_jmicron
[    1.811494] ata5: PATA max UDMA/100 cmd 0xbc00 ctl 0xb880 bmdma 0xb400 irq 19
[    1.811496] ata6: PATA max UDMA/100 cmd 0xb800 ctl 0xb480 bmdma 0xb408 irq 19
[    1.813734] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.813749] r8169 0000:05:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.813780] r8169 0000:05:00.0: setting latency timer to 64
[    1.813820]   alloc irq_desc for 56 on node -1
[    1.813822]   alloc kstat_irqs on node -1
[    1.813833] r8169 0000:05:00.0: irq 56 for MSI/MSI-X
[    1.814180] r8169 0000:05:00.0: eth0: RTL8168d/8111d at 0xf83dc000, 48:5b:39:59:81:5a, XID 083000c0 IRQ 56
[    1.814680] xhci_hcd 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.814693] xhci_hcd 0000:08:00.0: setting latency timer to 64
[    1.814696] xhci_hcd 0000:08:00.0: xHCI Host Controller
[    1.814734] xhci_hcd 0000:08:00.0: new USB bus registered, assigned bus number 3
[    1.815168] xhci_hcd 0000:08:00.0: irq 17, io mem 0xfbcfe000
[    1.818413] usb usb3: No SuperSpeed endpoint companion for config 1  interface 0 altsetting 0 ep 129: using minimum values
[    1.818471] xHCI xhci_add_endpoint called for root hub
[    1.818473] xHCI xhci_check_bandwidth called for root hub
[    1.818494] hub 3-0:1.0: USB hub found
[    1.818497] hub 3-0:1.0: 4 ports detected
[    1.832650] usb 1-1.5: new low speed USB device using ehci_hcd and address 4
[    1.847402] Initializing USB Mass Storage driver...
[    1.850057] scsi6 : usb-storage 1-1.1:1.0
[    1.850263] usbcore: registered new interface driver usb-storage
[    1.850265] USB Mass Storage support registered.
[    1.940806] usbcore: registered new interface driver hiddev
[    1.941849] generic-usb: probe of 0003:058F:6364.0001 failed with error -22
[    1.941923] usbcore: registered new interface driver usbhid
[    1.941925] usbhid: USB HID core driver
[    1.973509] ata5.00: ATAPI: HL-DT-STDVD-RAM GH22NP20, 2.00, max UDMA/66
[    1.989075] ata5.00: configured for UDMA/66
[    1.991759] scsi 4:0:0:0: CD-ROM            HL-DT-ST DVD-RAM GH22NP20 2.00 PQ: 0 ANSI: 5
[    1.996312] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.996318] Uniform CD-ROM driver Revision: 3.20
[    1.996405] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    1.996443] sr 4:0:0:0: Attached scsi generic sg2 type 5
[    2.000954] usb 1-1.6: new high speed USB device using ehci_hcd and address 5
[    2.168747] ahci 0000:03:00.0: version 3.0
[    2.168768] ahci 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.169282] firewire_ohci 0000:0c:03.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.172450] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.0/input/input2
[    2.172508] logitech 0003:046D:C517.0002: input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1a.0-1.5/input0
[    2.177778] logitech 0003:046D:C517.0003: fixing up Logitech keyboard report descriptor
[    2.178185] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.1/input/input3
[    2.178312] logitech 0003:046D:C517.0003: input,hiddev96,hidraw1: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1a.0-1.5/input1
[    2.184351] ahci 0000:03:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[    2.184358] ahci 0000:03:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[    2.184369] ahci 0000:03:00.0: setting latency timer to 64
[    2.184598] scsi7 : ahci
[    2.184731] scsi8 : ahci
[    2.184817] ata7: SATA max UDMA/133 abar m8192@0xfb9fe000 port 0xfb9fe100 irq 18
[    2.184821] ata8: SATA max UDMA/133 abar m8192@0xfb9fe000 port 0xfb9fe180 irq 18
[    2.263860] firewire_ohci: Added fw-ohci device 0000:0c:03.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x1
[    2.503171] ata8: SATA link down (SStatus 0 SControl 300)
[    2.503188] ata7: SATA link down (SStatus 0 SControl 300)
[    2.755085] firewire_core: created device fw0: GUID 001e8c0000d620da, S400
[    2.847637] scsi 6:0:0:0: Direct-Access     Generic- SD/MMC           1.00 PQ: 0 ANSI: 0
[    2.848392] scsi 6:0:0:1: Direct-Access     Generic- Compact Flash    1.01 PQ: 0 ANSI: 0
[    2.849100] scsi 6:0:0:2: Direct-Access     Generic- SM/xD-Picture    1.02 PQ: 0 ANSI: 0
[    2.849855] scsi 6:0:0:3: Direct-Access     Generic- MS/MS-Pro        1.03 PQ: 0 ANSI: 0 CCS
[    2.850423] sd 6:0:0:0: Attached scsi generic sg3 type 0
[    2.850516] sd 6:0:0:1: Attached scsi generic sg4 type 0
[    2.850600] sd 6:0:0:2: Attached scsi generic sg5 type 0
[    2.850685] sd 6:0:0:3: Attached scsi generic sg6 type 0
[    2.854974] sd 6:0:0:0: [sdc] Attached SCSI removable disk
[    2.855742] sd 6:0:0:1: [sdd] Attached SCSI removable disk
[    2.856566] sd 6:0:0:2: [sde] Attached SCSI removable disk
[    2.857364] sd 6:0:0:3: [sdf] Attached SCSI removable disk
[   18.017560] Adding 33554428k swap on /dev/sdb2.  Priority:-1 extents:1 across:33554428k 
[   18.032770] <30>udev[436]: starting version 167
[   18.041785] lp: driver loaded but no devices found
[   18.083465] Linux agpgart interface v0.103
[   18.127917] ATK0110 ATK0110:00: EC enabled
[   18.158014] nvidia: module license 'NVIDIA' taints kernel.
[   18.158016] Disabling lock debugging due to kernel taint
[   18.186342] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   18.191248] rtusb init --->
[   18.191322] === pAd = fa5c8000, size = 472668 ===
[   18.191323] <-- RTMPAllocAdapterBlock, Status=0
[   18.193111] usbcore: registered new interface driver rt2870
[   18.214597] type=1400 audit(1311112863.819:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=769 comm="apparmor_parser"
[   18.215172] type=1400 audit(1311112863.819:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=769 comm="apparmor_parser"
[   18.215537] type=1400 audit(1311112863.819:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=769 comm="apparmor_parser"
[   18.276068]   alloc irq_desc for 22 on node -1
[   18.276070]   alloc kstat_irqs on node -1
[   18.276076] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   18.276109]   alloc irq_desc for 57 on node -1
[   18.276110]   alloc kstat_irqs on node -1
[   18.276118] HDA Intel 0000:00:1b.0: irq 57 for MSI/MSI-X
[   18.276137] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   18.334856] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   18.334860] hda_intel: Disable MSI for Nvidia chipset
[   18.334880] HDA Intel 0000:01:00.1: setting latency timer to 64
[   19.125702] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   19.125710] nvidia 0000:01:00.0: setting latency timer to 64
[   19.125713] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   19.125810] NVRM: loading NVIDIA UNIX x86 Kernel Module  275.19  Tue Jul 12 18:29:18 PDT 2011
[   19.134252] type=1400 audit(1311112864.743:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=1127 comm="apparmor_parser"
[   19.135115] type=1400 audit(1311112864.743:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1129 comm="apparmor_parser"
[   19.135694] type=1400 audit(1311112864.743:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1129 comm="apparmor_parser"
[   19.136061] type=1400 audit(1311112864.743:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1129 comm="apparmor_parser"
[   19.138449] type=1400 audit(1311112864.747:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=1130 comm="apparmor_parser"
[   19.140458] type=1400 audit(1311112864.747:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1134 comm="apparmor_parser"
[   19.141140] type=1400 audit(1311112864.747:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1134 comm="apparmor_parser"
[   19.288845] ppdev: user-space parallel port driver
[   19.508726] <-- RTMPAllocTxRxRingMemory, Status=0
[   19.510413] -->RTUSBVenderReset
[   19.510535] <--RTUSBVenderReset

```

---

### Post by sea52020 on 2011-07-19
I just got a black screen... when I was trying to view the log by Log File Viewer.
the screen itself doesn't turn off though since the power light is still blue(instead if blinking orange).
after reboot WITHOUT the disk check(i skipped it for the 1st time), it cannot get a gui but black screen still. In addition, there's a Empathy window blinking, I think that's because I have added empathy to the startup app.
goes to terminal try to use dmesg and it tells me "Read-Only file system".

However, I think that's an different issue... since I sometimes get the same problem when running StarCraft2 in Win7.(looks the same though).

---

### Post by wildmanne39 on 2011-07-19
> **sea52020 said:**
> I just got a black screen... when I was trying to view the log by Log File Viewer.
the screen itself doesn't turn off though since the power light is still blue(instead if blinking orange).
after reboot WITHOUT the disk check(i skipped it for the 1st time), it cannot get a gui but black screen still. In addition, there's a Empathy window blinking, I think that's because I have added empathy to the startup app.
goes to terminal try to use dmesg and it tells me "Read-Only file system".

However, I think that's an different issue... since I sometimes get the same problem when running StarCraft2 in Win7.(looks the same though).Hi, I think this is your freeze problem.
> (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    19.042] (WW) Disabling Keyboard0
[    19.042] (WW) Disabling Mouse0 I am not sure how to turn hotplugging of but I am going to research it and I ask a friend about it so he may post the answer here. 

Your new keyboard and mouse they are usb correct? are they wireless?

Can you boot ubuntu now? or is it broken?

---

### Post by sea52020 on 2011-07-19
> **wildmanne39 said:**
> Hi, I think this is your freeze problem.
 I am not sure how to turn hotplugging of but I am going to research it and I ask a friend about it so he may post the answer here. 

Your new keyboard and mouse they are usb correct? are they wireless?

Can you boot ubuntu now? or is it broken?

I can use ubuntu now without problem, if i don't modify any file in Home Folder or use Log viewer(using terminal is fine).

My keyboard and mouse is wireless from Logitech. It uses usb adapter, not bluethooth.

---

### Post by wildmanne39 on 2011-07-19
> **sea52020 said:**
> I can use ubuntu now without problem, if i don't modify any file in Home Folder or use Log viewer(using terminal is fine).

My keyboard and mouse is wireless from Logitech. It uses usb adapter, not bluethooth.Hi, that is a different issue, it just started occurring correct? That may be a permission issue, you should probably start another thread for that issue. I am going to wait for awhile and see if my friend comes online because he may know how to fix the hotplug problem.

---

### Post by sea52020 on 2011-07-19
> **wildmanne39 said:**
> Hi, that is a different issue, it just started occurring correct? That may be a permission issue, you should probably start another thread for that issue. I am going to wait for awhile and see if my friend comes online because he may know how to fix the hotplug problem.

Thanks,
so the hotplug problem is related to the black screen or the freeze?
I'll probably see what's going on with the black screen and get more information then ask for help about that.

---

### Post by wildmanne39 on 2011-07-19
> **sea52020 said:**
> Thanks,
so the hotplug problem is related to the black screen or the freeze?
I'll probably see what's going on with the black screen and get more information then ask for help about that.Hi, I have done more research on the hotplug in the xorg file, while it looks like a problem it is not, many people have that in there file and it does not cause any problems so we are back to not knowing why your system is freezing.

---

### Post by sea52020 on 2011-07-20
> **wildmanne39 said:**
> Hi, I have done more research on the hotplug in the xorg file, while it looks like a problem it is not, many people have that in there file and it does not cause any problems so we are back to not knowing why your system is freezing.

ok... I take that as a good news? lol

So, I found that it's not possible for me to use the LibreOffice Writer that comes with 11.04. gui freezes when it's loading no matter when where how.
Didn't try openOffice yet.
May the problem caused by some permission things?

---

### Post by wildmanne39 on 2011-07-20
> **sea52020 said:**
> ok... I take that as a good news? lol

So, I found that it's not possible for me to use the LibreOffice Writer that comes with 11.04. gui freezes when it's loading no matter when where how.
Didn't try openOffice yet.
May the problem caused by some permission things?Hi, it is impossible for me to say for sure since we have not seen any errors in any log files.

You might be having issues from the nvidia driver, You could try using another one and see if that helps, I could not use the one recommended I had to use the older driver.

---

### Post by sea52020 on 2011-07-20
> **wildmanne39 said:**
> Hi, it is impossible for me to say for sure since we have not seen any errors in any log files.

You might be having issues from the nvidia driver, You could try using another one and see if that helps, I could not use the one recommended I had to use the older driver.


I switched to the one from official website of nvidia, seems they are the same though.
Thanks any way.
I'll try to create another user and see if that happens to that home folder.

---

