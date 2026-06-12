---
title: "Extremely Slow Firefox"
date: 2012-02-19
forum: General Help
---

### Post by ibrrfarr on 2012-02-19
Machine:  Compaq Presario CQ-57
OS:  Ubuntu 11.10

[CENTER][SIZE=2]Overview

[/SIZE][LEFT]Firefox is *painfully slow*; so slow that the average load time for gmail from click of button to load to display of mail is around 8 seconds or more.  If a site has video forget it.  It never buffers completely and is choppy the whole time.  Windows 7 runs fine and without issues.  So, this is a Ubuntu issue.  I would appreciate any help here and will post any test(s) requested.  Thank you.
[/LEFT]


[SIZE=3]LSPCI

[/SIZE][/CENTER]
president@OffGridOps:~$ lspci -v
00:00.0 Host bridge: Advanced Micro Devices [AMD] Family 14h Processor Root Complex
    Subsystem: Advanced Micro Devices [AMD] Family 14h Processor Root Complex
    Flags: bus master, 66MHz, medium devsel, latency 32

00:01.0 VGA compatible controller: ATI Technologies Inc Device 9804 (prog-if 00 [VGA controller])
    Subsystem: Hewlett-Packard Company Device 3577
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at 80000000 (32-bit, prefetchable) [size=256M]
    I/O ports at 4000 [size=256]
    Memory at 90400000 (32-bit, non-prefetchable) [size=256K]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx_updates, radeon

00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] (prog-if 01 [AHCI 1.0])
    Subsystem: Hewlett-Packard Company Device 3577
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
    I/O ports at 4118 [size=8]
    I/O ports at 4124 [size=4]
    I/O ports at 4110 [size=8]
    I/O ports at 4120 [size=4]
    I/O ports at 4100 [size=16]
    Memory at 90449000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
    Subsystem: Hewlett-Packard Company Device 3577
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at 90448000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
    Subsystem: Hewlett-Packard Company Device 3577
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
    Memory at 90447000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 42)
    Subsystem: Hewlett-Packard Company Device 3577
    Flags: 66MHz, medium devsel
    Kernel driver in use: piix4_smbus
    Kernel modules: sp5100_tco, i2c-piix4

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
    Subsystem: Hewlett-Packard Company Device 3577
    Flags: bus master, slow devsel, latency 32, IRQ 16
    Memory at 90440000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
    Subsystem: Hewlett-Packard Company Device 3577
    Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40) (prog-if 01 [Subtractive decode])
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=64

00:14.5 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI2 Controller (prog-if 10 [OHCI])
    Subsystem: Hewlett-Packard Company Device 3577
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at 90446000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:15.0 PCI bridge: ATI Technologies Inc SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=05, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: 90300000-903fffff
    Prefetchable memory behind bridge: 0000000090000000-00000000900fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:15.1 PCI bridge: ATI Technologies Inc SB700/SB800/SB900 PCI to PCI bridge (PCIE port 1) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Prefetchable memory behind bridge: 0000000090100000-00000000901fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:15.3 PCI bridge: ATI Technologies Inc SB900 PCI to PCI bridge (PCIE port 3) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
    Memory behind bridge: 90200000-902fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:16.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
    Subsystem: Hewlett-Packard Company Device 3577
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at 90445000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:16.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
    Subsystem: Hewlett-Packard Company Device 3577
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
    Memory at 90444000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 (rev 43)
    Flags: fast devsel

00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1
    Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2
    Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3
    Flags: fast devsel
    Capabilities: <access denied>
    Kernel driver in use: k10temp
    Kernel modules: k10temp

00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4
    Flags: fast devsel

00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6
    Flags: fast devsel

00:18.6 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5
    Flags: fast devsel

00:18.7 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7
    Flags: fast devsel

02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader (rev 01)
    Subsystem: Hewlett-Packard Company Device 3577
    Flags: bus master, fast devsel, latency 0, IRQ 20
    Memory at 90300000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: rts_pstor
    Kernel modules: rts_pstor

06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
    Subsystem: Hewlett-Packard Company Device 3577
    Flags: bus master, fast devsel, latency 0, IRQ 43
    I/O ports at 2000 [size=256]
    Memory at 90104000 (64-bit, prefetchable) [size=4K]
    Memory at 90100000 (64-bit, prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

07:00.0 Network controller: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe
    Subsystem: Hewlett-Packard Company Device 1636
    Flags: bus master, fast devsel, latency 0, IRQ 23
    Memory at 90200000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: rt2800pci
    Kernel modules: rt2800pci

[CENTER][SIZE=3]IFCONFIG

[/SIZE][LEFT][SIZE=3][SIZE=1][/SIZE][/SIZE]president@OffGridOps:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 44:1e:a1:c6:da:ec  
          inet addr:192.168.254.2  Bcast:192.168.254.255  Mask:255.255.255.0
          inet6 addr: fe80::461e:a1ff:fec6:daec/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:53421 errors:0 dropped:0 overruns:0 frame:0
          TX packets:62679 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:29761854 (29.7 MB)  TX bytes:49259444 (49.2 MB)
          Interrupt:43 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:169 errors:0 dropped:0 overruns:0 frame:0
          TX packets:169 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:17424 (17.4 KB)  TX bytes:17424 (17.4 KB)

[CENTER][SIZE=3]LSMOD

[/SIZE][LEFT][SIZE=3][SIZE=1][/SIZE][/SIZE]president@OffGridOps:~$ lsmod
Module                  Size  Used by
parport_pc             32114  0 
ppdev                  12849  0 
vesafb                 13489  1 
rfcomm                 38408  0 
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep
joydev                 17393  0 
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
snd_hda_codec_realtek   254125  1 
snd_hda_intel          24262  2 
snd_hda_codec          91859  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
uvcvideo               67271  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
videodev               85626  1 uvcvideo
arc4                   12473  2 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
rt2800pci              18340  0 
rt2800lib              48909  1 rt2800pci
crc_ccitt              12595  1 rt2800lib
rt2x00pci              14202  1 rt2800pci
rt2x00lib              48146  3 rt2800pci,rt2800lib,rt2x00pci
psmouse                73673  0 
mac80211              393459  3 rt2800lib,rt2x00pci,rt2x00lib
serio_raw              12990  0 
snd                    55902  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
k10temp                12990  0 
cfg80211              172427  2 rt2x00lib,mac80211
binfmt_misc            17292  1 
rts_pstor             353227  0 
eeprom_93cx6           12653  1 rt2800pci
sp5100_tco             13495  0 
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i2c_piix4              13093  0 
video                  18908  0 
wmi                    18744  1 hp_wmi
fglrx                2756852  143 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
r8169                  43104  0 
ahci                   21634  2 
libahci                25727  1 ahci

[/LEFT]
[/CENTER]
[/LEFT]
[/CENTER]

---

### Post by tomsn2 on 2012-02-19
Is download and upload slow as well on a speed test?  What are your DNS settings?  I didn't see that in your post.  DNS could cause this problem in my opinion.  Try setting it to Cisco 4.2.2.2 as a test and see if that changes page load speeds.

---

### Post by mardybear on 2012-02-19
> **ibrrfarr said:**
> 
Firefox is *painfully slow*; so slow that the average load time for gmail from click of button to load to display of mail is around 8 seconds or more.  If a site has video forget it.  It never buffers completely and is choppy the whole time.  Windows 7 runs fine and without issues.  So, this is a Ubuntu issue.  I would appreciate any help here and will post any test(s) requested.  Thank you.


Howdy.

Me thinks in the 1970s it took something like 20 minutes to send a 1-page fax...now 8 seconds seems like forever :(

I noticed my Ubuntu system was really slow following the most recent kernel 'upgrade'. You might want to reboot your system and select an older kernel from the grub boot menu to see if this makes a difference. Maybe something in the new kernel isn't agreeable with your system/hardware. Worth a try anyway...

Good luck,

mardybear

---

### Post by ibrrfarr on 2012-02-19
Ping:  161
Download:  2.57 Mbps
Upload:  0.37 Mbps
Latency:  192ms
Provider:  Frontier Communications

[CENTER]Background

[LEFT]I had to represent myself and sue Frontier just to get ADSL out here ([http://offgridops.org/?cat=24](http://offgridops.org/?cat=24)).  So, the speeds are pretty much written in stone.  I never really had this issue until I ran up 11.10.  Additionally, the Windows7 desktop does not function at the same slow level.  There are several other quirks which may or may not contribute to the overall situation:  a) periodic freezes when attempting to do tasks such as move in and out of programs; and b) when running Google Chrome there is no ability to see the status update of files being uploaded into Gmail (that's why I had to go back to Firefox).

Chrome actually seemed to be a bit faster than Firefox and with that said perhaps I need to be looking at a new browser, I don't know.  What I do know is that I fundamentally believe that there is an issue somewhere in the OS or perhaps my browser about:config settings and I really don't understand either one nor how to get the proper data for those whom do understand.

I am ultimately hoping to eventually upgrade to the 12.04 LTS one day as I feel far more comfortable with a LTS.  That is a while down the road, though, and as I already have one bug issued on launchpad ([https://bugs.launchpad.net/~president-6]("https://bugs.launchpad.net/%7Epresident-6")) I am trying to get 11.10 ironed out both for myself and for documentation purposes.

I thank anyone for helping me on this issue.
[/LEFT]
[/CENTER]

---

