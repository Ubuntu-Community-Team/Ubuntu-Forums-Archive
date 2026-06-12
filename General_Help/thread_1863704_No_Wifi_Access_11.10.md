---
title: "No Wifi Access 11.10"
date: 2011-10-18
forum: General Help
---

### Post by Jo.Buntu on 2011-10-18
Issues with Broadcom wireless card on a DV4.... Any suggestions?


Here is the jockey log file:

```
2011-10-18 01:22:25,297 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
```

---

### Post by westie457 on 2011-10-18
> **Jo.Buntu said:**
> Issues with Broadcom wireless card on a DV4.... Any suggestions?


Here is the jockey log file:

```
2011-10-18 01:22:25,297 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
```

Hi, any idea which particular B43xx chip? Post the output of ```
lspci -vnn
``` please.

And for good measure ```
lshw -C network

rfkill list all
``` 
If others are needed you will be asked.

Thank you.

---

### Post by Jo.Buntu on 2011-10-18
> **westie457 said:**
> Hi, any idea which particular B43xx chip? Post the output of ```
lspci -vnn
``` please.

And for good measure ```
lshw -C network

rfkill list all
```If others are needed you will be asked.

Thank you.

```
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
    Subsystem: Hewlett-Packard Company Device [103c:30f7]
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07) (prog-if 00 [VGA controller])
    Subsystem: Hewlett-Packard Company Device [103c:30f7]
    Flags: bus master, fast devsel, latency 0, IRQ 47
    Memory at d0000000 (64-bit, non-prefetchable) [size=4M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 60f0 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 07)
    Subsystem: Hewlett-Packard Company Device [103c:30f7]
    Flags: bus master, fast devsel, latency 0
    Memory at d5400000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>

00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03) (prog-if 00 [UHCI])
    Subsystem: Hewlett-Packard Company Device [103c:30f7]
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 60c0 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03) (prog-if 00 [UHCI])
    Subsystem: Hewlett-Packard Company Device [103c:30f7]
    Flags: bus master, medium devsel, latency 0, IRQ 17
    I/O ports at 60a0 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03) (prog-if 20 [EHCI])
    Subsystem: Hewlett-Packard Company Device [103c:30f7]
    Flags: bus master, medium devsel, latency 0, IRQ 18
    Memory at da504c00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:30f7]
    Flags: bus master, fast devsel, latency 0, IRQ 48
    Memory at da500000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00005000-00005fff
    Memory behind bridge: d9500000-da4fffff
    Prefetchable memory behind bridge: 00000000d0400000-00000000d13fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.2 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 [8086:2944] (rev 03) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: d8500000-d94fffff
    Prefetchable memory behind bridge: 00000000d1400000-00000000d23fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.3 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 [8086:2946] (rev 03) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: d7500000-d84fffff
    Prefetchable memory behind bridge: 00000000d2400000-00000000d33fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.4 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 [8086:2948] (rev 03) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: d6500000-d74fffff
    Prefetchable memory behind bridge: 00000000d3400000-00000000d43fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.5 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 [8086:294a] (rev 03) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=07, sec-latency=0
    I/O behind bridge: 00001000-00001fff
    Memory behind bridge: d5500000-d64fffff
    Prefetchable memory behind bridge: 00000000d4400000-00000000d53fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03) (prog-if 00 [UHCI])
    Subsystem: Hewlett-Packard Company Device [103c:30f7]
    Flags: bus master, medium devsel, latency 0, IRQ 20
    I/O ports at 6080 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03) (prog-if 00 [UHCI])
    Subsystem: Hewlett-Packard Company Device [103c:30f7]
    Flags: bus master, medium devsel, latency 0, IRQ 22
    I/O ports at 6060 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03) (prog-if 00 [UHCI])
    Subsystem: Hewlett-Packard Company Device [103c:30f7]
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 6040 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03) (prog-if 20 [EHCI])
    Subsystem: Hewlett-Packard Company Device [103c:30f7]
    Flags: bus master, medium devsel, latency 0, IRQ 20
    Memory at da504800 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=08, subordinate=08, sec-latency=32
    Capabilities: <access denied>

00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:30f7]
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt

00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03) (prog-if 01 [AHCI 1.0])
    Subsystem: Hewlett-Packard Company Device [103c:30f7]
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 45
    I/O ports at 60e8 [size=8]
    I/O ports at 60fc [size=4]
    I/O ports at 60e0 [size=8]
    I/O ports at 60f8 [size=4]
    I/O ports at 6020 [size=32]
    Memory at da504000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:30f7]
    Flags: medium devsel, IRQ 11
    Memory at da505000 (64-bit, non-prefetchable) [size=256]
    I/O ports at 6000 [size=32]
    Kernel modules: i2c-i801

02:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:137f]
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at d8500000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel modules: ssb

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:30f7]
    Flags: bus master, fast devsel, latency 0, IRQ 46
    I/O ports at 3000 [size=256]
    Memory at d2410000 (64-bit, prefetchable) [size=4K]
    Memory at d2400000 (64-bit, prefetchable) [size=64K]
    Expansion ROM at d2420000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

04:00.0 System peripheral [0880]: JMicron Technology Corp. SD/MMC Host Controller [197b:2382]
    Subsystem: Hewlett-Packard Company Device [103c:30f7]
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at d6500300 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

04:00.2 SD Host controller [0805]: JMicron Technology Corp. Standard SD Host Controller [197b:2381] (prog-if 01)
    Subsystem: Hewlett-Packard Company Device [103c:30f7]
    Flags: fast devsel, IRQ 16
    Memory at d6500200 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel modules: sdhci-pci

04:00.3 System peripheral [0880]: JMicron Technology Corp. MS Host Controller [197b:2383]
    Subsystem: Hewlett-Packard Company Device [103c:30f7]
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at d6500100 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: jmb38x_ms
    Kernel modules: jmb38x_ms

04:00.4 System peripheral [0880]: JMicron Technology Corp. xD Host Controller [197b:2384]
    Subsystem: Hewlett-Packard Company Device [103c:30f7]
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at d6500000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
```

```
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:d8500000-d8503fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:23:5a:46:37:e9
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=192.168.1.137 latency=0 multicast=yes port=MII speed=100Mbit/s
       resources: irq:46 ioport:3000(size=256) memory:d2410000-d2410fff memory:d2400000-d240ffff memory:d2420000-d243ffff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
```

```
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

---

### Post by westie457 on 2011-10-18
I knew I had forgotten one.```
lsmod
``` This will tell us which driver you are using if you are not 100% sure of the one installed.

Only running checks atm until the installed driver is identified, then the solution will come.

---

### Post by Jo.Buntu on 2011-10-18
> **westie457 said:**
> I knew I had forgotten one.```
lsmod
``` This will tell us which driver you are using if you are not 100% sure of the one installed.

Only running checks atm until the installed driver is identified, then the solution will come.
Here you go

```
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55577  1 vfat
usb_storage            44173  1 
uas                    17699  0 
parport_pc             32114  0 
ppdev                  12849  0 
rfcomm                 38408  0 
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep
snd_hda_codec_hdmi     31426  1 
snd_hda_codec_idt      60049  1 
joydev                 17393  0 
hp_wmi                 13652  0 
snd_hda_intel          28358  2 
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
sparse_keymap          13658  1 hp_wmi
snd_pcm                80468  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  505143  3 
psmouse                63474  0 
serio_raw              12990  0 
snd                    55902  14 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
jmb38x_ms              17406  0 
drm_kms_helper         32889  1 i915
binfmt_misc            17292  1 
memstick               15857  1 jmb38x_ms
drm                   196322  4 i915,drm_kms_helper
soundcore              12600  1 snd
wmi                    18744  1 hp_wmi
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13199  1 i915
ir_lirc_codec          12770  0 
lirc_dev               18700  1 ir_lirc_codec
video                  18908  1 i915
ir_sony_decoder        12493  0 
ir_jvc_decoder         12490  0 
ir_rc6_decoder         12490  0 
rc_rc6_mce             12454  0 
ir_rc5_decoder         12490  0 
ir_nec_decoder         12490  0 
ene_ir                 18214  0 
rc_core                25797  9 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,rc_rc6_mce,ir_rc5_decoder,ir_nec_decoder,ene_ir
hp_accel               21632  0 
lis3lv02d              19280  1 hp_accel
input_polldev          13648  1 lis3lv02d
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
r8169                  47200  0 
ahci                   21634  2 
libahci                25761  1 ahci
sdhci_pci              13658  0 
sdhci                  27360  1 sdhci_pci

```

---

### Post by westie457 on 2011-10-18
Very strange, there is no wireless driver that I can see listed in lsmod. Have you tried the STA driver that gets installed via Additional Drivers? Which driver did you use in 11.04? In theory the one used in 11.04 should work in 11.10.

The info in this link [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx) exactly describes and guides the correct driver you should be using.

Any problems post back here then we start experimenting without breaking anything.

---

### Post by Jo.Buntu on 2011-10-18
> **westie457 said:**
> Very strange, there is no wireless driver that I can see listed in lsmod. Have you tried the STA driver that gets installed via Additional Drivers? Which driver did you use in 11.04? In theory the one used in 11.04 should work in 11.10.

The info in this link [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx) exactly describes and guides the correct driver you should be using.

Any problems post back here then we start experimenting without breaking anything.
This is a fresh install of 11.1 with no prior versions

This may help better than attempting to explain:

[http://img684.imageshack.us/img684/6109/screenshotat20111018032.png](http://img684.imageshack.us/img684/6109/screenshotat20111018032.png)

---

### Post by westie457 on 2011-10-18
From what I can see in your screenie you might be having issues with a server.

Keep your cable connected.


Open Software Centre go to Edit > Software Sources. In the first tab make sure the top 4 boxes are checked and in the 'Download from' box choose a different server. Close that window then type in your password. After that has finished in the Search Box type in 'bcm', you will get a list of all the available drivers for Broadcom chips. Start with installing the top one. Each time you try one unplug the cable and reboot. Click on the Network icon. Will look like a piece of pie if wireless networks are detected and not connected and will have lines in if connected. If the drop down menu says something like Firmware missing try a different driver. When networks are detected click on yours and enter information as necessary, this should then connect automatically on every start up.

Every time a driver does not work uninstall it then try the next. It is not always necessary to reboot after an un-install but is necessary on a driver install.

These instructions are probably as clear as mud.

---

