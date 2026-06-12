---
title: "File/folder creation or moving causes system to freeze"
date: 2011-07-08
forum: General Help
---

### Post by Jynxed on 2011-07-08
I just got a Acer Aspire 7551g-7466, and I am running a dual-boot system of Natty Narwhal and Windows 7. I have been running Ubuntu in Classic mode, since I absolutely can't stand the Unity interface.

Every time I try to move, create, or rename a folder or file in the explorer, the computer freezes. If I restart, the command has been processed, but it will freeze again if I try to move something.

Please, if there is any more information you need, ask, and I will post it as soon as possible.

---

### Post by Diametric on 2011-07-09
A list of your hardware specs would be a good start.  Also, if you are able to open the command terminal, type the following and post the out put:

```
free mem
```

---

### Post by Jynxed on 2011-07-09
```
             total       used       free     shared    buffers     cached
Mem:       3094120     863624    2230496          0      45924     336276
-/+ buffers/cache:     481424    2612696
Swap:      4191228          0    4191228

```

EDIT: I should also note that Chromium sometimes causes the mouse to become a ball with the waiting circle and freezes the computer as well. And upon starting my linux partition this time, th eapplet that shows the four desktop environments and the clock have loaded white and act as empty space, though other applets cannot be moved there. I can still add those applets elsewhere.

---

### Post by wildmanne39 on 2011-07-09
> **Jynxed said:**
> ```
             total       used       free     shared    buffers     cached
Mem:       3094120     863624    2230496          0      45924     336276
-/+ buffers/cache:     481424    2612696
Swap:      4191228          0    4191228

```

EDIT: I should also note that Chromium sometimes causes the mouse to become a ball with the waiting circle and freezes the computer as well. And upon starting my linux partition this time, th eapplet that shows the four desktop environments and the clock have loaded white and act as empty space, though other applets cannot be moved there. I can still add those applets elsewhere.Hi run these commands in a terminal
```
sudo lshw
```
```
lspci | grep VGA
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets. Also chromuim has been know to cause crashes in natty, you might install chrome from there web site I have read that it works very well. Here is a link for people with freezing issues.
[https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)

---

### Post by Diametric on 2011-07-09
Would still like to see the hardware specs, too...

---

### Post by Jynxed on 2011-07-09
[Specs]("http://us.acer.com/ac/en/US/content/model/LX.RCE02.072")

```
alicia                    
    description: Notebook
    version: V1.15
    width: 32 bits
    capabilities: smbios-2.6 dmi-2.6 smp-1.4 smp
    configuration: boot=oem-specific chassis=notebook cpus=4 uuid=9089C4C0-7B21-11E0-B49C-98762D0F4C82
  *-core
       description: Motherboard
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies LTD
          physical id: 0
          version: V1.15
          date: 10/26/2010
          size: 118KiB
          capacity: 1984KiB
          capabilities: pci pnp upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-board UNCLAIMED
          description: Motherboard
          product: Aspire 7551
          vendor: Acer
          physical id: 2
          version: V1.15
          serial: LXRCE02073119006312000
          slot: Not Applicable
     *-cpu:0
          description: CPU
          product: AMD Phenom(tm) II N970 Quad-Core Processor
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 4
          bus info: cpu@0
          version: 15.5.3
          slot: Socket S1G4
          size: 800MHz
          capacity: 2200MHz
          width: 64 bits
          clock: 200MHz
          capabilities: x86-64 boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp 3dnowext 3dnow constant_tsc nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt nodeid_msr npt lbrv svm_lock nrip_save cpufreq
          configuration: cores=4 enabledcores=4 threads=4
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 128KiB
             capacity: 512KiB
             clock: 1GHz (1.0ns)
             capabilities: pipeline-burst internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 512KiB
             capacity: 2MiB
             clock: 1GHz (1.0ns)
             capabilities: pipeline-burst internal write-back unified
     *-memory
          description: System Memory
          physical id: d
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM DDR3 Synchronous 667 MHz (1.5 ns)
             product: NT2GC64B88B0NS-CG
             vendor: Nanya Technology
             physical id: 0
             serial: 46BA5C14
             slot: S1
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM DDR3 Synchronous 667 MHz (1.5 ns)
             product: NT2GC64B88B0NS-CG
             vendor: Nanya Technology
             physical id: 1
             serial: C57ADC16
             slot: S2
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 15.5.3
          size: 2200MHz
          capacity: 2200MHz
          capabilities: cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-cpu:2
          physical id: 3
          bus info: cpu@2
          version: 15.5.3
          size: 800MHz
          capacity: 800MHz
          capabilities: cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-cpu:3
          physical id: 5
          bus info: cpu@3
          version: 15.5.3
          size: 800MHz
          capacity: 800MHz
          capabilities: cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
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
             resources: irq:40 ioport:9000(size=4096) memory:d0000000-d00fffff ioport:c0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: NI Seymour [AMD Radeon HD 6470M]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=fglrx_pci latency=0
                resources: irq:46 memory:c0000000-cfffffff memory:d0000000-d001ffff ioport:9000(size=256) memory:d0040000-d005ffff
           *-multimedia
                description: Audio device
                product: ATI Technologies Inc
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:02:00.1
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=HDA Intel latency=0
                resources: irq:44 memory:d0020000-d0023fff
        *-pci:1
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 0)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 memory:d0100000-d01fffff
           *-network
                description: Ethernet interface
                product: NetLink BCM57780 Gigabit Ethernet PCIe
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 01
                serial: 20:6a:8a:3b:50:7c
                size: 10Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 duplex=half firmware=sb latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:45 memory:d0100000-d010ffff
        *-pci:2
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
             resources: irq:42 memory:d0200000-d02fffff
           *-network
                description: Wireless interface
                product: AR9287 Wireless Network Adapter (PCI-Express)
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:06:00.0
                logical name: wlan0
                version: 01
                serial: ec:55:f9:94:7e:6e
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=2.6.38-8-generic firmware=N/A ip=192.168.1.7 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:17 memory:d0200000-d020ffff
        *-storage
             description: SATA controller
             product: SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
             vendor: ATI Technologies Inc
             physical id: 11
             bus info: pci@0000:00:11.0
             logical name: scsi0
             logical name: scsi1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=64
             resources: irq:43 ioport:8440(size=8) ioport:8430(size=4) ioport:8420(size=8) ioport:8410(size=4) ioport:8400(size=16) memory:d0506800-d0506bff
           *-disk
                description: ATA Disk
                product: TOSHIBA MK6465GS
                vendor: Toshiba
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: GJ00
                serial: 31FVB2ARB
                size: 596GiB (640GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=ac4319e7
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 14f3-f4ce
                   size: 13GiB
                   capacity: 13GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2011-01-24 02:26:01 filesystem=ntfs label=PQSERVICE state=clean
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 3.1
                   serial: 8a60-ea1f
                   size: 70MiB
                   capacity: 100MiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2011-05-10 16:46:46 filesystem=ntfs label=SYSTEM RESERVED state=clean
              *-volume:2
                   description: Windows NTFS volume
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   version: 3.1
                   serial: 78004d9d-6edc-cd42-9060-4dbffa9ef76b
                   size: 306GiB
                   capacity: 306GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2011-05-10 16:46:58 filesystem=ntfs label=ACER modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
              *-volume:3
                   description: Extended partition
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   size: 276GiB
                   capacity: 276GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /
                      capacity: 272GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 4093MiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: DVD RW AD-7585H
                vendor: Optiarc
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                logical name: /media/AUTORUN
                version: KX04
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500 state=mounted status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
                   logical name: /media/AUTORUN
                   configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500 state=mounted
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
             resources: irq:18 memory:d0504000-d0504fff
        *-usb:1
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
             resources: irq:17 memory:d0506000-d05060ff
        *-usb:2
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
             resources: irq:18 memory:d0505000-d0505fff
        *-usb:3
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
             resources: irq:17 memory:d0506400-d05064ff
        *-serial UNCLAIMED
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 42
             width: 32 bits
             clock: 66MHz
             configuration: latency=0
        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 40
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=HDA Intel latency=64
             resources: irq:16 memory:d0500000-d0503fff
        *-isa
             description: ISA bridge
             product: SB7x0/SB8x0/SB9x0 LPC host controller
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 40
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
             version: 40
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

```

```
02:00.0 VGA compatible controller: ATI Technologies Inc NI Seymour [AMD Radeon HD 6470M]

``` "VGA" was in a red font

Right, I had actually forgotten about Chrome.

---

### Post by wildmanne39 on 2011-07-09
> **Jynxed said:**
> I just got a Acer Aspire 7551g-7466, and I am running a dual-boot system of Natty Narwhal and Windows 7. I have been running Ubuntu in Classic mode, since I absolutely can't stand the Unity interface.

Every time I try to move, create, or rename a folder or file in the explorer, the computer freezes. If I restart, the command has been processed, but it will freeze again if I try to move something.

Please, if there is any more information you need, ask, and I will post it as soon as possible.Hi, do you know what video card driver you are using? Fglrx Inteferes With Radeon Driver. You might have a look at this link if you have the fglrx driver installed, if you are not sure run this command 
```
lsmod
```
and post the results. Also are you using any compiz settings?
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)

---

### Post by Diametric on 2011-07-09
Wonder what happened with this - was curious to see wht the issue was.  Clearly not a hardware capacity issue.

---

### Post by wildmanne39 on 2011-07-09
Hi, it is probably and video card driver but there maybe other issues.

---

### Post by Jynxed on 2011-07-10
> **wildmanne39 said:**
> Hi, do you know what video card driver you are using? Fglrx Inteferes With Radeon Driver. You might have a look at this link if you have the fglrx driver installed, if you are not sure run this command 
```
lsmod
```and post the results. Also are you using any compiz settings?
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)

```
Module                  Size  Used by
nls_utf8               12493  1 
isofs                  39571  1 
parport_pc             32111  0 
ppdev                  12849  0 
vesafb                 13449  1 
binfmt_misc            13213  1 
joydev                 17322  0 
snd_hda_codec_hdmi     27479  1 
arc4                   12473  2 
snd_hda_codec_realtek   255820  1 
snd_hda_intel          24140  4 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
ath9k                 103633  0 
snd_pcm                80244  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               66851  0 
videodev               75143  1 uvcvideo
fglrx                2434640  161 
mac80211              257001  1 ath9k
psmouse                73312  0 
snd                    55295  17 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ath9k_common           13611  1 ath9k
ath9k_hw              300328  2 ath9k,ath9k_common
ath                    19141  2 ath9k,ath9k_hw
sp5100_tco             13456  0 
i2c_piix4              13095  0 
serio_raw              12990  0 
cfg80211              156212  3 ath9k,mac80211,ath
k10temp                12951  0 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
video                  18951  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
tg3                   131476  0 
ahci                   21591  3 
libahci                25548  1 ahci

```

Yes, I do have a few compiz settings. Are there any in particular known to cause this problem?
I have a ATI Mobility Radeon™ 5650 graphics card

Sorry about taking time to reply, I had work, and its always results in having no time.

---

### Post by wildmanne39 on 2011-07-10
Hi, if you are using effects in classic mode you need to see this link.
[http://www.webupd8.org/2011/05/how-to-downgrade-to-compiz-086-in.html](http://www.webupd8.org/2011/05/how-to-downgrade-to-compiz-086-in.html)

Also you can open log file viewer from the menu and look at dmesg logs and see if there are any errors reported. 

Also log out and log into ubuntu classic with no effects and see if that fixes your problem, then we will have a good idea it is compiz.

Here is a link on freezing issues.
[https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)

None of these things may be related to the freezing issue when you are moving or creating files, but it is likely.

I am not going to be on most of the day I am working on a guide for the cube and effects.

---

