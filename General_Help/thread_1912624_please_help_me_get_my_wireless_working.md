---
title: "please help me get my wireless working"
date: 2012-01-21
forum: General Help
---

### Post by jbunch on 2012-01-21
I am currently having to tether my laptop using my Droidx and would much rather use wifi but it is currently not working. hard wired connection is not working either.  I am on 10.4 it is the only thing that would boot on my laptop. 
Thanks in advanced.

---

### Post by JDog2pt0 on 2012-01-21
Install "wicd"

---

### Post by someitalian123 on 2012-01-21
Type "lspci -v" in the terminal and post the results

---

### Post by kurt18947 on 2012-01-21
> **jbunch said:**
> I am currently having to tether my laptop using my Droidx and would much rather use wifi but it is currently not working. hard wired connection is not working either.  I am on 10.4 it is the only thing that would boot on my laptop. 
Thanks in advanced.

Is your wireless adapter built in or plugged into a USB port?  If plugged into a USB port, could you post the output of 'lsusb'?  If the wireless adapter is built into the laptop, post the output of 'lcpci'?  10.04 requires extra software/firmware for certain chipsets.

---

### Post by wildmanne39 on 2012-01-21
Hi, not having a wired connection is going to make it a lot harder and possibly impossible for me to help you get it going, it all depends on the wireless card.

Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
Thanks

---

### Post by jbunch on 2012-01-21
00:00.0 Host bridge: Advanced Micro Devices [AMD] Device 1510
    Subsystem: Toshiba America Info Systems Device fd7b
    Flags: bus master, 66MHz, medium devsel, latency 32

00:01.0 VGA compatible controller: ATI Technologies Inc Device 9806
    Subsystem: Toshiba America Info Systems Device fd7c
    Flags: bus master, fast devsel, latency 0, IRQ 28
    Memory at c0000000 (32-bit, prefetchable) [size=256M]
    I/O ports at f000 [size=256]
    Memory at feb00000 (32-bit, non-prefetchable) [size=256K]
    Capabilities: <access denied>
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx

00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode] (rev 40) (prog-if 01)
    Subsystem: Toshiba America Info Systems Device fd7b
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 19
    I/O ports at f190 [size=8]
    I/O ports at f180 [size=4]
    I/O ports at f170 [size=8]
    I/O ports at f160 [size=4]
    I/O ports at f150 [size=16]
    Memory at feb4a000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
    Subsystem: Toshiba America Info Systems Device fd7b
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at feb49000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
    Subsystem: Toshiba America Info Systems Device fd7b
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
    Memory at feb48000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
    Subsystem: Toshiba America Info Systems Device fd7b
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at feb47000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
    Subsystem: Toshiba America Info Systems Device fd7b
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
    Memory at feb46000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 42)
    Subsystem: Toshiba America Info Systems Device fd7b
    Flags: 66MHz, medium devsel
    Kernel modules: i2c-piix4

00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller (rev 40) (prog-if 8a [Master SecP PriP])
    Subsystem: Toshiba America Info Systems Device fd7b
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at f100 [size=16]
    Kernel driver in use: pata_atiixp
    Kernel modules: pata_atiixp

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
    Subsystem: Toshiba America Info Systems Device fd78
    Flags: bus master, slow devsel, latency 32, IRQ 16
    Memory at feb40000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller (rev 40)
    Subsystem: Toshiba America Info Systems Device fd7b
    Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40) (prog-if 01)
    Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=64

00:15.0 PCI bridge: ATI Technologies Inc Device 43a0
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:15.1 PCI bridge: ATI Technologies Inc Device 43a1
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: fea00000-feafffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:15.2 PCI bridge: ATI Technologies Inc Device 43a2
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Prefetchable memory behind bridge: 00000000d0000000-00000000d00fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:16.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
    Subsystem: Toshiba America Info Systems Device fd7b
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at feb45000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:16.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
    Subsystem: Toshiba America Info Systems Device fd7b
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
    Memory at feb44000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:18.0 Host bridge: Advanced Micro Devices [AMD] Device 1700 (rev 43)
    Flags: fast devsel

00:18.1 Host bridge: Advanced Micro Devices [AMD] Device 1701
    Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] Device 1702
    Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] Device 1703
    Flags: fast devsel
    Capabilities: <access denied>

00:18.4 Host bridge: Advanced Micro Devices [AMD] Device 1704
    Flags: fast devsel

00:18.5 Host bridge: Advanced Micro Devices [AMD] Device 1718
    Flags: fast devsel

00:18.6 Host bridge: Advanced Micro Devices [AMD] Device 1716
    Flags: fast devsel

00:18.7 Host bridge: Advanced Micro Devices [AMD] Device 1719
    Flags: fast devsel

03:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8176 (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device 8182
    Flags: bus master, fast devsel, latency 0, IRQ 7
    I/O ports at e000 [size=256]
    Memory at fea00000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>

04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
    Subsystem: Toshiba America Info Systems Device fd7b
    Flags: bus master, fast devsel, latency 0, IRQ 27
    I/O ports at d000 [size=256]
    Memory at d0004000 (64-bit, prefetchable) [size=4K]
    Memory at d0000000 (64-bit, prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

---

### Post by jbunch on 2012-01-21
> **wildmanne39 said:**
> Hi, not having a wired connection is going to make it a lot harder and possibly impossible for me to help you get it going, it all depends on the wireless card.

Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```Thanks

jonathan@jonathan-laptop:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.3 LTS"
Linux jonathan-laptop 2.6.32-37-generic #81-Ubuntu SMP Fri Dec 2 20:35:14 UTC 2011 i686 GNU/Linux
jonathan@jonathan-laptop:~$ lspci -nnk lspci -nnk | grep -iA2 net
Usage: lspci [<switches>]

Basic display modes:
-mm        Produce machine-readable output (single -m for an obsolete format)
-t        Show bus tree

Display options:
-v        Be verbose (-vv for very verbose)
-k        Show kernel drivers handling each device
-x        Show hex-dump of the standard part of the config space
-xxx        Show hex-dump of the whole config space (dangerous; root only)
-xxxx        Show hex-dump of the 4096-byte extended config space (root only)
-b        Bus-centric view (addresses and IRQ's as seen by the bus)
-D        Always show domain numbers

Resolving of device ID's to names:
-n        Show numeric ID's
-nn        Show both textual and numeric ID's (names & numbers)
-q        Query the PCI ID database for unknown ID's via DNS
-qq        As above, but re-query locally cached entries
-Q        Query the PCI ID database for all ID's via DNS

Selection of devices:
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]    Show only devices in selected slots
-d [<vendor>]:[<device>]            Show only devices with specified ID's

Other options:
-i <file>    Use specified ID database instead of /usr/share/misc/pci.ids.gz
-p <file>    Look up kernel modules in a given file instead of default modules.pcimap
-M        Enable `bus mapping' mode (dangerous; root only)

PCI access options:
-A <method>    Use the specified PCI access method (see `-A help' for a list)
-O <par>=<val>    Set PCI access parameter (see `-O help' for a list)
-G        Enable PCI access debugging
-H <mode>    Use direct hardware access (<mode> = 1 or 2)
-F <file>    Read PCI configuration dump from a given file
jonathan@jonathan-laptop:~$ lsusb
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 04f2:b28e Chicony Electronics Co., Ltd 
Bus 002 Device 002: ID 0bda:0138 Realtek Semiconductor Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 22b8:4286 Motorola PCS 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
jonathan@jonathan-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

easytether0  no wireless extensions.

jonathan@jonathan-laptop:~$ rfkill list all
jonathan@jonathan-laptop:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
vfat                    8933  1 
fat                    47767  1 vfat
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_realtek   203440  1 
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
joydev                  8740  0 
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
fglrx                2781186  94 
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19130  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
uvcvideo               57438  0 
video                  17375  0 
output                  1871  1 video
agpgart                31724  1 fglrx
videodev               34425  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
psmouse                63677  0 
serio_raw               3978  0 
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
i2c_piix4               8335  0 
vga16fb                11385  1 
vgastate                8961  1 vga16fb
lp                      7028  0 
parport                32635  2 ppdev,lp
usb_storage            39969  1 
r8169                  34140  0 
ahci                   32680  2 
mii                     4381  1 r8169
pata_atiixp             3148  0 
jonathan@jonathan-laptop:~$

---

### Post by wildmanne39 on 2012-01-21
Hi, many of the commands did not come out right because of typo's that is why I suggested copy and paste for accuracy.

Please run them again and just copy and paste the output here.  

I did get your wireless device though, here is the method to get it working with an internet connection.
```
sudo add-apt-repository ppa:lexical/hwe-wireless
sudo apt-get update
sudo apt-get install rtl8192ce-dkms
```
If you will post the information again I will see if we can get the wired connection working first.
Thanks

---

### Post by jbunch on 2012-01-22
> **wildmanne39 said:**
> Hi, many of the commands did not come out right because of typo's that is why I suggested copy and paste for accuracy.

Please run them again and just copy and paste the output here.  

I did get your wireless device though, here is the method to get it working with an internet connection.
```
sudo add-apt-repository ppa:lexical/hwe-wireless
sudo apt-get update
sudo apt-get install rtl8192ce-dkms
```If you will post the information again I will see if we can get the wired connection working first.
Thanks

when i try that i get this error code
Error reading [https://launchpad.net/api/1.0/~lexical/+archive/hwe-wireless:]("https://launchpad.net/api/1.0/%7Elexical/+archive/hwe-wireless:") <urlopen error [Errno 110] Connection timed out>

EDIT:
I ran the commands again
jonathan@jonathan-laptop:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.3 LTS"
Linux jonathan-laptop 2.6.32-37-generic #81-Ubuntu SMP Fri Dec 2 20:35:14 UTC 2011 i686 GNU/Linux
jonathan@jonathan-laptop:~$ lspci -nnk | grep -iA2 net
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8176] (rev 01)
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Kernel driver in use: r8169
    Kernel modules: r8169
jonathan@jonathan-laptop:~$ lsusb
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 04f2:b28e Chicony Electronics Co., Ltd 
Bus 002 Device 002: ID 0bda:0138 Realtek Semiconductor Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 22b8:4286 Motorola PCS 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
jonathan@jonathan-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

easytether0  no wireless extensions.

jonathan@jonathan-laptop:~$ rfkill list all
jonathan@jonathan-laptop:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
vfat                    8933  1 
fat                    47767  1 vfat
binfmt_misc             6587  1 
ppdev                   5259  0 
joydev                  8740  0 
snd_hda_codec_realtek   203440  1 
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19130  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               57438  0 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
soundcore               6620  1 snd
psmouse                63677  0 
serio_raw               3978  0 
videodev               34425  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
video                  17375  0 
output                  1871  1 video
fglrx                2781186  103 
i2c_piix4               8335  0 
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
agpgart                31724  1 fglrx
vga16fb                11385  1 
vgastate                8961  1 vga16fb
lp                      7028  0 
parport                32635  2 ppdev,lp
usb_storage            39969  1 
pata_atiixp             3148  0 
r8169                  34140  0 
mii                     4381  1 r8169
ahci                   32680  2 
jonathan@jonathan-laptop:~$


EDIT 2
does being tether to my phone not count as an Internet connection?

---

### Post by wildmanne39 on 2012-01-22
Hi, because as I stated that is the method for getting it to work with an internet connection, that is why I asked for you to post the output of the commands again so I can see if it is possible to get the wired connection working.

However I mainly work with wireless issues so wired is not my strong suite.

You could also use a mobile phone as a modem to get the wireless working or borrow an usb wireless adapter from a friend that is plug and play.
Thanks

---

### Post by jbunch on 2012-01-22
> **wildmanne39 said:**
> Hi, because as I stated that is the method for getting it to work with an internet connection, that is why I asked for you to post the output of the commands again so I can see if it is possible to get the wired connection working.

However I mainly work with wireless issues so wired is not my strong suite.

You could also use a mobile phone as a modem to get the wireless working or borrow an usb wireless adapter from a friend that is plug and play.
Thanks

Im currently tethered to my phone will that work?

---

### Post by wildmanne39 on 2012-01-22
Hi, > Im currently tethered to my phone will that work?Yes that should work fine to install the wireless driver, just run these commands one line at a time then disconnect your phone and reboot.
```
sudo add-apt-repository ppa:lexical/hwe-wireless
sudo apt-get update
sudo apt-get install rtl8192ce-dkms
```
Thanks

---

### Post by jbunch on 2012-01-22
> **wildmanne39 said:**
> Hi, Yes that should work fine to install the wireless driver, just run these commands one line at a time then disconnect your phone and reboot.
```
sudo add-apt-repository ppa:lexical/hwe-wireless
sudo apt-get update
sudo apt-get install rtl8192ce-dkms
```Thanks

im getting an error when i try using that command

```
jonathan@jonathan-laptop:~$ sudo add-apt-repository ppa:lexical/hwe-wireless
[sudo] password for jonathan: 
Error reading https://launchpad.net/api/1.0/~lexical/+archive/hwe-wireless: <urlopen error [Errno 110] Connection timed out>
jonathan@jonathan-laptop:~$ sudo add-apt-repository ppa:lexical/hwe-wireless
Error reading https://launchpad.net/api/1.0/~lexical/+archive/hwe-wireless: <urlopen error [Errno 110] Connection timed out>
jonathan@jonathan-laptop:~$
```

```
 jonathan@jonathan-laptop:~$ sudo apt-get update
Get:1 http://ppa.launchpad.net lucid Release.gpg [316B]                        
Ign http://ppa.launchpad.net/lexical/hwe-wireless/ubuntu/ lucid/main Translation-en_US
Hit http://archive.canonical.com lucid Release.gpg                             
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_US       
Hit http://security.ubuntu.com lucid-security Release.gpg                      
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US   
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Hit http://us.archive.ubuntu.com lucid Release.gpg                             
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US          
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US    
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US      
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US    
Hit http://us.archive.ubuntu.com lucid-updates Release.gpg           
Hit http://security.ubuntu.com lucid-security Release                
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://archive.canonical.com lucid Release                       
Get:2 http://ppa.launchpad.net lucid Release [57.3kB]                
Hit http://us.archive.ubuntu.com lucid Release                                 
Ign http://ppa.launchpad.net lucid Release                                     
Hit http://security.ubuntu.com lucid-security/main Packages                    
Hit http://archive.canonical.com lucid/partner Packages                        
Hit http://ppa.launchpad.net lucid/main Packages                     
Hit http://us.archive.ubuntu.com lucid-updates Release
Hit http://security.ubuntu.com lucid-security/restricted Packages
Hit http://security.ubuntu.com lucid-security/main Sources
Hit http://security.ubuntu.com lucid-security/restricted Sources
Hit http://security.ubuntu.com lucid-security/universe Packages
Hit http://security.ubuntu.com lucid-security/universe Sources
Hit http://us.archive.ubuntu.com lucid/main Packages
Hit http://us.archive.ubuntu.com lucid/restricted Packages
Hit http://us.archive.ubuntu.com lucid/main Sources
Hit http://us.archive.ubuntu.com lucid/restricted Sources
Hit http://us.archive.ubuntu.com lucid/universe Packages
Hit http://security.ubuntu.com lucid-security/multiverse Packages
Hit http://security.ubuntu.com lucid-security/multiverse Sources
Hit http://us.archive.ubuntu.com lucid/universe Sources
Hit http://us.archive.ubuntu.com lucid/multiverse Packages
Hit http://us.archive.ubuntu.com lucid/multiverse Sources
Hit http://us.archive.ubuntu.com lucid-updates/main Packages
Hit http://us.archive.ubuntu.com lucid-updates/restricted Packages
Hit http://us.archive.ubuntu.com lucid-updates/main Sources
Hit http://us.archive.ubuntu.com lucid-updates/restricted Sources
Hit http://us.archive.ubuntu.com lucid-updates/universe Packages
Hit http://us.archive.ubuntu.com lucid-updates/universe Sources
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Packages
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Sources
Fetched 317B in 4s (77B/s)
Reading package lists... Done
W: GPG error: http://ppa.launchpad.net lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0C5CE27EA088FF1E
```

---

### Post by jbunch on 2012-01-22
After running those commands, wireless is working. thank you so much for your help!

---

### Post by mörgæs on 2012-01-22
Good, then please mark the thread 'solved' using 'thread tools'.

---

### Post by wildmanne39 on 2012-01-23
Hi, your welcome! 
Enjoy

---

