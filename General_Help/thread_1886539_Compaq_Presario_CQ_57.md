---
title: "Compaq Presario CQ 57"
date: 2011-11-25
forum: General Help
---

### Post by ibrrfarr on 2011-11-25
I just purchased a Compaq Presario CQ 57 at the Wal Mart Black Friday sale.  I am hoping to install Ubuntu 11.x on it.  I have had success in the past with Acer and eMachines and am hoping to get some decent feedback and/or advice before I press forward.  Mainly, I an worried about [http://ubuntuforums.org/showthread.php?t=1873823&highlight=compaq+cq57 ]("http://ubuntuforums.org/showthread.php?t=1873823&highlight=compaq+cq57")which seems to say there is an issue with the wireless drivers.  I have an ethernet cable I can run; however, the wireless is obviously extremely important.

I look forward to any input any and all may have as I would like to preemptively troubleshoot any issues and Google keeps kicking this thread and its offspring all over the place and not much else.

Thanks for reading!

---

### Post by ibrrfarr on 2011-11-30
So, I was bummed that there wasn't ***one*** comment here about anything dealing with this thread.  Had I been a noob I probably would've thrown in the towel and said, "Hey, if no one has the time to even tell me that they don't have a clue or at least point me to a thread what business do I have here?"  With that said, Ubuntu 11.10 is up and running without any problems.  The OS is a bit draggy and locks up quitea bit; however, that is Ubuntu and not the laptop.  I will post all the features and how they perform on my next post in about an hour.  

I guess for those gurus whom scan the posts to 'clear' a system for Ubuntu you can give this laptop a Grade A+ for accepting Ubuntu as I have had no issues.

*** After the fact:  Obviously, there is a problem with the OS or the laptop.  Still awaiting a single reply a week after the fact.  05DEC11 1725EST  New grade B-

---

### Post by giddy1945 on 2011-12-04
ibrrfarr, I am also bummed on this issue.  I have searched and searched.  I have spent many hours, days!  You have gone to the trouble of posting, yet you get no response.  I have the same laptop, and I tried that version.  The freezing prompted me to just let 11.10 cook a while.

---

### Post by ibrrfarr on 2011-12-05
> **giddy1945 said:**
> ibrrfarr, I am also bummed on this issue.  I have searched and searched.  I have spent many hours, days!  You have gone to the trouble of posting, yet you get no response.  I have the same laptop, and I tried that version.  The freezing prompted me to just let 11.10 cook a while.

I am having HORRIBLE freezing issues as well!  I have to restart the computer at least six (06) times on any given business eight hour day.  I guess it's OS related and am gonna downgrade to 10.10 soon.

Now, seven (07) days later the wireless has quit working.  This is simply not acceptable.  I am very disappointed in 11.10.  I normally don't talk too much about the forums here; however, as there are many high level folks on here I am going to say that I am disillusioned now.  This is a classic example of a properly established thread, tags and all.  And it appears that the only two (02) folks on here are those with issues.  If Ubuntu and it's participating membership hope to ever have a viable OS for those of us in the business community then it would behoove those in power and/or control to chime in.  If for no other reason than to say, "Hey, just stopping by and wondered if there were any issues."

I mean 11.10 is a newer OS so I expect a bug or two, but how can the powers that be on this forum even pretend to 'clear' hardware as Ubuntu certified (so to speak) if they do not even have a vetting process in play?  Then, if the lag for reply is soooooo long that the OS glitch has either repaired itself or the OS has been moved along to a new version, the post is moot.

Look, Compaq is a mainstream computer company.  For those on this forum whom are obviously talented and proficient to bury their heads in the sand and refuse to offer assistance is rather reprehensible.  If, though, the new trend is to force inexperienced folks like myself and others to pony up money to hire Ubuntu programmers to talk to and/or fix stuff I will not be using the OS nor will I continue to recommend it to others in the financial community.

VERY DISGRUNTLED!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by ibrrfarr on 2011-12-05
Three (03) tests below.  LSPCI, IFCONFIG and IFCFIG WAN. Tell me what others you want.  Additionally, wireless worked from stick and is listed in the Internet Profile window (or whatever you want to call it).  It stopped working seven (07) days ago and yes, the wireless light is lit up.  Modem is SAGECOM SE657.


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
    Kernel driver in use: radeon
    Kernel modules: radeon

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

president@OffGridOps:~$ ifconfig wlan0 up
SIOCSIFFLAGS: Permission denied
president@OffGridOps:~$ sudo ifconfig wlan0 up
[sudo] password for president: 
SIOCSIFFLAGS: Operation not possible due to RF-kill
president@OffGridOps:~$ 

president@OffGridOps:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 44:1e:a1:c6:da:ec  
          inet addr:192.168.254.6  Bcast:192.168.254.255  Mask:255.255.255.0
          inet6 addr: fe80::461e:a1ff:fec6:daec/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17045 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24241 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6320341 (6.3 MB)  TX bytes:20597732 (20.5 MB)
          Interrupt:43 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1560 (1.5 KB)  TX bytes:1560 (1.5 KB)

---

### Post by ibrrfarr on 2011-12-05
lspci -nnk lsmod uname -a rfkill list iwconfig ifconfig -a cat /etc/network/interfaces


president@OffGridOps:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12617  0 
nls_cp437              12751  0 
vfat                   17308  0 
fat                    55577  1 vfat
parport_pc             32114  0 
ppdev                  12849  0 
snd_hda_codec_realtek   254125  1 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
joydev                 17393  0 
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
snd_hda_intel          24262  2 
arc4                   12473  2 
snd_hda_codec          91754  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
rt2800pci              18340  0 
snd_pcm                80468  2 snd_hda_intel,snd_hda_codec
rt2800lib              48909  1 rt2800pci
crc_ccitt              12595  1 rt2800lib
rt2x00pci              14202  1 rt2800pci
rt2x00lib              48114  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              393459  3 rt2800lib,rt2x00pci,rt2x00lib
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              172392  2 rt2x00lib,mac80211
psmouse                73673  0 
serio_raw              12990  0 
k10temp                12990  0 
eeprom_93cx6           12653  1 rt2800pci
radeon                925094  4 
snd                    55902  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ttm                    65224  1 radeon
rts_pstor             353227  0 
soundcore              12600  1 snd
drm_kms_helper         32889  1 radeon
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
sp5100_tco             13495  0 
drm                   192226  6 radeon,ttm,drm_kms_helper
i2c_piix4              13093  0 
wmi                    18744  1 hp_wmi
i2c_algo_bit           13199  1 radeon
binfmt_misc            17292  1 
video                  18908  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
usb_storage            44173  0 
uas                    17699  0 
r8169                  43104  0 
ahci                   21634  2 
libahci                25727  1 ahci

president@OffGridOps:~$ uname -a
Linux OffGridOps 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:25:36 UTC 2011 i686 athlon i386 GNU/Linux

[FONT=monospace]president@OffGridOps:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

president@OffGridOps:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off


president@OffGridOps:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 44:1e:a1:c6:da:ec  
          inet addr:192.168.254.6  Bcast:192.168.254.255  Mask:255.255.255.0
          inet6 addr: fe80::461e:a1ff:fec6:daec/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:26934 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36118 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12260758 (12.2 MB)  TX bytes:21980205 (21.9 MB)
          Interrupt:43 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:36 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2880 (2.8 KB)  TX bytes:2880 (2.8 KB)

wlan0     Link encap:Ethernet  HWaddr 38:59:f9:98:d4:2d  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

president@OffGridOps:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

president@OffGridOps:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


president@OffGridOps:~$ lspci -nnk
00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 14h Processor Root Complex [1022:1510]
    Subsystem: Advanced Micro Devices [AMD] Family 14h Processor Root Complex [1022:1510]
00:01.0 VGA compatible controller [0300]: ATI Technologies Inc Device [1002:9804]
    Subsystem: Hewlett-Packard Company Device [103c:3577]
    Kernel driver in use: radeon
    Kernel modules: radeon
00:11.0 SATA controller [0106]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] [1002:4391]
    Subsystem: Hewlett-Packard Company Device [103c:3577]
    Kernel driver in use: ahci
    Kernel modules: ahci
00:12.0 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
    Subsystem: Hewlett-Packard Company Device [103c:3577]
    Kernel driver in use: ohci_hcd
00:12.2 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
    Subsystem: Hewlett-Packard Company Device [103c:3577]
    Kernel driver in use: ehci_hcd
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 42)
    Subsystem: Hewlett-Packard Company Device [103c:3577]
    Kernel driver in use: piix4_smbus
    Kernel modules: sp5100_tco, i2c-piix4
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383] (rev 40)
    Subsystem: Hewlett-Packard Company Device [103c:3577]
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller [1002:439d] (rev 40)
    Subsystem: Hewlett-Packard Company Device [103c:3577]
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384] (rev 40)
00:14.5 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI2 Controller [1002:4399]
    Subsystem: Hewlett-Packard Company Device [103c:3577]
    Kernel driver in use: ohci_hcd
00:15.0 PCI bridge [0604]: ATI Technologies Inc SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0) [1002:43a0]
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:15.1 PCI bridge [0604]: ATI Technologies Inc SB700/SB800/SB900 PCI to PCI bridge (PCIE port 1) [1002:43a1]
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:15.3 PCI bridge [0604]: ATI Technologies Inc SB900 PCI to PCI bridge (PCIE port 3) [1002:43a3]
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:16.0 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
    Subsystem: Hewlett-Packard Company Device [103c:3577]
    Kernel driver in use: ohci_hcd
00:16.2 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
    Subsystem: Hewlett-Packard Company Device [103c:3577]
    Kernel driver in use: ehci_hcd
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 [1022:1700] (rev 43)
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1 [1022:1701]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2 [1022:1702]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3 [1022:1703]
    Kernel driver in use: k10temp
    Kernel modules: k10temp
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4 [1022:1704]
00:18.5 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6 [1022:1718]
00:18.6 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5 [1022:1716]
00:18.7 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7 [1022:1719]
02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader [10ec:5209] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:3577]
    Kernel driver in use: rts_pstor
    Kernel modules: rts_pstor
06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Hewlett-Packard Company Device [103c:3577]
    Kernel driver in use: r8169
    Kernel modules: r8169
07:00.0 Network controller [0280]: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe [1814:5390]
    Subsystem: Hewlett-Packard Company Device [103c:1636]
    Kernel driver in use: rt2800pci
    Kernel modules: rt2800pci

[/FONT][FONT=monospace]

[/FONT]

---

### Post by praseodym on 2011-12-05
Try to install this driver:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms patch fakeroot unzip
wget http://media.cdn.ubuntu-de.org/forum/attachments/3208747/angepasster-2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO.zip
unzip angepasster-2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO.zip
cd angepasster-2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/
sudo make
sudo make install
sudo modprobe -rfv rt2800pci
sudo depmod -a
sudo update-initramfs -u 
sudo modprobe -v rt5390sta
echo "blacklist rt2800pci" | sudo tee /etc/modprobe.d/blacklist-rt2800pci.conf
```
Check:

```
lsmod
iwconfig
rfkill list
sudo iwlist scan
```

---

### Post by ibrrfarr on 2011-12-05
Thank you very much for your attention to this thread!  As requested:

president@OffGridOps:~$ lsmod
Module                  Size  Used by
rt5390sta            1287707  0 
nls_iso8859_1          12617  0 
nls_cp437              12751  0 
vfat                   17308  0 
fat                    55577  1 vfat
parport_pc             32114  0 
ppdev                  12849  0 
snd_hda_codec_realtek   254125  1 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
joydev                 17393  0 
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
snd_hda_intel          24262  2 
arc4                   12473  0 
snd_hda_codec          91754  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73673  0 
serio_raw              12990  0 
k10temp                12990  0 
radeon                925094  4 
snd                    55902  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ttm                    65224  1 radeon
rts_pstor             353227  0 
soundcore              12600  1 snd
drm_kms_helper         32889  1 radeon
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
sp5100_tco             13495  0 
drm                   192226  6 radeon,ttm,drm_kms_helper
i2c_piix4              13093  0 
wmi                    18744  1 hp_wmi
i2c_algo_bit           13199  1 radeon
binfmt_misc            17292  1 
video                  18908  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
usb_storage            44173  0 
uas                    17699  0 
r8169                  43104  0 
ahci                   21634  2 
libahci                25727  1 ahci
president@OffGridOps:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  
          
president@OffGridOps:~$ rfkill list
1: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
president@OffGridOps:~$ sudo iwlist sca
[sudo] password for president: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ra0       Interface doesn't support scanning : Network is down

---

### Post by praseodym on 2011-12-05
Any button/switch/key(s)/key combination to press once or permanently or repeatedly during boot-up? Tried

```
sudo rfkill unblock all
```

---

### Post by ibrrfarr on 2011-12-05
> **praseodym said:**
> Any button/switch/key(s)/key combination to press once or permanently or repeatedly during boot-up? Tried

```
sudo rfkill unblock all
```

No special key combos to press during start up.  Just rebooted.  Still the same.  Called provider and no ISP issues.  Tested W*indows laptop w/o issue.

---

### Post by ibrrfarr on 2011-12-05
OK.  We have success.  I used XChat to goto #Ubuntu and found [https://wiki.ubuntu.com/josephmills](https://wiki.ubuntu.com/josephmills)  Here's the deal:  Apparently, at least with my laptop (and perhaps others), you have a special key to activate the wireless.  In the case of the CQ57 it is the f12 key.  No ctrl/alt/fn --- NO SPECIAL KEY IN ADDITION --- just press the f12.  Now, in my case the blue light in the right hand corner of the f12 **always** stays on.  I believe that however Ubuntu moves forward, this quirk, [COLOR=Red]**_*MUST BE FIXED*_**[/COLOR][COLOR=Black]!!!!!  It erroneously causes the operator to believe that the wireless is on.

Now, I followed all the earlier stuff recommended; however, was it that or a combination of my depressing the f12 to reactivate the wireless I do not know.  I believe that it was simply the need to depress the f12 key.  Also, you may have to either press it a bunch or simply be patient as 11.10 seems to be a draggy OS and sometimes it seems to work and sometimes it may be lag time I don't know.  You will be happy that once you key it up it stays on after reboot.  No need to press it again unless you don't have signal and then you might have accidentally hit it and need to restart it.  This goes back to the fact that Ubuntu needs to get the blue light bug fixed.

Look, I have taken the time to put this thread together.  I am in HOPES that someone higher than me will get this in the area it needs to be and get the data on the blue light to whomever handles it.

The OS is still draggy, but that is a different thread.  I will periodically report back to this thread to advise when I put the bug into the system.
[/COLOR]

---

### Post by DapperMe17 on 2011-12-05
Remember that Ubuntu is a free & open-source alternative to Win, Mac, or other. It is you're choice to try it on your PC.  

Attempting to drop your problems into the hands of others to fix, is an egregious decision. 

Your copy of Ubuntu was free, as is the service help that you've received from the kind folks here. 

Since it was your choice to try the free OS and ask for free help, you should consider taking a moment to give something back in return for free, and fill out a bug report so that other's may benefit from your experiences with Ubuntu.

Now, wouldn't that make more sense to you?

---

### Post by ibrrfarr on 2011-12-05
> **DapperMe17 said:**
> Remember that Ubuntu is a free & open-source alternative to Win, Mac, or other. It is you're choice to try it on your PC.  

Attempting to drop your problems into the hands of others to fix, is an egregious decision. 

Your copy of Ubuntu was free, as is the service help that you've received from the kind folks here. 

Since it was your choice to try the free OS and ask for free help, you should consider taking a moment to give something back in return for free, and fill out a bug report so that other's may benefit from your experiences with Ubuntu.

Now, wouldn't that make more sense to you?

Well, such elitist comments always make me brim with joy!  The bug report was filed:  [https://bugs.launchpad.net/ubuntu/+bug/900594](https://bugs.launchpad.net/ubuntu/+bug/900594)

Your presumptuous attitude is something that I rarely encounter on here, but as it has reared it head I will address it.  Constructive criticism is something that allows others to grow within a community.  That is why I voiced my disappointment as did another fellow.  As a matter of fact there are **multiple** threads dealing with this issue.  However, at no point whatsoever (the one person whom did post on here did at my behest via me contacting through PM) did anyone even comment.  So, for me to document this and state that it might be a good idea to get some input from others whom are far more educated than I makes pretty good sense.

Posting the bug:  Hmnn, did you read in the thread JUST ABOVE yours that I stated I would post it as soon as I finished?!  Yeah, well now you have the precise area as you jumped the gun.

Free:  yeah, it's free as is the support on here.  I have a few posts on here and have common sense.  Granted Cannonical is making money and donations come into the forum; however, withstanding that no one owes me anything.  Likewise, I believe it is my right, as a member in good standing of this community, to voice my opinion about lack of input without assaultive commenting as a direct result.  Or perhaps not?!

I take **great** offense to your insinuations and innuendos which, at first blush, smack as condensation.  Had I been a simple person I probably would've left and given up and especially after your post.  See, that's the deal:  Elitist attitudes towards folks voicing opinions will place Ubuntu in a precarious position moving forward.  I do foreclosure work here in the US and thus work directly for most of the financial institutions and the US Government.  Make no mistake I support Ubuntu and try to move it along as best I can.  If, though, as you seem to be saying, freedom to voice opinion and question is not tolerated then the major players in the world will never bring it in as an OS.  Perhaps, though, that is what you want.

---

### Post by DapperMe17 on 2011-12-05
=;

---

### Post by malspa on 2011-12-06
I'm quite late in seeing this thread (unfortunately, that's how things go at these forums, sometimes), and I don't really have a lot of info to offer, but I bought a Compaq Presario CQ 56 (not CQ 57, though) a little while back. Also from Walmart. I've been running 11.04 on it and everything seems fine. None of the freezing that you mentioned, except it was was quite sluggish booting the 11.04 live CD, and using the live CD to install went quite slowly. However, I didn't have the same problem with a Mepis 11 live DVD.

I did try a few different live sessions from flash drives, and those all worked fine.

I don't use wireless, so can't comment on that.

I understand that it isn't the exact same model but hopefully it'll end up working out for you. I thought it was a good deal, but I kinda wish that I could have waited for the model you got, would have saved me about $50 bucks, I think. Best of luck!

Oh, yeah, don't be too hard on folks that are tying to help you here; nobody's getting paid for it. Don't flame me for saying that, though. Hope that machine works out for ya.

---

### Post by garyed on 2011-12-06
I also purchased a CQ57 at Walmart about a month ago.
I loaded Ubuntu & Lubuntu 11.10 with very few problems. 
I did have a problem with the wifi F12 button not working when I was out of town & found something interesting about it. Even booting Windows 7 showed the wireless switch disabled & I couldn't get it working. A guy got it working for me by going into the HP tools software in Windows. I missed what he did but there is some software that is used along with the button to activate or deactivate th

---

### Post by garyed on 2011-12-06
Sorry, double post

---

### Post by ibrrfarr on 2011-12-06
I don't want to get too far off topic here, but I suppose I should comment a bit on the evolution of the topic first and then the CQ57.  As to the evolution:  I am ex military.  I suppose that after my hitch doing intel I see the world from a different point-of-view.  I am a dye-in-the-wool a**hole as my Mrs. likes to call me.  I generally call on the carpet issues immediately as in the war it cost lives.  Software has *always* been a critical component in my field and the *rigidity* of my background probably drives how I speak ... or I am just and a**hole?! :)  Look, when I look at Ubuntu what I see is the future.  Not just for those of us whom like to tinker and dream, but the future for folks like my 2 year old son.  I also see the safety of my Nation as in an OS wherein our power, water and communications grids could be impervious to cyber attack.  Finally, as I do foreclosure work, I see the ability for both myself and other contractors in the property preservation business to become far more productive.  I predict Ubuntu will eventually become the OS of not just tablets, but most 21st Century devices.  With that said, it requires a community which is both fluid (as opposed to static) and willing to tackle its own pitfalls.  Constructive criticism is paramount to success.  With that said, the post which started this is water under the bridge.  My opinion will not change nor his; I respect his right to state his as I fought and was wounded for it, neither one of us are completely correct.  Let us, though, steer this back to where it needs to be:  the CQ57.

I am in hopes that a moderator will be able to move this into whatever area it needs to be so that we use this thread to by-in-large *clear* the CQ57 for mainstream use.  After all, that is the question I originally posited.  What I need, though, is guidance as to precisely what kind of tests I need to put her through.  I believe the more units we prove to be field tested the closer we are, as a community, to showing Ubuntu as a viable, out-of-the-box OS.  So, I encourage and implore those of you here whom know how to contact a moderator or whatever to get the thread moved to the proper area (if it is not there yet).  

Some background notes:


[LIST]
[*]DVD Player works out of the box
[*]WiFi keys up automatic and properly stores the dataset
[*]Compiz w/rotate cube works great
[*]Cairo Dock works great
[*]All the function keys native to the 57 seem to perform their duties EXCEPT the f12
[*]USB and SD Card readers all perform out of the box
[*]Server Edition working great (using it for MediaWiki on localhost)
[*]No excess fan running that I can tell
[*]RAM at 25% (mainly from Firefox)
[*]CPU1 at 6%; CPU2 at 1%
[*]SWAP at 0%
[/LIST]
I simply don't know what else is important to those of you who are able to use this data.  So, if y'all will define the mission I will secure the objective.  Ach, too much military speak there.  Simply tell me what data to provide and thanks to each and all, including DapperMe17.  With 600+ posts I could learn quite a bit from you as well!  

**[COLOR=Red]SCREENSHOT OF SENSORS ATTACHED[/COLOR]**

---

### Post by ibrrfarr on 2011-12-06
> **malspa said:**
> I'm quite late in seeing this thread (unfortunately, that's how things go at these forums, sometimes), and I don't really have a lot of info to offer, but I bought a Compaq Presario CQ 56 (not CQ 57, though) a little while back. Also from Walmart. I've been running 11.04 on it and everything seems fine. None of the freezing that you mentioned, except it was was quite sluggish booting the 11.04 live CD, and using the live CD to install went quite slowly. However, I didn't have the same problem with a Mepis 11 live DVD.

I did try a few different live sessions from flash drives, and those all worked fine.

I don't use wireless, so can't comment on that.

I understand that it isn't the exact same model but hopefully it'll end up working out for you. I thought it was a good deal, but I kinda wish that I could have waited for the model you got, would have saved me about $50 bucks, I think. Best of luck!

Oh, yeah, don't be too hard on folks that are tying to help you here; nobody's getting paid for it. Don't flame me for saying that, though. Hope that machine works out for ya.

Wanted to comment on the "...saving $50 bucks..."  The only reason that the price was lower was that it was Black Friday.  So, anyone interested in this model needs to check the current price as I am sure it has gone up and that is presuming all WalMart's still carry it.

---

### Post by malspa on 2011-12-06
> **ibrrfarr said:**
> Wanted to comment on the "...saving $50 bucks..."  The only reason that the price was lower was that it was Black Friday.  So, anyone interested in this model needs to check the current price as I am sure it has gone up and that is presuming all WalMart's still carry it.

Yeah, understood.

> **ibrrfarr said:**
> I believe the more units we prove to be field tested the closer we are, as a community, to showing Ubuntu as a viable, out-of-the-box OS.

I'd say that Ubuntu can be a viable, out-of-the-box distro -- but a lot depends on the hardware you're running it on. It may or may not be the best distro for the CQ57, and for wireless on that machine.

Seems to me that the thing about Linux, generally, is setting up the right environment for it to run in. This was a point that someone mentioned to me when I first started out with Linux, and (for me) it turned out to be an important one.

You've got so many different types of hardware and it isn't always easy getting Linux to run on every type of computer, ya know? I just don't think it's ever gonna happen where you can take one particular distro and it's gonna work out perfectly on any computer you install it on.

Also, from what I've seen, wireless continues to be somewhat of an issue for many Linux users. Hoping you can get that straightened out.

> **ibrrfarr said:**
> The OS is a bit draggy and locks up quite a bit; however, that is Ubuntu and not the laptop.

Regarding that, I am wondering if the system is more responsive if you're running GNOME Shell instead of Unity. Or if you've had the opportunity to run it with something lighter (I've got Openbox installed in Ubuntu 10.04 -- quite snappy!).

---

### Post by ibrrfarr on 2011-12-06
> **malspa said:**
> 

I'd say that Ubuntu can be a viable, out-of-the-box distro -- but a lot depends on the hardware you're running it on. It may or may not be the best distro for the CQ57, and for wireless on that machine.

Seems to me that the thing about Linux, generally, is setting up the right environment for it to run in. This was a point that someone mentioned to me when I first started out with Linux, and (for me) it turned out to be an important one.

You've got so many different types of hardware and it isn't always easy getting Linux to run on every type of computer, ya know? I just don't think it's ever gonna happen where you can take one particular distro and it's gonna work out perfectly on any computer you install it on.



In some ways I agree; however, even W*ndows needs tweaking no matter where it's applied.  Also, when you look at hardware a lot of it is simply geared towards Bill and his Evil Empire.  As Ubuntu evolves and becomes more mainstream I believe that hardware manufacturers will work more with Ubuntu.  The natural progression will eventually be Cloud computing say in 3 - 5 years.  With servers already geared with Apache, Perl, etc. Ubuntu seems a natural fit.

In addressing the CQ57 I believe that when we look at precisely how massive an amount of coding is involved in the OS, having only **one** glitch is beyond remarkable!  I consider Ubuntu and excellent fit.

---

### Post by bmike1 on 2011-12-06
I got that computer and everything worked after I upgraded to th 3.1.4 kernel. Then I put a 64bit o/s on the computer and it didn't like that. Now I can't get things right again. So frustrating!

---

### Post by ibrrfarr on 2011-12-06
> **bmike1 said:**
> I got that computer and everything worked after I upgraded to th 3.1.4 kernel. Then I put a 64bit o/s on the computer and it didn't like that. Now I can't get things right again. So frustrating!

If you are within the US pm me and I will shoot my telephone number (Verizon) and see if I can help you.  Other than that the best thing I would suggest is reinstall and bring it back to the level where it worked.

---

### Post by ibrrfarr on 2011-12-06
This is from:  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/900594](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/900594)

This documents my bug and discussions with some fellow from launchpad and someone else with a Cannonical email who asked me to reinstall a new kernel.


Ok, here's how it goes:  I dumped 12.04 onto USB and fired it up off of USB.  Now, other than the purple screen, the Man, the Wireless Icon and System nothing happened other than asking me if I wanted to install or run off disk.  I checked English and ran off disk.

The red light was constant when I was not online and the blue light was on when I was online.  I cycled this three (03) or (04) times with the same results.  I never accessed the Internet, though, as all it did was sync my wireless device, but as I know the name and had to enter the password I presume it is doing what it is supposed to.

What I would respectfully request, as I have taken the time to do all this, is an explanation IN LAYMAN'S terms, how to take the piece from 12.04 and put it on my system and make it stay throughout updates.  Fair trade off I believe.

If y'all need other stuff done let me know.  I will be gone from 1630EST - 1930EST +/- and will check back then.

---

### Post by bmike1 on 2011-12-06
The freezing issues are taken care off by upgrading to the 3.1.4 kernel

---

### Post by bmike1 on 2011-12-06
My wireless just stopped working too.... upon googling it it seems windows users have this issue too.

---

### Post by praseodym on 2011-12-06
Did you reinstall the VGA driver after upgrading the kernel?

---

### Post by bmike1 on 2011-12-06
No. How do you do that?

---

### Post by bmike1 on 2011-12-06
>I did have a problem with the wifi F12 button not working when I was out  of town & found something interesting about it. 
>Even booting  Windows 7 showed the wireless switch disabled & I couldn't get it  working. A guy got it working for me by 
>going into the HP tools software  in Windows. I missed what he did but there is some software that is  used along with the 
>button to activate or deactivate th

How do yo do this through Linux? I blew Windows7 away.

---

### Post by bmike1 on 2011-12-06
>the best thing I  would suggest is reinstall and bring it back to the level where it  worked.

I tried to.... about 6 times now. It got to the point where I was hard-rebooting and it wouldn't let me choose my kernel and the screen would jusr be black.

---

### Post by bmike1 on 2011-12-07
I wish I could say I thought of this. It didn't work but I should of thought of this.

bmike1@Michaels-Laptop ~ $ sudo ifconfig wlan0 up
[sudo] password for bmike1: 
SIOCSIFFLAGS: Operation not possible due to RF-kill
bmike1@Michaels-Laptop ~ $

---

### Post by bmike1 on 2011-12-07
I just googled the error and a solution to the problem was presented '(rfkill unblock all) when I issued the command it issued no errors but still the wifi doesn't work.

---

### Post by bmike1 on 2011-12-07
I ran your command and the apt ran with no problems. But when I trtied to run make:

bmike1@Michaels-Laptop ~ $ sudo make
make: *** No targets specified and no makefile found.  Stop.

Do I need to change directories?

> **praseodym said:**
> Try to install this driver:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms patch fakeroot unzip
wget http://media.cdn.ubuntu-de.org/forum/attachments/3208747/angepasster-2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO.zip
unzip angepasster-2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO.zip
cd angepasster-2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/
sudo make
sudo make install
sudo modprobe -rfv rt2800pci
sudo depmod -a
sudo update-initramfs -u 
sudo modprobe -v rt5390sta
echo "blacklist rt2800pci" | sudo tee /etc/modprobe.d/blacklist-rt2800pci.conf
```Check:

```
lsmod
iwconfig
rfkill list
sudo iwlist scan
```

---

### Post by praseodym on 2011-12-07
Yes:

cd angepasster-2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/

---

### Post by ibrrfarr on 2011-12-07
> **praseodym said:**
> Yes:

cd angepasster-2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/

I wanted to jump in here.  Perhaps we need to post the link to what is going on so that others may *precisely* follow, step-by-step, what is going on.  I followed your instructions and the packages are still in my machine; however, I do not know if it was them or simply the fact that I needed to depress the f12 as it was showing a false read from the blue light.

There are two (02) things in play here I think we all need to remember.  First, this thread is **specific** to the Compaq Presario CQ57 --- now, the hardware may be identical to other machines so in a bit I will break down the hardware piece-by-piece.  The other thing is that whatever I have done in *my *case seems to work other than the fact that the f12 key still displays the false read by and through the blue light.

If someone could jump in and tell me:  a) how to install the 3.4 kernel I will; b) what tests they need displayed; and c) I think we should remove the angepasster stuff out *before* I do anything.  What I am driving at is that I feel we need a baseline to go forward from.  That way we can logically rule out what is and is not causing the wireless to work.

I thank each and all for contributing to this thread as how it is going now is how I always felt it should be as we now have a flowing record for folks above my paygrade (old military saying) to look at and say, "Hey, for the next LTS this is what we need to do."

---

### Post by praseodym on 2011-12-07
Imho the problem are the original Ralink drivers, which cannot be build with kernel 3.x so far?! But here the client uses 10.10, which should work with this stick with the module rt2870sta or the driver rt3070sta

---

### Post by bmike1 on 2011-12-07
> **praseodym said:**
> Yes:

cd angepasster-2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/
  I 
I updatedb->locate angepasster

It didn't find anything on my system with that sequence in it. 

```
wget http://media.cdn.ubuntu-de.org/forum/attachments/3208747/angepasster-2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO.zip unzip angepasster-2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO.zip cd angepasster-2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/ 
```The computer doesn't like it all together so I ran each command individually. Unfortunately when I got to the unzio command it replied:
```
no zipfiles found
```but when I look at the file through the GUI there is a packaged file there which I can (and do) unpack.
```

bmike1@Michaels-Laptop ~/Programs/angepasster (for wifi)/angepasster-2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO $ sudo make
make -C tools
make[1]: Entering directory `/home/bmike1/Programs/angepasster (for wifi)/angepasster-2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/bmike1/Programs/angepasster (for wifi)/angepasster-2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/tools'
/home/bmike1/Programs/angepasster (for wifi)/angepasster-2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/tools/bin2h
/bin/sh: Syntax error: word unexpected (expecting ")")
make: *** [build_tools] Error 2
```

---

### Post by praseodym on 2011-12-07
Linux sometimes doesnt like blanks in paths:

> /home/bmike1/Programs/[COLOR="Red"]angepasster (for wifi)[/COLOR]/angepasster-2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/tools
So change the folder name and try it again. I tried it here in 10.04 and the compilation worked flawlessly.

---

### Post by bmike1 on 2011-12-07
I did.
```
bmike1@Michaels-Laptop ~/Programs/angepasster-(for- wifi)/angepasster-2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO $ make
make -C tools
make[1]: Entering directory `/home/bmike1/Programs/angepasster-(for-wifi)/angepasster-2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/bmike1/Programs/angepasster-(for-wifi)/angepasster-2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/tools'
/home/bmike1/Programs/angepasster-(for-wifi)/angepasster-2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/tools/bin2h
/bin/sh: Syntax error: word unexpected (expecting ")")
make: *** [build_tools] Error 2

```

---

### Post by bmike1 on 2011-12-07
I know it looks as if there is a space :
(for- wifi)
but there isn't. I just changed it to 'forWifi' to make sure but I get the same error.

---

### Post by praseodym on 2011-12-07
Still one blank:

> angepasster-[COLOR="Red"](for- wifi)[/COLOR]
Try it also without brackets:
> /bin/sh: Syntax error: word unexpected (expecting [COLOR="Red"]")"[/COLOR])

---

### Post by bmike1 on 2011-12-07
[QUOTE=ibrrfarr;11520117
If someone could jump in and tell me:  a) how to install the 3.4 kernel I will;[/QUOTE]

My advise: If you aren't having issues don't upgrade. I had Linux running flawlessly on my CQ57 when I first installed it. Then I upgraded to a 64 bit version of the O/S. When I didn't like it and put the 32bit o/s is when my troubles began. I've reinstalled the o/s at least 5 times and most of the installs are different. If you do choose to upgrade the kernel you might need to reinstall your graphics card and someone else will have to help you with that.

---

### Post by bmike1 on 2011-12-07
okay..... I got it to make and install and all of the rest of your lines. What is that suppossed to do?

---

### Post by bmike1 on 2011-12-07
I an absolutely frustrated..... time to reinstall.

I stuck the live disk in and... presto..... wifi came up.

---

### Post by praseodym on 2011-12-07
Please test with Live-CD:

```
lsmod
iwconfig
rfkill list
sudo iwlist scan
iwlist chan
dmesg | egrep 'rt2|rt5'
```
and after reboot from the installed system, too.

---

### Post by bmike1 on 2011-12-07
well.... I missed the message not to reinstall until after It was done.... so now I am back to the original problem of it crashing while on battery power. But I know how to fix that: upgrade to the 3.1.4 kernel. So I look for the place to get the kernel ([http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/")) So I down load kernel 3.1.4 headrs files and image file for my processor and unpack them in a certain order: 
```
*all.deb
*headers*i386.deb
*image*
```open a terminal and type:
```
sudo update-grub
```
then you reboot... and now my computer is happily running the 3.1.4 kernel! I just hope it doesn't start to crash.

and that's how you install a prepackaged kernel

You know.... I always thought I had a bad install that last time. Thanks for all the help you guys have given to me.

---

### Post by garyed on 2011-12-07
> **bmike1 said:**
> >I did have a problem with the wifi F12 button not working when I was out  of town & found something interesting about it. 
>Even booting  Windows 7 showed the wireless switch disabled & I couldn't get it  working. A guy got it working for me by 
>going into the HP tools software  in Windows. I missed what he did but there is some software that is  used along with the 
>button to activate or deactivate th

How do yo do this through Linux? I blew Windows7 away.

Good question.
I was getting ready to post that same question before I saw this thread.
Its a good thing I kept Windows 7 on the machine because I couldn't get the wifi button to turn on in Linux.

---

### Post by ibrrfarr on 2011-12-07
> **bmike1 said:**
> well.... I missed the message not to reinstall until after It was done.... so now I am back to the original problem of it crashing while on battery power. But I know how to fix that: upgrade to the 3.1.4 kernel. So I look for the place to get the kernel ([http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/")) So I down load kernel 3.1.4 headrs files and image file for my processor and unpack them in a certain order: 
```
*all.deb
*headers*i386.deb
*image*
```open a terminal and type:
```
sudo update-grub
```then you reboot... and now my computer is happily running the 3.1.4 kernel! I just hope it doesn't start to crash.

and that's how you install a prepackaged kernel

You know.... I always thought I had a bad install that last time. Thanks for all the help you guys have given to me.

So, just to clarify:  For your situation (and you have the same laptop as the title of this thread) by installing the 3.1.4 kernel solved all the wireless issues?

president@OffGridOps:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
president@OffGridOps:~$ cat /etc/issue
Ubuntu 11.10 \n \l
president@OffGridOps:~$ uname -a
Linux OffGridOps 3.1.4-030104-generic #201111281851 SMP Mon Nov 28 23:59:58 UTC 2011 i686 athlon i386 GNU/Linux

 president@OffGridOps:~$ lsmod
Module                  Size  Used by
rfcomm                 37609  0 
bnep                   17749  2 
bluetooth             153182  10 rfcomm,bnep
parport_pc             32006  0 
ppdev                  12900  0 
snd_hda_codec_realtek   239668  1 
joydev                 17313  0 
snd_hda_intel          23931  2 
binfmt_misc            17258  1 
snd_hda_codec          92814  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                75935  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25103  1 snd_seq_midi
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51256  2 snd_seq_midi,snd_seq_midi_event
psmouse                69062  0 
snd_timer              24609  2 snd_pcm,snd_seq
snd_seq_device         14130  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               66560  0 
radeon                935377  4 
videodev               90267  1 uvcvideo
snd                    55680  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
k10temp                12951  0 
serio_raw              13024  0 
soundcore              12600  1 snd
ttm                    64680  1 radeon
snd_page_alloc         14036  2 snd_hda_intel,snd_pcm
sp5100_tco             13456  0 
i2c_piix4              13079  0 
drm_kms_helper         32653  1 radeon
video                  18792  0 
drm                   191907  6 radeon,ttm,drm_kms_helper
rts_pstor             351870  0 
i2c_algo_bit           13152  1 radeon
wmi                    18645  1 hp_wmi
lp                     13349  0 
parport                36664  3 parport_pc,ppdev,lp
usbhid                 45614  0 
hid                    81147  1 usbhid
r8169                  47038  0 
ahci                   21524  2 
libahci                25841  1 ahci
president@OffGridOps:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

president@OffGridOps:~$ rfkill list
0: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: no



Also, although the blue light went from blue to red, the wireless is shut off.  I am going to go and redo the other stuff from earlier in the thread and report back.

---

### Post by ibrrfarr on 2011-12-07
After installing all the stuff I had priorly, no wireless.  So, the new kernel does not do much for me.  I am going to wait a bit and then reinstall.


president@OffGridOps:~$ lsmod
Module                  Size  Used by
bnep                   17749  2 
rfcomm                 37609  0 
bluetooth             153182  10 bnep,rfcomm
parport_pc             32006  0 
ppdev                  12900  0 
binfmt_misc            17258  1 
snd_hda_codec_realtek   239668  1 
snd_hda_intel          23931  2 
snd_hda_codec          92814  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                75935  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25103  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51256  2 snd_seq_midi,snd_seq_midi_event
radeon                935377  4 
snd_timer              24609  2 snd_pcm,snd_seq
joydev                 17313  0 
snd_seq_device         14130  3 snd_seq_midi,snd_rawmidi,snd_seq
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
ttm                    64680  1 radeon
snd                    55680  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         32653  1 radeon
drm                   191907  6 radeon,ttm,drm_kms_helper
sp5100_tco             13456  0 
uvcvideo               66560  0 
soundcore              12600  1 snd
videodev               90267  1 uvcvideo
snd_page_alloc         14036  2 snd_hda_intel,snd_pcm
i2c_piix4              13079  0 
video                  18792  0 
rts_pstor             351870  0 
psmouse                69062  0 
serio_raw              13024  0 
rt5390sta            1287707  0 [permanent]
i2c_algo_bit           13152  1 radeon
wmi                    18645  1 hp_wmi
k10temp                12951  0 
lp                     13349  0 
parport                36664  3 parport_pc,ppdev,lp
usbhid                 45614  0 
hid                    81147  1 usbhid
r8169                  47038  0 
ahci                   21524  2 
libahci                25841  1 ahci
president@OffGridOps:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  
          
president@OffGridOps:~$ rfkill list
0: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
president@OffGridOps:~$

---

### Post by ibrrfarr on 2011-12-07
After a brand new install with only updates added this is the info:


president@OffGridOps:~$ lsmod
Module                  Size  Used by
rfcomm                 38408  0 
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep
parport_pc             32114  0 
ppdev                  12849  0 
vesafb                 13489  1 
binfmt_misc            17292  1 
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
joydev                 17393  0 
arc4                   12473  2 
snd_hda_codec_realtek   254125  1 
rt2800pci              18340  0 
rt2800lib              48909  1 rt2800pci
crc_ccitt              12595  1 rt2800lib
rt2x00pci              14202  1 rt2800pci
rt2x00lib              48114  3 rt2800pci,rt2800lib,rt2x00pci
snd_hda_intel          24262  2 
mac80211              393459  3 rt2800lib,rt2x00pci,rt2x00lib
snd_hda_codec          91754  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  2 snd_hda_intel,snd_hda_codec
hp_wmi                 13652  0 
snd_seq_midi           13132  0 
fglrx                2595570  97 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
cfg80211              172392  2 rt2x00lib,mac80211
rts_pstor             353227  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
sparse_keymap          13658  1 hp_wmi
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
eeprom_93cx6           12653  1 rt2800pci
psmouse                73673  0 
serio_raw              12990  0 
snd                    55902  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
video                  18908  0 
k10temp                12990  0 
wmi                    18744  1 hp_wmi
soundcore              12600  1 snd
sp5100_tco             13495  0 
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i2c_piix4              13093  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
r8169                  43104  0 
ahci                   21634  2 
libahci                25727  1 ahci
president@OffGridOps:~$ clear

president@OffGridOps:~$ lsmod
Module                  Size  Used by
rfcomm                 38408  0 
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep
parport_pc             32114  0 
ppdev                  12849  0 
vesafb                 13489  1 
binfmt_misc            17292  1 
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
joydev                 17393  0 
arc4                   12473  2 
snd_hda_codec_realtek   254125  1 
rt2800pci              18340  0 
rt2800lib              48909  1 rt2800pci
crc_ccitt              12595  1 rt2800lib
rt2x00pci              14202  1 rt2800pci
rt2x00lib              48114  3 rt2800pci,rt2800lib,rt2x00pci
snd_hda_intel          24262  2 
mac80211              393459  3 rt2800lib,rt2x00pci,rt2x00lib
snd_hda_codec          91754  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  2 snd_hda_intel,snd_hda_codec
hp_wmi                 13652  0 
snd_seq_midi           13132  0 
fglrx                2595570  99 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
cfg80211              172392  2 rt2x00lib,mac80211
rts_pstor             353227  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
sparse_keymap          13658  1 hp_wmi
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
eeprom_93cx6           12653  1 rt2800pci
psmouse                73673  0 
serio_raw              12990  0 
snd                    55902  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
video                  18908  0 
k10temp                12990  0 
wmi                    18744  1 hp_wmi
soundcore              12600  1 snd
sp5100_tco             13495  0 
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i2c_piix4              13093  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
r8169                  43104  0 
ahci                   21634  2 
libahci                25727  1 ahci
president@OffGridOps:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

[B]president@OffGridOps:~$ rfkill list
0: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no[/B]

president@OffGridOps:~$ sudo iwlist scan
[sudo] password for president: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

 
So, in the morning I will probably reinstall the other stuff and report back as I am pretty tired.  At least we now have a baseline.

---

### Post by bmike1 on 2011-12-08
Yeah... I have the same computer as you. I got mine at the black friday sale too. Can' t beat the price! ($189 It normally goes for $458 )You say your wireless is down? The upgrade of the kernel stopped my system from panicing. I'll find out soon if it does the same thing this time around! <looks as if it did> The reinstall got my wireless back up. Try pressing the wireless button multiple times to see if that gets it back up.

In the next post you are told to delete a file. If I were you I would rename it  to something else in case you need it later.
   
sudo rm /etc/modprobe.d/blacklist-hp.conf

I think should rather be:

sudo mv /etc/modprobe.d/blacklist-hp.conf   /etc/modprobe.d/blacklist-hp.conf  .old

 or whatever you want to call it/wherever you want to put it

---

### Post by praseodym on 2011-12-08
Hi ibrrfarr,

try to blacklist the module hp_wmi:

```
echo "blacklist hp_wmi" | sudo tee /etc/modprobe.d/blacklist-hp.conf
```
and reboot. Check after that
```
sudo rfkill unblock all
rfkill list
iwconfig
lsmod
```
If nothing works, delete the file via
```
sudo rm /etc/modprobe.d/blacklist-hp.conf
```
With kernel 3.1.4 and the module rt5370sta
```
sudo rfkill unblock all
```
should break the "soft block"

---

### Post by bmike1 on 2011-12-08
I think something happened to my video driver. This may or may not be related but I tried to update my driver to the proprietary one (FGLRX) but the instalation failed. Then a little later  I was playing with xrandr. I entered:```
xrandr --output LVDS --mode 1366x768 refresh 75
``` and it didn't do anything. (i figured out what I was looking for was:```
xrandr -s 1366x768
```) In any case then I rebooted and x was dead. This is what happens:
1- start the computer
2- option to enter BIOS appears
2a-if  do nothing screen goes black with power to it for about 20 seconds
2b- upon restart it gives you a choice of kernels to start with
2b1-if you choose the 3.1.4 screen goes blank then if you press F1 some text appears 
      then disappears (upon restart I find most of the text is what follows) 
      then more text appears (something about virtual box and stuff that 
      disappears to quick) then the screen goes blank. Sometimes I have
      to go through the process again  but sometimes I press F1 and text appears:

a         [     9.300411] SP5100  TCO  timer:mmio address 0xb80430 already in use
b         [   11.853316] Bad LUN  (0:1)
d         [   11.853871] Bad target number (1:0)
e         [   11.854556] Bad target number (2:0)
f          [   11.855076] Bad target number (3:0)
g         [   11.855629] Bad target number (4:0)
h         [   11.856440] Bad target number (5:0)
i          [   11.856917] Bad target number (6:0)
j          [   11.856763] Bad target number (7:0)
k           *Stopping anac(h)ronistic cron                          l            [OK]
m          *Starting CPU interrupts balancing daemon                    [OK]
n           *Stopping save kernel messages                                  [OK]

then the screen goes blank and if I hit F1 I get lines a-j (the numbers in the brackets do change each time I see them.) and the login screen. If I login and 'startx' the screen blacks out and I am unable to do anything. not even go to tty1-6
[IMG]https://mail.google.com/mail/images/cleardot.gif[/IMG]

---

### Post by bmike1 on 2011-12-08
now the stupid kernel only boots into recovery mode!
 if I go to the GUI tty (F7) I see this text:

*Stopping save kernel messages
*starting bluetooth
*pulseaudio configured for per-user sessions
saned disable; edit /etc/default/saned
fsck from util-linux 2.19.1
/dev/sda1: clean, 190511/15163392 files, 2045963/60628992 blocks
initctl: event failed
* starting mdns/dns-sd daemon
* starting network connection manager
* starting cups printing spooler/server
speech-dispatcher disabled; edit /etc/default/speech-dispatcher
checking for running unattended-upgrades:
* stopping failsafe boot delay
* stopping system v initialisation compatibility
* starting system v runlevel compatibility
* starting lightdm display manager
* starting acpi daemon
* starting anac(h)ronistic cron
* starting save kernel messages
* starting regular  background program processing daemon
* starting deferred execution scheduler
* starting starting automatic crash report generation
* starting cpu interrupts balancing daemon

---

### Post by praseodym on 2011-12-08
You mean fglrx? Try to reinstall the stuff:

```
sudo apt-get install --reinstall linux-image-$(uname -r) linux-headers-$(uname -r) build-essential dkms fglrx
```
Reboot

---

### Post by bmike1 on 2011-12-08
it says it can't reinstall my linux headers and image. it says it can't download them.

<perhaps because it is kernel3.1.4>

it ran the rest of the command but that didn't fix anything

---

### Post by praseodym on 2011-12-08
Where did you save the .deb-files? Boot in an earlier kernel and try:

```
sudo dpkg -i /path/to/files/linux-*.deb
```

---

### Post by bmike1 on 2011-12-08
after doing as instructed in tty1 I typed 'shutdown now'  and it said thaat modemmanager was starting. then it said modem manager could not get the system bus. then I had to hard-reboot as all my ttys froze. I could not login to another tty (I didn't try tty7 <GUI>). In any case.... x is still not running.

hmmm.... I wonder. When I just rebooted I noticed my wifi stayed off until the following text scrolled by:
```

starting network connection manager
```I wonder if that has anything to do with the wifi issue.

I just rebooted again and noticed 
```
init ctrl event failed
```What is that? Could this have something to do with our problems?

I don't know if this helps with anything but my video is as an AMD Radeon HD 6310.

---

### Post by garyed on 2011-12-08
I'm listening to all these problems you're having & I'm wondering if my CQ57 I got at Walmart last month is different than yours. Everything in mine has worked out of the box with Ubuntu 11.10: 3.0.0-12-generic 32 bit kernel & Lubuntu 11.10 64 bit. I even got Puppy Lucid working fine after installing the Realtek wireless driver. The only issue I've had is with the F12/wifi button. Just a thought but what about the possibility of downloading Ubuntu again & burning another iso. It may be a waste of time but with all the time spent so far what have you got to lose.

---

### Post by bmike1 on 2011-12-08
I think I found a solution today for the video issue but am unsure what to do. I found it here:
[http://forums.amd.com/forum/messageview.cfm?catid=390&threadid=145785](http://forums.amd.com/forum/messageview.cfm?catid=390&threadid=145785)


This is what it says:


Got it working(OpenCL and X11), turns out AMD posted the Linux driver for HD 6XXX today :-)
 Here are some rough notes for Fedora 14:
 #get ATI driver for E350/Zacate Radeon HD 6310 
support.amd.com
  Desktop->HD Radeon->6XXX driver->x86_64 Linux
sh ati-driver-installer-x11-1-x86.x86_64.run
cd /lib/modules/fglrx
sh make.install.sh
modprobe fglrx
init 3
killall -9 Xorg
aticonfig --initialize
init 5

#get AMD APP / ATI Stream API
tar xzf ati-stream-sdk-v2.3-lnx64.tgz
cd ati-stream-sdk-v2.3-lnx64
#edit make/openclsdkdefs.mk:
  OpenCL -> OpenCL GL GLU
make
export LD_LIBRARY_PATH=`pwd`/lib/x86_64
execstack -c lib/x86_64/libatiocl64.so
cd samples/opencl/bin/x86_64
./MatrixMultiplication


I went to:
[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English)
hmmmm..... I can't get lynx to open that page!
so I opened the download link page:
[http://www2.ati.com/drivers/linux/ati-driver-installer-11-11-x86.x86_64.run](http://www2.ati.com/drivers/linux/ati-driver-installer-11-11-x86.x86_64.run) and downloaded the driver 



How do I unpack a .run file? the file is ati-driver-installer-11-11-x86.x86_64.run

---

### Post by praseodym on 2011-12-08
It is there:
> sh ati-driver-installer-x11-1-x86.x86_64[COLOR="Red"].run[/COLOR]

---

### Post by ibrrfarr on 2011-12-08
> **praseodym said:**
> Hi ibrrfarr,

try to blacklist the module hp_wmi:

```
echo "blacklist hp_wmi" | sudo tee /etc/modprobe.d/blacklist-hp.conf
```

OK.  Now I initially typed sudo rfkill unblock all and nothing happened.  Then I entered the line above and I am back to having wifi with the blue lights on.  So, I am curious what, in layman's terms, does this statement do?  Is there any easy explanation?  Also, I am going to report on Launchpad what has happened and that you were instrumental in the fix.  I am kinda the lab rat and you are administering medicine! :P

Is it safe for me to go ahead, now, and add all my normal bells and whistles?!

---

### Post by ibrrfarr on 2011-12-08
> **garyed said:**
> I'm listening to all these problems you're having & I'm wondering if my CQ57 I got at Walmart last month is different than yours. Everything in mine has worked out of the box with Ubuntu 11.10: 3.0.0-12-generic 32 bit kernel & Lubuntu 11.10 64 bit. I even got Puppy Lucid working fine after installing the Realtek wireless driver. The only issue I've had is with the F12/wifi button. Just a thought but what about the possibility of downloading Ubuntu again & burning another iso. It may be a waste of time but with all the time spent so far what have you got to lose.

As to my situation that is what I precisely did.  Now, I don't know about other folks, but I never use the same .iso twice.  I guess I am an oddity.  Mine works fine again with the command I listed above.  I think that's good advice, though, figuring the multiple times that a person runs and reruns it is eventually bound to confuse a 0 or 1 in the machine language eventually?  Ghost in the Machine as we used to say at Fort Meade.

---

### Post by bmike1 on 2011-12-09
> **garyed said:**
> I'm listening to all these problems you're having & I'm wondering if my CQ57 I got at Walmart last month is different than yours. Everything in mine has worked out of the box with Ubuntu 11.10: 3.0.0-12-generic 32 bit kernel & Lubuntu 11.10 64 bit. I even got Puppy Lucid working fine after installing the Realtek wireless driver. The only issue I've had is with the F12/wifi button. Just a thought but what about the possibility of downloading Ubuntu again & burning another iso. It may be a waste of time but with all the time spent so far what have you got to lose.

that''s the problem! I had it working great until I decided I wanted to run the 64bit animal. when I figured out the 64 bit wasn't any improvement and might even be a detriment I put the 32 bit  animal back on and everything went to hell! I just had it back to normal when I put fglrx video driver on and when I rebooted my machinethe graphics was dead. Now I hope I just need to put the video driver back in place. This new driver I'm trying to put in by AMD I don't care if I have. I just want things the way they were but I don't know how to put the original driver back on because I don't know what it is called.

---

### Post by bmike1 on 2011-12-09
I just got back from an easy day at work and I'm thinking that I'm about to get my system up again and I am so excited. I just have to find the file
So I then type updatedb and then locate ati* and hit return and it is nowhere to be found! Could someone tell me how to put the original driver back on?

Well, I found and installed the new AMD driver but got stuck with his instructions at the next step....  the one where I change directories.  it responded: no such file or directory it said.

Darn, how do you put the original driver back in?

Wait a second.... I just looked at the instructions..... this is the FGLRX driver! No wonder it doesn't work.

---

### Post by praseodym on 2011-12-09
The module/driver **hp_wmi** is responsible for the software side of the hardware keys (if any). Sometimes its buggy/just not working, so blacklisting can help. But maybe other keys dont work anymore?! You have to figure it out...

---

### Post by bmike1 on 2011-12-09
I found instructions on how  to put the catalyst driver in:
```

wget http://www2.ati.com/drivers/linux/ati-driver-installer-11-11-x86.x86_64.run

```
well I ran this but there was a  typo. I put wwww2..... accidentally. But it ran (I think) for like half a second. I didn't think that was long enough but I ran the next line anyways:
```
chmod +x ati-driver-installer-11-11-x86.x86_64.run
sh ./ati-driver-installer-11-11-x86.x86_64.run
```
 to which I got the error:
```
redirection unexpected
```
so I looked at the wget command and fixed my error but after pressing enter it resolved the host and then I got the error:
```
HTTP request sent, awaiting response... 404 not found.
```
 why did it run with the typo but not when it was corrected?

then I added the line 'blacklist hp_wmi' to the file /etc/modprobe.d/blacklist.conf and rebooted.
 and I have graphics again! Yipee. 

You have been so instrumental to getting this going again. Thanks!

---

### Post by bmike1 on 2011-12-09
you know the wireless fixed  when I reinstalled. I'm just  waiting for it to go out again. Do you think we could figure out how to  'flip the switch' (turn it on/off)   without pushing the button?

---

### Post by bmike1 on 2011-12-09
I've been googling for this but can't find the solution.  I need to  network a Mint box, Ubuntu computer, and an XP machine. I need my  brothers Windows machine and the Mint box to be able to print (the  printer is attached to the Ubuntu) without emailing the documents to be  printed to myself. Further, I want to be able to control one machines  pointer from another computer (remote desktop access). The best page I found for The best page I found for connecting Linux with XP is: [http://www.howtodothings.com/computers/ ... hines.html]("http://www.howtodothings.com/computers/a2335-how-to-connect-linux-and-xp-machines.html")
Then  it told me to enter: 'smb: //mywindowsmachinesname/ or smb:  //mywindowsmachines LAN IP/' (I went to the windows machine ran ipconfig  and figured out  the LAN IP is 192.168.0.2) into konqueror. I figured  it would be the same with firefox but it responded: '...(smb isn't  associated with any program.' so I googled more adding the term 'ubuntu'  but couldn't find anything useful. I guess you are supposed to enter  something else! Please, what is it?
Also: the page told me to 'apt-get  install cupsys cupsys-bsd cupsys-client foomatic-bin samba smbclient  gs-esp a2ps'  but apparently I don't have the source in my repository  because mint responded with the not available but referred to by another  package error.

---

### Post by ibrrfarr on 2011-12-10
> **bmike1 said:**
> I've been googling for this but can't find the solution. now I need to  network a Mint box, Ubuntu computer, and an XP machine. I need my  brothers Windows machine and the Mint box to be able to print (the  printer is attached to the Ubuntu) without emailing the documents to be  printed to myself. Further, I want to be able to control one machines  pointer from another. The best page I found for this was: [http://www.howtodothings.com/computers/ ... hines.html]("http://www.howtodothings.com/computers/a2335-how-to-connect-linux-and-xp-machines.html")
Then  it told me to enter: 'smb: //mywindowsmachinesname/ or smb:  //mywindowsmachines LAN IP/' (I went to the windows machine ran ipconfig  and figured out  the LAN IP is 192.168.0.2) into konqueror. I figured  it would be the same with firefox but it responded: '...(smb isn't  associated with any program.' so I googled more adding the term 'ubuntu'  but couldn't find anything useful. I guess you are supposed to enter  something else! Please, what is it?
Also: the page told me to 'apt-get  install cupsys cupsys-bsd cupsys-client foomatic-bin samba smbclient  gs-esp a2ps'  but apparently I don't have the source in my repository  because mint responded with the not available but referred to by another  package error.

Probably best to start a new thread on that as this one mainly deals with the CQ57.  Glad to hear we both got our stuff going though!

---

### Post by ibrrfarr on 2011-12-10
> **praseodym said:**
> The module/driver **hp_wmi** is responsible for the software side of the hardware keys (if any). Sometimes its buggy/just not working, so blacklisting can help. But maybe other keys dont work anymore?! You have to figure it out...

A final note here:  I just did a new reinstall and found it interesting that I didn't have to even do anything to the wifi.  I don't know if it is because even though it was a new install the system retained some of the old settings; I selected the option to do a complete wipe and initialization.  Odd quirk I guess.

---

### Post by garyed on 2011-12-11
I found something interesting a few minutes ago. Everything has been fine for a week until I used the computer driving in the car with no wireless reception. When I got back to the house the wireless button would stay red & not connect. Pushing the wifi button, rebooting to Ubuntu or even to Windows did not help. In Windows I went in to HP diagnostics & somehow got the F12/wifi button to turn blue & connect. Then I booted into Ubuntu & everything worked fine again. So even though the button is mechanical it must be software driven to be able to be engaged through the HP diagnostics.

---

### Post by ibrrfarr on 2011-12-11
> **garyed said:**
> I found something interesting a few minutes ago. Everything has been fine for a week until I used the computer driving in the car with no wireless reception. When I got back to the house the wireless button would stay red & not connect. Pushing the wifi button, rebooting to Ubuntu or even to Windows did not help. In Windows I went in to HP diagnostics & somehow got the F12/wifi button to turn blue & connect. Then I booted into Ubuntu & everything worked fine again. So even though the button is mechanical it must be software driven to be able to be engaged through the HP diagnostics.

It would be great if you could cut and paste this post in the bug report as it might help developers to figure out exactly what's going on.


[https://bugs.launchpad.net/ubuntu/+s...ux/+bug/900594]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/900594")

---

### Post by garyed on 2011-12-13
> **ibrrfarr said:**
> It would be great if you could cut and paste this post in the bug report as it might help developers to figure out exactly what's going on.


[https://bugs.launchpad.net/ubuntu/+s...ux/+bug/900594]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/900594")

I hate to sound stupid but I couldn't figure out how to do it. I found where I could report a new bug but I couldn't figure how to add to the existing thread.

---

### Post by ibrrfarr on 2011-12-15
> **garyed said:**
> I hate to sound stupid but I couldn't figure out how to do it. I found where I could report a new bug but I couldn't figure how to add to the existing thread.

With your permission I will simply cut and paste it along with your username.  Is that ok?

---

### Post by bmike1 on 2011-12-22
a new cq57 issue!

I  installed my new system about a month ago and as I was installing  something came up about testing the microphone (you know the bar graph  thing). SO I did and the bar graph moved as I talked so I figured all  was well with that. Anyways I never listened to the any recording (I   never made any) so I went on for a month until now. When I tried to  record something nothing played back. So, after a little research I  found alsamixer (which I started). Somehow the microphone volume got  turned all the way down. (I wonder how) Anyways, before I submitted my  recording to the website I listened to it. I could barely hear myself!  It was mainly a bunch of static. I then turned the record volume down a little but that had no effect. I Could someone enlighten me on how to  fix this issue?

I went here:
     [https://help.ubuntu.com/community/SoundTroubleshooting#Line_Input.2BAC8-Microphone_Troubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting#Line_Input.2BAC8-Microphone_Troubleshooting)
But that didn't help any! In fact  now I get static on my  speakers now which doesn't change it's volume level if I adjust the volume  until i turn it all the way down to no volume at all or select to mute  it.
I thought restarting it might get rid  of the static but it didn't. I found when I play with 'Mic Boost' in the  alsamixer that will adjust the static but if I would adjust 'internal  mic boost' it would cause no change.

In my research I found that you might need the following information:

bmike1@Michaels-Laptop ~ $ cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC270
bmike1@Michaels-Laptop ~ $ aplay -L
default
Playback/recording through the PulseAudio sound server
pulse
Playback/recording through the PulseAudio sound server
front:CARD=SB,DEV=0
HDA ATI SB, ALC270 Analog
Front speakers
surround40:CARD=SB,DEV=0
HDA ATI SB, ALC270 Analog
4.0 Surround output to Front and Rear speakers
surround41:CARD=SB,DEV=0
HDA ATI SB, ALC270 Analog
4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=SB,DEV=0
HDA ATI SB, ALC270 Analog
5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=SB,DEV=0
HDA ATI SB, ALC270 Analog
5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=SB,DEV=0
HDA ATI SB, ALC270 Analog
7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
dmix:CARD=SB,DEV=0
HDA ATI SB, ALC270 Analog
Direct sample mixing device
dsnoop:CARD=SB,DEV=0
HDA ATI SB, ALC270 Analog
Direct sample snooping device
hw:CARD=SB,DEV=0
HDA ATI SB, ALC270 Analog
Direct hardware device without any conversions
plughw:CARD=SB,DEV=0
HDA ATI SB, ALC270 Analog
Hardware device with all software conversions
bmike1@Michaels-Laptop ~ $                                                                [bmike1]("http://forums.linuxmint.com/memberlist.php?mode=viewprofile&u=71696")             Level 3
[IMG]http://forums.linuxmint.com/images/ranks/3.gif[/IMG] **Posts:** 101**Joined:** Sun Nov 27, 2011 10:13 pm

---

### Post by bmike1 on 2011-12-22
If you need to work on someone elses computer you can do it with teamviewer.
It is free for non-comercial use and I didn't have to mess with it. It just worked.

---

### Post by bmike1 on 2011-12-23
I just discovered the microphone works but there  is still a lot of static on the line; not as much as before (you can at  least hear me) but it is still there.
--edit--
I got rid of the  static. I turned both of the boosts  (Mic Boost and Internal Mic Boost)  all the way down and that took care of the static.

---

### Post by bmike1 on 2011-12-24
new issue with the microphone: I tried to do a google video chat and the guy I was talking with had difficulties hearing me. I click the speaker  (volume control) and I have the volume controls for both the speaker and the microphone. The speaker control stays constant but when I turn the microphone volume up it turns itself down as noise is made. I opened alsamixer and hit F4  and  'Mic Boost' is at zero but Capture is at three cubes and Internal Mic Boost is maxed out (I turned it down to zero). I turn Internal Mic Boost down to zero and Capture back up but when I make any noise it resets to Capture at two or three cubes and Internal Mic Boost at max. I've figured it out... someone made it so that the volume has to be at a certain level (which is too quiet to hear easily).
On a whim I went to the website that I want to leave recordings on ([http://www.livemocha.com/lessonPlan/view/l:154/e:1995](http://www.livemocha.com/lessonPlan/view/l:154/e:1995)) and it would record but wouldn't play anything back.

---

### Post by bmike1 on 2011-12-24
this  is bewildering to me,,,,,  none of the settings are ever saved, it  obviously doesn't need internal mic boost yet insists on having it  (intedrnal mic booster is setabout half yet the mic itself is at two  cubes, and if I change it it resets itself to those mentioned levels if I  speak) and why in the world will it not record to the website yet the  mic works on google chat?

Hmmm.... I just found that if I open pvaucontrol  and pavumeter the meter will be visible in the pavucontrol window under  the recording tab. I further found that there is a setting I can  manipulate that says:

PulseAudio Volume Meter: PulseAudio Volume Meter <i>from</i>
(and then I can choose) 'Monitor of Internal Analog Stereo' or 'Internal Analog Stereo'

Monitor  of Internal Audio Analog Stereo is the default and with it selected the  levels on the meter are nil but if I select the other option the meter  starts responding to my voice. I'm pretty sure this means that 'pulse'  is paying attention to the monitor rather than the actual device but I  am at a loss as to how to fix it.

---

### Post by garyed on 2011-12-24
> **ibrrfarr said:**
> With your permission I will simply cut and paste it along with your username.  Is that ok?

fine with me as long as you only use my words without any additions.

---

### Post by bmike1 on 2011-12-25
it was then suggested elsewhere that I set your mic's front left channel to  the left and the front right channel to the right[off],  with pavucontrol because the two channels  might be canceling each other out.

when I start pavucontrol the meter isn't registering sound as I make noise until.... I started pavucontrol and then in the 'recording' tab changed

 '<b>PulseAudio Volume Meter</b>: PulseAudio Volume Meter <i>from</i> Monitor of Internal Audio Analog Stereo.
to
'<b>PulseAudio Volume Meter</b>: PulseAudio Volume Meter <i>from</i> Internal Audio Analog Stereo.

Now  I will say that when I turn one of the channels down the moment I make  any noise the 'nobs' reset themselve to be equal in volume. It is as if  the volumes need to be equal. I wonder if when the mics get old if  they'll adjust themselves so that one side is louder than the other.

Another  thing is that the mic works in google chat; although the volume needs  to be louder. I click on the volume control and the microphone is there*  as well as the speakers. So I turn it up but as I make any noise it  turns itself down. It is as though there is a predetermined decibel  maximum  and you can't make any noise above that level. You can set it  below that level but if you set it above it turns itself down so that  you are at that level (the volume will only turn itself down, not up).

one more thing..... MERRY  ChRiStMaSSSSSS!

*only if I do the <b>PulseAudio Volume Meter</b> thing

---

### Post by bmike1 on 2011-12-25
> **garyed said:**
> I found something interesting a few minutes ago. Everything has been fine for a week until I used the computer driving in the car with no wireless reception. When I got back to the house the wireless button would stay red & not connect. Pushing the wifi button, rebooting to Ubuntu or even to Windows did not help. In Windows I went in to HP diagnostics & somehow got the F12/wifi button to turn blue & connect. Then I booted into Ubuntu & everything worked fine again. So even though the button is mechanical it must be software driven to be able to be engaged through the HP diagnostics.

Gary.... I had this same problem. It was suggested that I try blacklisting hp-wmi.... this is how to do that
# nano gedit /etc/modprobe.d/blacklist.conf             There you can add 'blacklist hp-wmi' to the bottom of the file and reboot.

(the '#' means you need to be root)(or append the command with 'sudo')

Later I asked about how to turn it off if this happened again and was told that it shouldn't happen again with hp_wmi blacklisted. In two weeks it hasn't happened again but who knows what will happen in the future.

---

### Post by mack-ubun on 2012-01-02
Hi there! Just to give my first contribution to the Ubuntu community by giving some feedback with the Compaq CQ57. these are the issues I had:

1) It came with W7 as default OS. The execution of the system is very poor, I think it is the hardware, therefore, the very computer. Not very good quality computer in deed.

2) Could not instal Ubuntu 11.10 as there was a conflict with the partitions. I researched the issue and, effectively, it was a problem other found. This computer seems to get hold of all the hard drive and does not allow space for Ubuntu unless you mess up with partitions which I was not so keen to do.

3) I finally decided to delete one of the drivers, one with the HP recovery solution. I used the software in the computer to do this and delete this, from my point of view, waist of space and resources.

4) Once I did that, installing Ubuntu was sooooooo easy I could not believe it! The partition was set up by Ubuntu in the unit I deleted as recovery solution. And the!!!!!! 

5) The system asked me to set up the wireless conecction. I introduced the name of the wireless network and password and, of be go, it got conected with not delay!

6) The installation went all around well and I did installed latter all upgrades!   

7) Only issue is not been able to paly HD movies, no even 720! And very poor performance with video card which can not be upgraded according t Ubuntu. 

This computer is supposed to be a dual core and the performace is even poorer than a Dell Inspiron Mini 1012 with a Atom chip! My guess is that this computer is a very poor hardware option and the final performance is at a low I never thought it could be possible.

But I must said that the installation went sooo well and it was soooo easy that my love for this OS is growing now even more. We need to give a chance to this system and try and help each other with driver's issues which is the most common problem.

Hope this helps! Happy new year to all in this community!

:o:o:o:o

---

### Post by ac4rb on 2012-01-20
Here are some of my observations and  suggestions . I am new to this forum  so if I have covered  something already covered please forgive me. While most seem to have problems with the wireless, as of now after about 20 days, I have had no problems with the wireless with the exception of not being able to install some software with it and none  without it.

	 	 	 	 	 	 	 	  Problems with Ubuntu 11.10.AMD64
 

 This was loaded on a Compaq CQ57 . This  laptop is virtually the same as the HP 2000 with the exception of the memory and hard drive size. I loaded it on a 16gb USB flash drive. The boot was also loaded on the flash drive to keep the computer in its original state. All goes well with installation it even recognized the web cam and displayed a picture of me while loading the OS. Now for my problems and recommendations. First let me explain that although I am a retired EE with some programming (Asm and C++ mostly) I still do not consider myself a computer expert by no means.
 Computers when I was educated was mostly a dream (early 1960s). My software knowledge with the exception of some classes in Assembly was mostly self taught. So please do not assume that I am right in my statements but check each out.  
  	As I see it, there was too much time used in making the graphics look good and they are very impressive, and not enough time in checking out some of the problems.  I assumed that this would be similar to the Xandros OS in that it would work “out of the box” which it don't. The programmers and people that put this package together makes too many assumptions. First they assume that the computer is connected to a high speed internet when it is being loaded. First of all, I don't even have high speed internet. About the only packaged software that works out of the box is the wireless connection and the photo displays. I could not get any of the media apps to play or run even a midi file much less a video file of any type. In order to get these to work, I had a very good friend that had high-speed wireless internet. So I did get the media to work by downloading the codecs. Next I tried to do an update, It appeared to do the thing, but alas, It too seemed only to a degree. In order to get my dial up to work I downloaded the wvdial program along with wine, ndiswrapper, and some of the suggested programs. Each one of these would appear to be loading. When I returned home and tried to set them up, none was on the system. So I took the time to download wvdial again with my old desktop box. Got the deb files and tried to load them. Now to my surprise, the darn thing told me that even though I was logged in as administrator, I didn't have the privileges to load software. After many attempts, I found that I was not the owner and couldn't make changes. I searched through the docs that came with the software and couldn't find any way to take control or ownership. This is a real crock. I tried to change permissions with no luck. Again, I was logged in as ADMINISTRATOR. I can understand having something like this in an industrial or office environment, but in a home computer? Come on now. This is outrageous.  
 	I believe this could be a great OS if the people packaging this would:
 
[LIST=1]
[*]Quit assuming that everyone has 	high-speed Intranet and try to load the OS on a new machine like I 	did without  wireless, dial-up, any internet or network.
[*]Package some codecs or at least do 	as Xandros, and have an applications CD to support what you put into 	the OS package. In other words, if you put the software in the 	package, it should have the necessary codecs, or lib files to make 	it work on at least the most popular types of music or videos. If it 	is an office suite then spelling and such should work. Again, with 	Xandros and some other distros, they do work.
[*]Fix it so a person can install a 	deb file without being connected to any kind of network. Again,do 	this on a network or internet free computer. After all, everyone 	doesn't stay connected to the internet all of the time.  	
[*]As mentioned before, while loading 	the OS it displayed a picture of me loading it, but I could not find 	any way to display the web cam picture after it was loaded. Must 	have deleted the package for it after it was loaded.  	
[*]Some of the functions that should 	work, at least it gives the impression that it will, do not work. 	For instance, I had some old unformatted CD-RWs laying around. Try 	to format one. Even though it tells you that it is unformatted and 	asks if you want to format it, it will not. The software goes 	through the whole routine, such as type of format, size, and Ect. It 	even tells you that formating will destroy any data on the disk. 	Then guess what, the software tells you it can't format the disk. 	Why didn't the software check the disk out first then decide whether 	it could or could not format the CD and tell you that  before you go 	through 4 or 5 minuets reading and deciding how to format it only to 	find you can't.
[*]To me, as this OS is, without some 	changes, is nearly worthless. I can't even get the OS to install 	programs I downloaded and put on a CD. It continues to tell me that 	it cannot connect to the Ubuntu software center every time I click 	on a deb file. In Xandros, all I do in include the CD as a source 	and it works. I could not find any way to make my CD/DVD drive a 	download source.  Does this really sound like a good system?  And 	please don't send a bunch of command line commands. Because I have 	found that even those who have good intentions, make the assumption 	that everyone knows where to place a space, forward slash, or dash. 	Only the very best of the experts on these forums give examples with 	explanations. Some simply say do sudo :$%%&*&^( or some 	crazy command function without any explanations and the poor jerk 	trying his best to get the thing working has to try a dozen times 	before figuring it out for his or herself). Please remember, 	everyone trying to load an OS on a computer doesn't have a PHD in 	computer science.
[/LIST]
 

 	As soon as I loaded Ubuntu up on the flash drive, I was impressed with the graphics, but after trying to do what should be simple tasks, such as installing a deb file from a CD. I was very discouraged. When some of these things are fixed, then I might try it again, but as it stands now, I think I will try to find another Linux OS that will work out of the box on an AMD64 laptop.

---

### Post by mastablasta on 2012-01-20
You are only user not administrator (root). however you have root access by command sudo, or gksudo (for graphical interfaces). If not in terminal then (at leats thats' how it used to be in Gnome) you right click and run as root. you use your own user password to run sudo command. more explanation here:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

> **ac4rb said:**
> 
     I believe this could be a great OS if the people packaging this would:
 
[LIST=1]
[*]Quit assuming that everyone has     high-speed Intranet and try to load the OS on a new machine like I     did without  wireless, dial-up, any internet or network.
[*]Package some codecs or at least do     as Xandros, and have an applications CD to support what you put into     the OS package. In other words, if you put the software in the     package, it should have the necessary codecs, or lib files to make     it work on at least the most popular types of music or videos. If it     is an office suite then spelling and such should work. Again, with     Xandros and some other distros, they do work.
[/LIST]
They can't do that without breaking copyright law. they add what they can, but they can't add codecs as adding them would go against some laws. Some systems do add them (take a look at ubuntu based Linux Mint or other Ubuntu variants), but they can only add them as they are based in such countries where these laws don't apply or they are small enoguh that no one really cares.


i do hate it that they completelly ignored PPP /dial up, though i believe the package has returned in 11.10 or will return in 12.04 not sure here. it is not there in 10.04 LTS. gnome-PPP or something like that.
[https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer)



> 
Fix it so a person can install a     deb file without being connected to any kind of network. Again,do     this on a network or internet free computer. After all, everyone     doesn't stay connected to the internet all of the time.    
 you can do that. not sure which .deb  you used. you can also download packages elsewhere and then use synaptic package manager to install them. or use source code and compile it (not a good way but it is usually easy enough - just copy paste the commands).
  
> .      
Some of the functions that should     work, at least it gives the impression that it will, do not work.     For instance, I had some old unformatted CD-RWs laying around. Try     to format one. Even though it tells you that it is unformatted and     asks if you want to format it, it will not. The software goes     through the whole routine, such as type of format, size, and Ect. It     even tells you that formating will destroy any data on the disk.     Then guess what, the software tells you it can't format the disk.     Why didn't the software check the disk out first then decide whether     it could or could not format the CD and tell you that  before you go     through 4 or 5 minuets reading and deciding how to format it only to     find you can't.
Eh, try another software such a k3b. As i know windowsXP for example has an even more stupid system of burning disks.
> 
To me, as this OS is, without some     changes, is nearly worthless. I can't even get the OS to install     programs I downloaded and put on a CD. It continues to tell me that     it cannot connect to the Ubuntu software center every time I click     on a deb file. In Xandros, all I do in include the CD as a source     and it works. I could not find any way to make my CD/DVD drive a     download source.  Does this really sound like a good system?  And     please don't send a bunch of command line commands. Because I have     found that even those who have good intentions, make the assumption     that everyone knows where to place a space, forward slash, or dash.     Only the very best of the experts on these forums give examples with     explanations. Some simply say do sudo :$%%&*&^( or some     crazy command function without any explanations and the poor jerk     trying his best to get the thing working has to try a dozen times     before figuring it out for his or herself). Please remember,     everyone trying to load an OS on a computer doesn't have a PHD in     computer science.

you can do that by going to software sources and then click to only use CD/DVD. it's all done via GUI. it can also be done with commands. have a look here: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)


The reason people give you the command is because they work the same on all desktop environments (if you haven't noticed Ubuntu comes in 4 flavours: Gnome (default Ubuntu), KDE (Kubuntu), XFCE (Xubuntu), LXDE (Lubuntu). you should try them BTW. Especially KDE is very Windows like after you right click the K and select classic menu.  In addition to those you have Enlightenment, various windows managers (IceWM, openbox....) that can also be put on top of Ubuntu. Now in each one there is another way to find things. However same commands work on all of them

And since commands can be copied and pasted to the terminal i don't really see any major issue here with typing.
  
 Another thing is these in between numbers are mostly like stable testing varieties. the LTS are the ones with long support.

[https://help.ubuntu.com/11.10/ubuntu-help/index.html](https://help.ubuntu.com/11.10/ubuntu-help/index.html)

---

### Post by ac4rb on 2012-01-20
> **mastablasta said:**
> You are only user not administrator (root). however you have root access by command sudo, or gksudo (for graphical interfaces). If not in terminal then (at leats thats' how it used to be in Gnome) you right click and run as root. you use your own user password to run sudo command. more explanation here:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

[/LIST]
They can't do that without breaking copyright law. they add what they can, but they can't add codecs as adding them would go against some laws. Some systems do add them (take a look at ubuntu based Linux Mint or other Ubuntu variants), but they can only add them as they are based in such countries where these laws don't apply or they are small enoguh that no one really cares.


i do hate it that they completelly ignored PPP /dial up, though i believe the package has returned in 11.10 or will return in 12.04 not sure here. it is not there in 10.04 LTS. gnome-PPP or something like that.
[https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer)



 you can do that. not sure which .deb  you used. you can also download packages elsewhere and then use synaptic package manager to install them. or use source code and compile it (not a good way but it is usually easy enough - just copy paste the commands).
  

Eh, try another software such a k3b. As i know windowsXP for example has an even more stupid system of burning disks.


you can do that by going to software sources and then click to only use CD/DVD. it's all done via GUI. it can also be done with commands. The reason people give you the command is because they work the same on all desktop environments (if you haven't noticed Ubuntu comes in 4 flavours: Gnome (default Ubuntu), KDE (Kubuntu), XFCE (Xubuntu), LXDE (Lubuntu). you should try them BTW. Especially KDE is very Windows like after you right click the K and select classic menu.  In addition to those you have Enlightenment, various windows managers (IceWM, openbox....) that can also be put on top of Ubuntu. Now in each one there is another way to find things. However same commands work on all of them

And since commands can be copied and pasted to the terminal i don't really see any major issue here with typing.
  
 Another thing is these in between numbers are mostly like stable testing varieties. the LTS are the ones with long support.

[https://help.ubuntu.com/11.10/ubuntu-help/index.html](https://help.ubuntu.com/11.10/ubuntu-help/index.html)
[U]NOTE: Thanks MASTABLASTER you are one of the real experts that try to help. I really appreciate you and the others that trully try to help instead of impress.
Thanks againAC4RB[/U]

---

### Post by ac4rb on 2012-01-20
> **ac4rb said:**
> [U]NOTE:  Thanks MASTABLASTER you are one of the real experts that try to help. I really appreciate you and the others that trully try to help instead of impress.
Thanks againAC4RB[/U]_1. I loaded ver. 11.10.AMD64 if dial-up is there, I cant find it. 2. I downloaded all deb files mentioned from Ubuntu's software center. 3. Is there any way I can change ownership?. I don't want anyone to take offence of the above thread. I sent it only as constructive critisism, and I know it is free and I really appreciate the people who work on this project. Would like to get it working as well as the Xandros because I think it can be a much better system. _

---

### Post by ac4rb on 2012-02-01
This is very Frustrating, I used my friends wireless highspeed internet to load either wvdial or gnome ppp. Using Ubuntu's software installation tool, I still had no luck. Both came back and said that there were dependences and would not install. Both needed some lib files. What is going on, why if the installation tool has enough smarts to know that these files are needed before it can install a new application, can't it also load the dependences first and then  load the installation? Xandros' network does just this and it works great. Like I said before, if I could find a Xandros that would work on my 64bit AMD laptop, I would use it. Looks like I am going to have to delete Ubuntu, and I really hate that because I think I would love it if I could get it working.

---

### Post by mastablasta on 2012-02-01
if you got access to high speed internet you should have installed via software center or synaptics, that way all dependencies would be downloaded as well (for example if you mark it it should mark all dependencies). if it's not in synaptics it means it has been dropped :-O
 
unless i missunderstod and you were using windows to download it. that might be a different issue.

---

### Post by ac4rb on 2012-02-01
> **mastablasta said:**
> if you got access to high speed internet you should have installed via software center or synaptics, that way all dependencies would be downloaded as well (for example if you mark it it should mark all dependencies). if it's not in synaptics it means it has been dropped :-O
 
unless i missunderstod and you were using windows to download it. that might be a different issue.
Mastablasta,
   Thanks, I did use the software center on Ubuntu desktop. This is where I got the messages about dependances not loaded. I searched for the gnome ppp in the software center, found and clicked on install after reading the normal information that is attached. After clicking on install, that is when the software center came back and told me that it could not install because there were some files that gnome ppp needs that was not on my computer and that the installation was not completed. It gave about 4 lib files that was needed BEFORE it could install the gnome ppp. Again, I thought if the software center knew that these were needed, it would install them, but it didn't. Xandros Networks, will and I have had very little getting a package to install even when I downloaded it and just clicked on it. Xandros asked me if I wanted to start it with Xandros Networks and I clicked yes, and it would do a complete install naming and including the dependances. 
      Maybe I have something loaded that shouldn't be in Ubuntu. Or it is just so much different that I haven't gotten the hang of it yet.
    Thanks again and may God bless,

Glenn AC4RB

---

### Post by mastablasta on 2012-02-03
that is very odd.
 
it should downldoad any packages if it really needs them. and installing from software center should work. what mirror are you using for repositories?
 
furthermore i find it strange that .deb is failing: 
[https://launchpad.net/ubuntu/+source/gnome-ppp/0.3.23-1ubuntu5](https://launchpad.net/ubuntu/+source/gnome-ppp/0.3.23-1ubuntu5)
[http://packages.ubuntu.com/oneiric/gnome-ppp](http://packages.ubuntu.com/oneiric/gnome-ppp)
 
Strange because even in debian sid this package is mainatained and new verison of gnomePPP (updated) is being tested for 12.04.
 
perhaps you could try to register on launchpad and ask the developer for help or if you are sure you did everything you should do to file a bug.

---

### Post by ac4rb on 2012-02-03
> **mastablasta said:**
> that is very odd.
 
it should downldoad any packages if it really needs them. and installing from software center should work. what mirror are you using for repositories?
 
furthermore i find it strange that .deb is failing: 
[https://launchpad.net/ubuntu/+source/gnome-ppp/0.3.23-1ubuntu5](https://launchpad.net/ubuntu/+source/gnome-ppp/0.3.23-1ubuntu5)
[http://packages.ubuntu.com/oneiric/gnome-ppp](http://packages.ubuntu.com/oneiric/gnome-ppp)
 
Strange because even in debian sid this package is mainatained and new verison of gnomePPP (updated) is being tested for 12.04.
 
perhaps you could try to register on launchpad and ask the developer for help or if you are sure you did everything you should do to file a bug.

I am using whatever repositories that are in the Software Center. I too think it is odd. Could it be because I have Ubuntu installed on a 16gb USB flash disk? Is it looking at the hard disk and trying to determine what to load? I was able to install WINE and NDISWRAPPER with ease. It didn't install a shortcuts in the GUI but I can envoke them in terminal. I thought this might be the case with Gnome PPP but that is not the case. 
Thanks Mastablasta..

Glenn

---

### Post by ac4rb on 2012-02-10
MASTABLASTA:
 I finally got wvdial to load. What I had to do was go to terminal type sudo nautilus, This gave me the ability to go to root and change premissions on the folders. I simply gave myself onwership of the needed files instead of root. After doing this this gave me premissions to change, add, or deleate files. Doing this allowed me to manually install wvdial. Now all I need to do is get a suitable driver (ini file) for my USB modem and I should be in business. By the way, for those reading this that are not aware of this, (I am sure MASTABLASTA is aware of this so I don't want to offend him) once you log out or close the window, it reverts back to root control. That is, the premissions will remain as you changed them but you just cannot go to system and change the premissions again without doing the whole terminal sudo nautilus thing again.  This gives you complete control while in the window only. 

Thanks again MASTABLASTA and may God bless,

Glenn AC4RB

---

### Post by ac4rb on 2012-02-12
> **ac4rb said:**
> MASTABLASTA:
 I finally got wvdial to load. What I had to do was go to terminal type sudo nautilus, This gave me the ability to go to root and change premissions on the folders. I simply gave myself onwership of the needed files instead of root. After doing this this gave me premissions to change, add, or deleate files. Doing this allowed me to manually install wvdial. Now all I need to do is get a suitable driver (ini file) for my USB modem and I should be in business. By the way, for those reading this that are not aware of this, (I am sure MASTABLASTA is aware of this so I don't want to offend him) once you log out or close the window, it reverts back to root control. That is, the premissions will remain as you changed them but you just cannot go to system and change the premissions again without doing the whole terminal sudo nautilus thing again.  This gives you complete control while in the window only. 

Thanks again MASTABLASTA and may God bless,

Glenn AC4RB

Please be careful when you change permissions. Change only those that are required to load applications or else it may crash.

---

### Post by Pifilatakanemu on 2012-08-07
What about 12.04 ?

Any issues with Ubuntu on the device?

Thanks!

---

### Post by LaPingvino on 2012-10-10
I have Wubi installed with 12.04.1 and it works without a glitch!

---

### Post by kronosua on 2013-06-27
I had problems with wi-fi and bluetooth in ubuntu 13.04. solved this problems by updating the BIOS and reset it to the default settings.

hp cq57-383sr

---

