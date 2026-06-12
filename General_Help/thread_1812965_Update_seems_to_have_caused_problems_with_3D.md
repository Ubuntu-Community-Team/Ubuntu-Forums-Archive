---
title: "Update seems to have caused problems with 3D"
date: 2011-07-27
forum: General Help
---

### Post by kaldor on 2011-07-27
Running 11.04 64bit. AMD Radeon HD 6450 with proprietary drivers.

This is a new PC that I got a few weeks ago. Up until tonight, there have never been any issues. I earlier had an update for dbus and dbus-x11 which prompted me to reboot. After rebooting, I am noticing some mild to severe problems when gaming.

It's like there's a jitter, yet the ingame fps (frames per second) is normal. Window dragging on the desktop looks fine, but dragging the unity launcher up/down looks slightly jittery too. 

Thinking it was just some sort of Unity/compiz problem, I booted into Classic desktop with no effects. Issue still persists.

Really want to fix this, as it's a pretty annoying issue =/

Edit: After posting this, I realized it seems to have caused issues with scrolling too. Scrolling does not look smooth and is also jittery.

---

### Post by wildmanne39 on 2011-07-27
Hi, have a look at this link it usually fix that issue.
[http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow](http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow)

---

### Post by kaldor on 2011-07-27
I did that the day that I installed Ubuntu on the new PC. It worked instantly back then, and I just double checked again. It's unchecked and lag is still occurring.

It's a brand new issue brought on after this update.

---

### Post by wildmanne39 on 2011-07-27
Hi, run these two commands in a terminal please
```
sudo lshw
```
```
lsmod
```
and post the outcome here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by kaldor on 2011-07-27
sudo lshw gives:

```
    capabilities: smbios-2.6 dmi-2.6 vsyscall64 vsyscall32
    configuration: boot=normal chassis=desktop family=103C_53316J G=D sku=QN598AA#ABC uuid=E2B2ED2B-F10A-960D-CDDF-E7FA0AEE261F
  *-core
       description: Motherboard
       product: 2AB1
       vendor: FOXCONN
       physical id: 0
       version: 1.00
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 6.06
          date: 03/22/2011
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pnp upgrade shadowing escd cdboot bootselect socketedrom edd int5printscreen int9keyboard int14serial int17printer int10video acpi usb biosbootspecification netboot
     *-cpu
          description: CPU
          product: AMD Phenom(tm) II X6 1065T Processor
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 4
          bus info: cpu@0
          version: AMD Phenom(tm) II X6 1065T Processor
          slot: CPU 1
          size: 800MHz
          capacity: 3400MHz
          width: 64 bits
          clock: 200MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt arat cpb npt lbrv svm_lock nrip_save pausefilter cpufreq
          configuration: cores=6 enabledcores=6
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 768KiB
             capacity: 768KiB
             capabilities: pipeline-burst internal varies
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 3MiB
             capacity: 3MiB
             capabilities: pipeline-burst internal varies
        *-cache:2
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             size: 6MiB
             capacity: 6MiB
             capabilities: pipeline-burst internal varies
     *-memory
          description: System Memory
          physical id: f
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: [empty]
             product: ModulePartNumber00
             vendor: Manufacturer00
             physical id: 0
             serial: SerNum00
             slot: DIMM1
        *-bank:1
             description: [empty]
             product: ModulePartNumber01
             vendor: Manufacturer01
             physical id: 1
             serial: SerNum01
             slot: DIMM2
        *-bank:2
             description: DIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: M378B5273CH0-CH9
             vendor: Samsung
             physical id: 2
             serial: 815D2498
             slot: DIMM3
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:3
             description: DIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: M378B5273CH0-CH9
             vendor: Samsung
             physical id: 3
             serial: 7E5D2498
             slot: DIMM4
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
     *-pci:0
          description: Host bridge
          product: RS880 Host Bridge
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
        *-pci:0
             description: PCI bridge
             product: RS780 PCI to PCI bridge (ext gfx port 0)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:d000(size=4096) memory:fe900000-fe9fffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: NI Caicos [AMD RADEON HD 6450]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=fglrx_pci latency=0
                resources: irq:45 memory:d0000000-dfffffff memory:fe9e0000-fe9fffff ioport:d000(size=256) memory:fe9c0000-fe9dffff
           *-multimedia
                description: Audio device
                product: ATI Technologies Inc
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=HDA Intel latency=0
                resources: irq:44 memory:fe9bc000-fe9bffff
        *-pci:1
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 1)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 memory:fea00000-feafffff
           *-network UNCLAIMED
                description: Network controller
                product: Ralink corp.
                vendor: Ralink corp.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: latency=0
                resources: memory:feaf0000-feafffff
        *-pci:2
             description: PCI bridge
             product: RS780/RS880 PCI to PCI bridge (PCIE port 5)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: a
             bus info: pci@0000:00:0a.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:e000(size=4096) memory:feb00000-febfffff ioport:fdf00000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth3
                version: 05
                serial: 2c:27:d7:1a:a3:d5
                size: 100Mbit/s
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.108 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
                resources: irq:43 ioport:e800(size=256) memory:febff000-febfffff memory:fdffc000-fdffffff
        *-storage
             description: SATA controller
             product: SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
             vendor: ATI Technologies Inc
             physical id: 11
             bus info: pci@0000:00:11.0
             logical name: scsi0
             logical name: scsi2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=64
             resources: irq:22 ioport:c000(size=8) ioport:b000(size=4) ioport:a000(size=8) ioport:9000(size=4) ioport:8000(size=16) memory:fe8ffc00-fe8fffff
           *-disk
                description: ATA Disk
                product: WDC WD15EARS-60M
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 51.0
                serial: WD-WCAZA7135268
                size: 1397GiB (1500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=da88dd9b
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 800a-f007
                   size: 98MiB
                   capacity: 100MiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2011-06-01 00:16:01 filesystem=ntfs label=SYSTEM state=clean
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 3.1
                   serial: 26ab1b8d-8f70-2941-ac37-08d93a0ea3f3
                   size: 639GiB
                   capacity: 639GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2011-05-03 17:53:01 filesystem=ntfs label=OS modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
              *-volume:2
                   description: Windows NTFS volume
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   version: 3.1
                   serial: c0dd42e2-2b1a-fc49-810d-fdd1b24c7428
                   size: 12GiB
                   capacity: 12GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2011-05-03 21:01:49 filesystem=ntfs label=HP_RECOVERY state=clean
              *-volume:3
                   description: Extended partition
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   size: 745GiB
                   capacity: 745GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /
                      capacity: 737GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,stripe=1,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 8191MiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: DVD-RAM GH60L
                vendor: hp
                physical id: 1
                bus info: scsi@2:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: RD05
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-usb:0
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:16 memory:fe8fe000-fe8fefff
        *-usb:1
             description: USB Controller
             product: SB7x0 USB OHCI1 Controller
             vendor: ATI Technologies Inc
             physical id: 12.1
             bus info: pci@0000:00:12.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:16 memory:fe8fd000-fe8fdfff
        *-usb:2
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:17 memory:fe8ff800-fe8ff8ff
        *-usb:3
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:fe8fc000-fe8fcfff
        *-usb:4
             description: USB Controller
             product: SB7x0 USB OHCI1 Controller
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:fe8f7000-fe8f7fff
        *-usb:5
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:19 memory:fe8ff400-fe8ff4ff
        *-serial
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 3c
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: driver=piix4_smbus latency=0
             resources: irq:0
        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=HDA Intel latency=64
             resources: irq:16 memory:fe8f0000-fe8f3fff
        *-isa
             description: ISA bridge
             product: SB7x0/SB8x0/SB9x0 LPC host controller
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:3
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
     *-pci:1
          description: Host bridge
          product: Family 10h Processor HyperTransport Configuration
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 10h Processor Address Map
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Family 10h Processor DRAM Controller
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 10h Processor Miscellaneous Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:5
          description: Host bridge
          product: Family 10h Processor Link Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-scsi
          physical id: 1
          bus info: usb@2:6
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@4:0.0.1
             logical name: /dev/sdc
        *-disk:2
             description: SCSI Disk
             physical id: 0.0.2
             bus info: scsi@4:0.0.2
             logical name: /dev/sdd
        *-disk:3
             description: SCSI Disk
             product: MS/MS-Pro
             vendor: Generic-
             physical id: 0.0.3
             bus info: scsi@4:0.0.3
             logical name: /dev/sde
             version: 1.03
             serial: 3
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sde
  *-power UNCLAIMED
       product: Standard Efficiency
       physical id: 1
       capacity: 32768mWh

```

```

Module                  Size  Used by
snd_seq_dummy          12798  0 
binfmt_misc            17565  1 
parport_pc             36959  0 
ppdev                  17113  0 
vboxnetadp             13382  0 
vboxnetflt             28297  0 
vesafb                 13761  1 
vboxdrv               268268  2 vboxnetadp,vboxnetflt
snd_hda_codec_hdmi     28167  1 
snd_hda_codec_realtek   336771  1 
joydev                 17606  0 
snd_seq_midi           13324  0 
snd_hda_intel          33211  2 
snd_rawmidi            30486  1 snd_seq_midi
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_seq_midi_event     14899  1 snd_seq_midi
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96391  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq                61621  3 snd_seq_dummy,snd_seq_midi,snd_seq_midi_event
sp5100_tco             13744  0 
psmouse                73535  0 
edac_core              53845  0 
snd_seq_device         14462  4 snd_seq_dummy,snd_seq_midi,snd_rawmidi,snd_seq
snd_timer              29602  2 snd_pcm,snd_seq
edac_mce_amd           23464  0 
k10temp                13119  0 
serio_raw              13166  0 
i2c_piix4              13303  0 
fglrx                2739144  114 
snd                    67382  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_rawmidi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq,snd_seq_device,snd_timer
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
usb_storage            53538  0 
uas                    17996  0 
usbhid                 46956  0 
hid                    91020  1 usbhid
ahci                   25951  2 
r8169                  48022  0 
libahci                26642  1 ahci

```

Edit: Should also mention that heat is not an issue. Currently "sensors" shows:

```
temp1:       +15.5°C  (high = +70.0°C)      
```

The highest I have seen it go was 26 degrees when testing how far I could push it by running many games at once.

Edit 2: I relogged into Classic (No Effects) and the lag issues are 100% gone. Weird that they didn't disappear before (I am entirely sure I didn't log into the compiz one, I checked). Going to relogin to Unity to see if it persists.

---

### Post by wildmanne39 on 2011-07-27
Hi, I think I found the problem,Fglrx  Driver.

You would be better off installing the ati driver then using the fglrx, but I can not promise that will fix the issue but here is a link about it.
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)

I am off for the note it is late here.

---

### Post by kaldor on 2011-07-27
> **wildmanne39 said:**
> Hi, I think I found the problem,Fglrx  Driver

I am beginning to think it is Unity/Compiz.

I just booted into Classic with no effects and gameplay is smooth and pure in all games. Not a clue what's causing this random lag.

Also, the lag seems to be able to be reproduced easily ingame. It's not a *constant* jitter/lag, but when going to certain areas in the games. For example if I can avoid parts of some maps on Urban Terror and other Quake games, and that avoids the jitter. As soon as I take a few steps into a certain area, lag starts up. 

It's not the game's fault because it has never happened before and it happens across all games I've tried. Weird.

That said, the launcher is still not smooth when moved, and same goes for scrolling in Firefox, Chromium, and Nautilus while in Unity.

---

### Post by wildmanne39 on 2011-07-27
Hi, it sounds like there was an update to compiz that is effecting your system, I had backports and prerelease checked in synaptic and I was getting updates that caused problems in natty, after I turned them off my system became stable again.

---

