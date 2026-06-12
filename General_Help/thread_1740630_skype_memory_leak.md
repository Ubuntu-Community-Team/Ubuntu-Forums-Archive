---
title: "skype memory leak?"
date: 2011-04-27
forum: General Help
---

### Post by Ashrael on 2011-04-27
Hi all!

Yesterday this happened for the first time, ALL of my memory used! Took a look and found skype to be the memory addict. Killed the process, restarted skype, and... no problem.
Today same thing...... 

Looks like it does it only when I start it the first time.

Anybody else have had this happen?

:confused:

---

### Post by user1397 on 2011-04-27
> **Ashrael said:**
> Hi all!

Yesterday this happened for the first time, ALL of my memory used! Took a look and found skype to be the memory addict. Killed the process, restarted skype, and... no problem.
Today same thing...... 

Looks like it does it only when I start it the first time.

Anybody else have had this happen?

:confused:Have you upgraded to the latest version?  I haven't encountered this problem yet

---

### Post by ksprasad on 2011-04-27
Hi,
 
 Have you tried reinstalling Skype? After that also same issue?
 
Regards,
ksprasad

---

### Post by Ashrael on 2011-04-27
using 2.2.0.25-1maverick right now... AFAIK it's the latest version...


Thanks for thinking with me!

---

### Post by kingofsnakes2111 on 2011-05-02
Same problem here. When I run skype from unity, sometime it takes all memory (and start swapping), but if I run it from terminal, it starts normally.

---

### Post by Ashrael on 2011-05-05
Somehow it has stopped occuring in my system, so I think we can call this solved I guess...

Anybody out there disagree?


Thanks  :P

---

### Post by Ashrael on 2011-05-06
I take it back!!! It happened again!!! It is a combination of factors that leads to this behavior I guess. I think it has something to do with someone calling me when I am not around, and me then calling them back.


keep ya posted.

---

### Post by zob on 2011-05-11
I think I can confirm this issue with the latest skype version on 11.04 (ubuntu AND xubuntu). I can't add any detail right now, but I'll follow the post and probably post later.
If it is the same issue that I have, I don't think it is related to lost calls.

---

### Post by evoka0 on 2011-05-12
Same here in ubuntu 10.10 and skype 2.2.0.25  it has happen twice already, after dialing a hard-line number.

---

### Post by Ashrael on 2011-05-27
I still have this happen to me every once in a while, but I found out that it happens at the same time with the person I am calling. She uses 8.10 still, so this might be an issue?

Check out my lshw, lsusb, lspci and lsmod, maybe we can find the answer in there.

LSHW:


>     description: Notebook
    product: Satellite Pro A40
    vendor: TOSHIBA
    version: PSA45E-0016T-DU
    serial: 24843080G
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: administrator_password=disabled boot=normal chassis=notebook frontpanel_password=disabled keyboard_password=disabled power-on_password=disabled uuid=FB91F200-0042-1571-8045-B0D024843080
  *-core
       description: Motherboard
       product: Portable PC
       vendor: TOSHIBA
       physical id: 0
       version: Version A0
       serial: $$S2427035
     *-firmware
          description: BIOS
          vendor: TOSHIBA
          physical id: 0
          version: Version 1.50 (01/26/2004)
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pcmcia pnp upgrade shadowing vesa cdboot bootselect pcmciaboot edd int13floppytoshiba int13floppy720 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) CPU 2.60GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.2.9
          slot: uFC-PGA Socket
          size: 2600MHz
          capacity: 2600MHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 12
             slot: CPU Internal
             size: 8KiB
             capacity: 8KiB
             clock: 1GHz (1.0ns)
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 13
             slot: CPU Internal
             size: 128KiB
             capacity: 128KiB
             clock: 1GHz (1.0ns)
             capabilities: internal write-back
     *-memory
          description: System Memory
          physical id: 81
          slot: System board or motherboard
          size: 2GiB
          capacity: 2GiB
        *-bank:0
             description: SODIMM SDRAM Synchronous
             physical id: 0
             slot: DIMM 0
             size: 1GiB
             width: 64 bits
        *-bank:1
             description: SODIMM SDRAM Synchronous
             physical id: 1
             slot: DIMM 1
             size: 1GiB
             width: 64 bits
     *-pci
          description: Host bridge
          product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-generic:0 UNCLAIMED
             description: System peripheral
             product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
             vendor: Intel Corporation
             physical id: 0.1
             bus info: pci@0000:00:00.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: latency=0
        *-generic:1 UNCLAIMED
             description: System peripheral
             product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
             vendor: Intel Corporation
             physical id: 0.3
             bus info: pci@0000:00:00.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: latency=0
        *-display:0
             description: VGA compatible controller
             product: 82852/855GM Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:d8000000-dfffffff memory:d0000000-d007ffff ioport:eff8(size=8)
        *-display:1 UNCLAIMED
             description: Display controller
             product: 82852/855GM Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
             resources: memory:80000000-87ffffff memory:8c000000-8c07ffff
        *-usb:0
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:18c0(size=32)
        *-usb:1
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:18e0(size=32)
        *-usb:2
             description: USB Controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:8c080000-8c0803ff
        *-pci
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 83
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:c000(size=4096) memory:cff00000-cfffffff memory:88000000-8bffffff
           *-network
                description: Ethernet interface
                product: 82801DB PRO/100 VE (MOB) Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:01:08.0
                logical name: eth0
                version: 83
                serial: 00:08:0d:c2:50:d0
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s
                resources: irq:20 memory:cffff000-cfffffff ioport:cf40(size=64)
           *-pcmcia
                description: CardBus bridge
                product: ToPIC100 PCI to Cardbus Bridge with ZV Support
                vendor: Toshiba America Info Systems
                physical id: b
                bus info: pci@0000:01:0b.0
                version: 33
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=0 maxlatency=5 mingnt=128
                resources: irq:18 memory:cff00000-cff00fff ioport:c000(size=256) ioport:c400(size=256) memory:88000000-8bffffff memory:90000000-93ffffff
        *-isa
             description: ISA bridge
             product: 82801DBM (ICH4-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801DBM (ICH4-M) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:bfa0(size=16) memory:8c080400-8c0807ff
           *-disk
                description: ATA Disk
                product: TOSHIBA MK4025GA
                vendor: Toshiba
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: KA10
                serial: 14TA6470S
                size: 37GiB (40GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=a4f34ee6
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   logical name: /
                   version: 1.0
                   serial: 05d5b13e-21ed-4e8a-8c1f-408f2e0e3f90
                   size: 10GiB
                   capacity: 10GiB
                   capabilities: primary bootable journaled extended_attributes large_files recover ext3 ext2 initialized
                   configuration: created=2011-02-12 03:50:58 filesystem=ext3 modified=2011-05-15 11:09:03 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,commit=5,barrier=0,data=ordered mounted=2011-05-27 15:53:32 state=mounted
              *-volume:1
                   description: Linux swap volume
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   version: 1
                   serial: b0ff17f2-b359-4212-a58c-3d51ddd94f49
                   size: 1498MiB
                   capacity: 1498MiB
                   capabilities: primary nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
              *-volume:2
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   logical name: /home
                   version: 1.0
                   serial: ca4370e0-d356-43e3-88cd-732c908dd6ed
                   size: 25GiB
                   capacity: 25GiB
                   capabilities: primary journaled extended_attributes large_files recover ext3 ext2 initialized
                   configuration: created=2009-12-08 01:10:34 filesystem=ext3 modified=2011-05-27 15:53:34 mount.fstype=ext3 mount.options=rw,relatime,errors=continue,commit=5,barrier=0,data=ordered mounted=2011-05-27 15:53:34 state=mounted
           *-cdrom
                description: DVD reader
                product: DVD-ROM SD-R2412
                vendor: TOSHIBA
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1330
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5 status=nodisc
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0
             resources: irq:17 ioport:1000(size=256) ioport:1880(size=64) memory:8c080800-8c0809ff memory:8c080a00-8c080aff
        *-communication UNCLAIMED
             description: Modem
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm generic cap_list
             configuration: latency=0
             resources: ioport:1400(size=256) ioport:1800(size=128)
  *-battery
       description: Lithium Ion Battery
       product: LPX53E
       vendor: TOSHIBA
       physical id: 1
       version: 01/16/04
       serial: 3200151716
       slot: 1st Battery
       configuration: voltage=10.8V
  *-network
       description: Wireless interface
       physical id: 2
       bus info: usb@1:2
       logical name: wlan2
       serial: 00:60:b3:46:97:d6
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=zd1211rw driverversion=2.6.35-28-generic firmware=N/A ip=10.0.0.101 link=yes multicast=yes wireless=IEEE 802.11bg

LSUSB:

> Bus 003 Device 004: ID 046d:c714 Logitech, Inc. diNovo Edge Keyboard
Bus 003 Device 003: ID 046d:c713 Logitech, Inc. 
Bus 003 Device 002: ID 046d:0b04 Logitech, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 1395:0020 Sennheiser Communications 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 079b:0062 Sagem XG-76NA 802.11bg
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

LSPCI:

> 00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 83)
01:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 33)

LSMOD:

> Module                  Size  Used by
gspca_sonixj           25900  0 
gspca_main             23644  1 gspca_sonixj
videodev               43098  1 gspca_main
v4l1_compat            13359  1 videodev
aes_i586                7280  2 
aes_generic            26875  1 aes_i586
binfmt_misc             6599  1 
snd_intel8x0           25664  2 
snd_ac97_codec         99227  1 snd_intel8x0
ac97_bus                1014  1 snd_ac97_codec
snd_pcm                71475  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi            4588  0 
arc4                    1165  2 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
i915                  295435  3 
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
zd1211rw               43440  0 
hid_logitech            8971  0 
ppdev                   5556  0 
ff_memless              4393  1 hid_logitech
snd_timer              19067  2 snd_pcm,snd_seq
joydev                  8767  0 
drm_kms_helper         30200  1 i915
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
mac80211              231959  1 zd1211rw
pcmcia                 35973  0 
drm                   168060  3 i915,drm_kms_helper
snd                    49038  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport_pc             26058  1 
usbhid                 36882  1 hid_logitech
intel_agp              26566  2 i915
yenta_socket           21518  0 
toshiba_acpi            8454  0 
pcmcia_rsrc            10566  1 yenta_socket
agpgart                32011  2 drm,intel_agp
cfg80211              144694  2 zd1211rw,mac80211
i2c_algo_bit            5168  1 i915
soundcore                880  1 snd
pcmcia_core            14657  3 pcmcia,yenta_socket,pcmcia_rsrc
hid                    67742  2 hid_logitech,usbhid
snd_page_alloc          7120  2 snd_intel8x0,snd_pcm
psmouse                59033  0 
video                  18712  1 i915
serio_raw               4022  0 
output                  1883  1 video
shpchp                 29886  0 
lp                      7342  0 
parport                31492  3 ppdev,parport_pc,lp
e100                   30356  0 
mii                     4425  1 e100
Module                  Size  Used by
aes_i586                7280  2 
aes_generic            26875  1 aes_i586
binfmt_misc             6599  1 
snd_intel8x0           25664  2 
arc4                    1165  2 
snd_usb_audio          86480  1 
snd_ac97_codec         99227  1 snd_intel8x0
ac97_bus                1014  1 snd_ac97_codec
snd_pcm                71475  3 snd_intel8x0,snd_ac97_codec,snd_usb_audio
snd_hwdep               5040  1 snd_usb_audio
snd_usbmidi_lib        17413  1 snd_usb_audio
snd_seq_midi            4588  0 
i915                  295435  3 
zd1211rw               43440  0 
snd_rawmidi            17783  2 snd_usbmidi_lib,snd_seq_midi
mac80211              231959  1 zd1211rw
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
ppdev                   5556  0 
joydev                  8767  0 
drm_kms_helper         30200  1 i915
pcmcia                 35973  0 
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   168060  3 i915,drm_kms_helper
cfg80211              144694  2 zd1211rw,mac80211
yenta_socket           21518  0 
snd                    49038  16 snd_intel8x0,snd_ac97_codec,snd_usb_audio,snd_pcm,snd_hwdep,snd_usbmidi_lib,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                59033  0 
hid_logitech            8971  0 
pcmcia_rsrc            10566  1 yenta_socket
pcmcia_core            14657  3 pcmcia,yenta_socket,pcmcia_rsrc
serio_raw               4022  0 
intel_agp              26566  2 i915
ff_memless              4393  1 hid_logitech
parport_pc             26058  1 
snd_page_alloc          7120  2 snd_intel8x0,snd_pcm
shpchp                 29886  0 
i2c_algo_bit            5168  1 i915
soundcore                880  1 snd
video                  18712  1 i915
agpgart                32011  2 drm,intel_agp
toshiba_acpi            8454  0 
output                  1883  1 video
lp                      7342  0 
parport                31492  3 ppdev,parport_pc,lp
usbhid                 36882  1 hid_logitech
hid                    67742  2 hid_logitech,usbhid
e100                   30356  0 
mii                     4425  1 e100


HTH!

---

### Post by KeesM on 2011-05-29
For me, it happens when I switch from another logged-in Ubuntu user to myself. Login goes OK, but then, when building the screen, I already see in the system monitor I have running in the top panel the amount of memory going up due to Skype trying to start. Memory goes to 100% for some 20..30 seconds, and then Skype dies, making the system responsive again.

It does not seem to happen when I start Skype manually (and also does not happen always). Don't see anything special in logs, but also don't really know what to look for.

For the moment, no auto-start for Skype...

---

