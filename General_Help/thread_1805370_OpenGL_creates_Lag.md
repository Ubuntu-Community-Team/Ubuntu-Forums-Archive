---
title: "OpenGL creates Lag"
date: 2011-07-15
forum: General Help
---

### Post by joeturtle on 2011-07-15
Hello. I'm an Ubuntu 11.04 user. I recently switched from Windows Vista, and I really do love the Unity layout (although there could be some improvements) and how beautiful Ubuntu is. But one thing I noticed is that Ubuntu seems to be lagging, but only slightly. This issue is very noticeable when typing, as there is a split-second lag between when I press the keys and when the letters show up on the screen. This becomes a major problem when trying to delete. Videos on youtube also seem to be very choppy, along with videos downloaded to my hard drive (although not as bad as youtube). 

I've noticed none of these problems in Vista...and from my understanding, Vista is much more of a system-intense OS than Ubuntu. So with that said, I need to ask...why is my system being so slow/choppy? I've provided my system information below, so you can check to see if my understanding is correct. 

System Information:
AMD Turion(tm) X2 Dual-Core Mobile RM-75 
3852MB of RAM
Radeon HD 3200 Graphics (ATI Technologies Inc RS780M/RS780MN)

If you need more information, don't be shy to ask. I'd be happy to provide it for you.


Note:
When using Ubuntu Classic, I have the same lags as using the default Ubuntu Desktop. But when using Ubuntu Classic (no effects), it runs much, much smother. (Even the Youtube lag is gone). So I tested to see which one of the options is creating the horrible lag...and I found it was OpenGL. Disabling it completely from the Compiz menu clears up the lag incredibly. 

But OpenGL is needed to use any of the fun features Ubuntu has (including Unity). So...can anyone offer any help as to why OpenGL is causing the lag and how to fix it? Thanks!

---

### Post by wildmanne39 on 2011-07-16
Hi, try what this link says and see if it helps, but please do not change any other setting in compiz without a guide or you could break unity.
[http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow](http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow)

---

### Post by joeturtle on 2011-07-16
> **wildmanne39 said:**
> Hi, try what this link says and see if it helps, but please do not change any other setting in compiz without a guide or you could break unity.
[http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow](http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow)

Thanks Wildmanne for the answer, but that made no change at all.

---

### Post by wildmanne39 on 2011-07-16
Hi, that usually helps a lot, I had the typing problem come up I had to stop using my wireless keyboard.

The slowness in classic is another issue as well compiz needs to be downgraded for the best performace, here is a link for that.
[http://www.webupd8.org/2011/05/how-to-downgrade-to-compiz-086-in.html](http://www.webupd8.org/2011/05/how-to-downgrade-to-compiz-086-in.html)

If you want more help you can run these commands in a terminal
```
sudo lshw
```
```
lspci | grep VGA
```
```
lsmod
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.

Hopefully this information will give us a better idea how to help you.

---

### Post by joeturtle on 2011-07-16
For lshw

```
jacob-hp-touchsmart-tx2-notebook-pc
    description: Notebook
    product: HP TouchSmart tx2 Notebook PC (FR171AV)
    vendor: Hewlett-Packard
    version: Rev 1
    serial: CNF920123H
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4
    configuration: boot=normal chassis=notebook family=103C_5335KV sku=FR171AV uuid=434E4639-3230-3132-3348-00238BBC95D4
  *-core
       description: Motherboard
       product: 3045
       vendor: Quanta
       physical id: 0
       version: 16.09
       serial: None
       slot: Base Board Chassis Location
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 0
          version: F.12
          date: 02/17/2009
          size: 1MiB
          capabilities: isa pci pnp upgrade shadowing escd cdboot bootselect int5printscreen int9keyboard int14serial int17printer acpi usb agp smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: AMD Turion(tm) X2 Dual-Core Mobile RM-75
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: a
          bus info: cpu@0
          version: 15.3.1
          serial: NotSupport
          slot: Socket M2/S1G1
          size: 550MHz
          capacity: 2200MHz
          width: 64 bits
          clock: 2GHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow constant_tsc nonstop_tsc extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch osvw skinit arat lbrv svm_lock nrip_save cpufreq
        *-cache:0
             description: L1 cache
             physical id: b
             slot: L1 Cache
             size: 128KiB
             capacity: 256KiB
             capabilities: synchronous internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: c
             slot: L2 Cache
             size: 512KiB
             capacity: 1MiB
             capabilities: synchronous internal write-back unified
     *-memory
          description: System Memory
          physical id: d
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: SODIMM DDR2 Synchronous 800 MHz (1.2 ns)
             product: 16HTF25664HY-800E1
             vendor: 000000000000002C
             physical id: 0
             serial: 2C000000000000000F0911DE2984CD
             slot: SODIMM 0
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: SODIMM DDR2 Synchronous 800 MHz (1.2 ns)
             product: 16HTF25664HY-800E1
             vendor: 000000000000002C
             physical id: 1
             serial: 2C000000000000000F0911DE2984CC
             slot: SODIMM 1
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
     *-pci:0
          description: Host bridge
          product: RS780 Host Bridge
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
        *-pci:0
             description: PCI bridge
             product: RS780/RS880 PCI to PCI bridge (int gfx)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci ht normal_decode bus_master cap_list
             resources: ioport:5000(size=4096) memory:d2200000-d23fffff ioport:c0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: RS780M/RS780MN [Radeon HD 3200 Graphics]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi vga_controller bus_master cap_list rom
                configuration: driver=fglrx_pci latency=0
                resources: irq:18 memory:c0000000-cfffffff ioport:5000(size=256) memory:d2300000-d230ffff memory:d2200000-d22fffff
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
             resources: irq:40 ioport:3000(size=8192) memory:d1200000-d21fffff ioport:d0000000(size=16777216)
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
             resources: irq:41 memory:d1100000-d11fffff
           *-network
                description: Wireless interface
                product: BCM4312 802.11b/g LP-PHY
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:08:00.0
                logical name: eth1
                version: 01
                serial: 00:21:00:e6:d6:a3
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 ip=10.0.0.8 latency=0 multicast=yes wireless=IEEE 802.11bg
                resources: irq:17 memory:d1100000-d1103fff
        *-pci:3
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 2)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:2000(size=4096) memory:d2500000-d25fffff ioport:d1000000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:09:00.0
                logical name: eth0
                version: 02
                serial: 00:23:8b:bc:95:d4
                size: 10Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:43 ioport:2000(size=256) memory:d1010000-d1010fff memory:d1000000-d100ffff memory:d1020000-d102ffff
        *-storage
             description: SATA controller
             product: SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
             vendor: ATI Technologies Inc
             physical id: 11
             bus info: pci@0000:00:11.0
             logical name: scsi2
             logical name: scsi3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=64
             resources: irq:22 ioport:6038(size=8) ioport:604c(size=4) ioport:6030(size=8) ioport:6048(size=4) ioport:6010(size=16) memory:d2409000-d24093ff
           *-disk
                description: ATA Disk
                product: TOSHIBA MK3252GS
                vendor: Toshiba
                physical id: 0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: LV01
                serial: 49UGF6QYS
                size: 298GiB (320GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=00001e70
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: d166abbf-84f6-43e6-9db6-0e0f0e6d318e
                   size: 294GiB
                   capacity: 294GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-07-12 14:59:38 filesystem=ext4 lastmountpoint=/ modified=2011-07-15 21:11:38 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2011-07-15 23:23:18 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   size: 3836MiB
                   capacity: 3836MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 3836MiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: CDDVDW TS-L633M
                vendor: TSSTcorp
                physical id: 1
                bus info: scsi@3:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 0200
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
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
             resources: irq:16 memory:d2408000-d2408fff
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
             resources: irq:16 memory:d2407000-d2407fff
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
             resources: irq:17 memory:d2409500-d24095ff
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
             resources: irq:18 memory:d2406000-d2406fff
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
             resources: irq:18 memory:d2405000-d2405fff
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
             resources: irq:19 memory:d2409400-d24094ff
        *-serial
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 3a
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: driver=piix4_smbus latency=0
             resources: irq:0
        *-ide
             description: IDE interface
             product: SB7x0/SB8x0/SB9x0 IDE Controller
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide msi bus_master cap_list
             configuration: driver=pata_atiixp latency=64
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:6000(size=16)
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
             resources: irq:16 memory:d2400000-d2403fff
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
        *-pci:4
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
             resources: ioport:1000(size=4096)
        *-usb:6
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
             vendor: ATI Technologies Inc
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:d2404000-d2404fff
     *-pci:1
          description: Host bridge
          product: Family 11h Processor HyperTransport Configuration
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 40
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 11h Processor Address Map
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Family 11h Processor DRAM Controller
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 11h Processor Miscellaneous Control
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
          product: Family 11h Processor Link Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-scsi:0
          physical id: 1
          bus info: usb@1:1
          logical name: scsi8
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@8:0.0.0
             logical name: /dev/sdb
             size: 3827MiB (4012MB)
             capabilities: partitioned partitioned:dos
           *-volume
                description: Windows FAT volume
                vendor: mkdosfs
                physical id: 1
                bus info: scsi@8:0.0.0,1
                logical name: /dev/sdb1
                version: FAT32
                serial: 389e-e985
                size: 3826MiB
                capacity: 3826MiB
                capabilities: primary bootable fat initialized
                configuration: FATs=2 filesystem=fat label=SanDisk
     *-scsi:1
          physical id: 2
          bus info: usb@1:4
          logical name: scsi9
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@9:0.0.0
             logical name: /dev/sdc

```

For lspci | grep VGA

```
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]

```

For lsmod

```
Module                  Size  Used by
parport_pc             32111  0 
ppdev                  12849  0 
vesafb                 13449  1 
snd_hrtimer            12680  1 
binfmt_misc            13213  1 
vboxnetadp             13348  0 
vboxnetflt             27855  0 
vboxdrv               238410  2 vboxnetadp,vboxnetflt
snd_atiixp_modem       18624  0 
snd_via82xx_modem      18305  0 
snd_hda_codec_si3054    12924  1 
snd_hda_codec_realtek   255882  1 
snd_intel8x0m          18493  0 
snd_hda_intel          24140  2 
snd_ac97_codec        105614  3 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m
snd_hda_codec          90901  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
ac97_bus               12642  1 snd_ac97_codec
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  7 snd_atiixp_modem,snd_via82xx_modem,snd_hda_codec_si3054,snd_intel8x0m,snd_ac97_codec,snd_hda_intel,snd_hda_codec
uvcvideo               66851  0 
joydev                 17322  0 
snd_seq_midi           13132  0 
hp_wmi                 13418  0 
sparse_keymap          13666  1 hp_wmi
videodev               75143  1 uvcvideo
fglrx                2434640  50 
snd_rawmidi            25269  1 snd_seq_midi
hid_ntrig              12818  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  3 snd_seq_midi,snd_seq_midi_event
lib80211_crypt_tkip    17203  0 
snd_timer              28659  3 snd_hrtimer,snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
ir_lirc_codec          12770  0 
lirc_dev               18720  1 ir_lirc_codec
ir_sony_decoder        12493  0 
ir_jvc_decoder         12490  0 
psmouse                59039  0 
ir_rc6_decoder         12490  0 
ir_rc5_decoder         12490  0 
rc_rc6_mce             12454  0 
ir_nec_decoder         12490  0 
wl                   2642531  0 
ene_ir                 22309  0 
rc_core                25760  9 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,rc_rc6_mce,ir_nec_decoder,ene_ir
snd                    55295  19 snd_atiixp_modem,snd_via82xx_modem,snd_hda_codec_si3054,snd_hda_codec_realtek,snd_intel8x0m,snd_ac97_codec,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
video                  18951  0 
serio_raw              12990  0 
soundcore              12600  1 snd
sp5100_tco             13456  0 
k10temp                12951  0 
i2c_piix4              13095  0 
snd_page_alloc         14073  5 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_hda_intel,snd_pcm
lib80211               14570  2 lib80211_crypt_tkip,wl
shpchp                 32345  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usbhid                 41704  1 hid_ntrig
hid                    77084  2 hid_ntrig,usbhid
usb_storage            43946  1 
ahci                   21591  2 
uas                    17676  0 
r8169                  46630  0 
libahci                25548  1 ahci
pata_atiixp            12968  0 

```

And thanks for you help. I really do appreciate it.

---

### Post by wildmanne39 on 2011-07-16
Hi, first are you running this in virtualbox? If not then I suspect it is this Fglrx Inteferes With Radeon Driver. Have you installed your ati driver from additional drivers?

Have a look at this link.
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)

---

### Post by joeturtle on 2011-07-16
Thank you, thank you, thank you, wildmanne39!

That link you provided fixed the problem! I'm experiencing no more lag and youtube plays flawlessly. :D 

Thanks again!

---

### Post by wildmanne39 on 2011-07-16
> **joeturtle said:**
> Thank you, thank you, thank you, wildmanne39!

That link you provided fixed the problem! I'm experiencing no more lag and youtube plays flawlessly. :D 

Thanks again!Hi, you are very welcome! I am glad it worked.

---

