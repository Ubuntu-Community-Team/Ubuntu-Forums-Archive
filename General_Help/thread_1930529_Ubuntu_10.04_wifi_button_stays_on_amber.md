---
title: "Ubuntu 10.04 wifi button stays on amber"
date: 2012-02-23
forum: General Help
---

### Post by geewhan on 2012-02-23
When I boot my laptop, HP Pavilion dv6, and log in into Ubuntu desktop the wifi button is amber color instead of white. Which I do not receive wireless network. I do get wired network when I connect it to the Ethernet cable. 

I understand there are other posts out there, but it looks like their situation is different. There is one solution that did this
installed the following in one batch:
bcmwl-kernel-source
b43-fwcutter
bcmwl-modaliases

This did not work for me.

Could anyone please help me.

Thank you for your time.

---

### Post by miasmablk on 2012-02-23
could you post the outputs of

```
ifconfig
```

and 

```
lspci -v
```

---

### Post by geewhan on 2012-02-23
for ifconfig
```
gee@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 2c:41:38:5c:8d:5f  
          inet addr:192.168.2.7  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::2e41:38ff:fe5c:8d5f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:479 errors:0 dropped:479 overruns:0 frame:479
          TX packets:562 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:425711 (425.7 KB)  TX bytes:125363 (125.3 KB)
          Interrupt:27 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)
```


for lspci -v

```
gee@ubuntu:~$ lspci -v
00:00.0 Host bridge: Advanced Micro Devices [AMD] Device 1705
    Subsystem: Advanced Micro Devices [AMD] Device 1705
    Flags: bus master, 66MHz, medium devsel, latency 32

00:01.0 VGA compatible controller: ATI Technologies Inc Device 9647
    Subsystem: Hewlett-Packard Company Device 358b
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at e0000000 (32-bit, prefetchable) [size=256M]
    I/O ports at 4000 [size=256]
    Memory at f0300000 (32-bit, non-prefetchable) [size=256K]
    Capabilities: <access denied>

00:01.1 Audio device: ATI Technologies Inc Device 1714
    Subsystem: Hewlett-Packard Company Device 358b
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at f0344000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:04.0 PCI bridge: Advanced Micro Devices [AMD] Device 1709
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Prefetchable memory behind bridge: 00000000f0000000-00000000f00fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:05.0 PCI bridge: Advanced Micro Devices [AMD] Device 170a
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: f0200000-f02fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:06.0 PCI bridge: Advanced Micro Devices [AMD] Device 170b
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    Memory behind bridge: f0100000-f01fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:10.0 USB Controller: Advanced Micro Devices [AMD] Device 7812 (rev 03) (prog-if 30)
    Subsystem: Hewlett-Packard Company Device 358b
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at f0348000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd
    Kernel modules: xhci

00:10.1 USB Controller: Advanced Micro Devices [AMD] Device 7812 (rev 03) (prog-if 30)
    Subsystem: Hewlett-Packard Company Device 358b
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at f034a000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd
    Kernel modules: xhci

00:11.0 SATA controller: Advanced Micro Devices [AMD] Device 7804 (prog-if 01)
    Subsystem: Hewlett-Packard Company Device 358b
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 28
    I/O ports at 4138 [size=8]
    I/O ports at 414c [size=4]
    I/O ports at 4130 [size=8]
    I/O ports at 4148 [size=4]
    I/O ports at 4110 [size=16]
    Memory at f0350000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:12.0 USB Controller: Advanced Micro Devices [AMD] Device 7807 (rev 11) (prog-if 10)
    Subsystem: Hewlett-Packard Company Device 358b
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at f034f000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:12.2 USB Controller: Advanced Micro Devices [AMD] Device 7808 (rev 11) (prog-if 20)
    Subsystem: Hewlett-Packard Company Device 358b
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
    Memory at f034e000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:13.0 USB Controller: Advanced Micro Devices [AMD] Device 7807 (rev 11) (prog-if 10)
    Subsystem: Hewlett-Packard Company Device 358b
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at f034d000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.2 USB Controller: Advanced Micro Devices [AMD] Device 7808 (rev 11) (prog-if 20)
    Subsystem: Hewlett-Packard Company Device 358b
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
    Memory at f034c000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:14.0 SMBus: Advanced Micro Devices [AMD] Device 780b (rev 13)
    Subsystem: Hewlett-Packard Company Device 358b
    Flags: 66MHz, medium devsel
    Kernel modules: i2c-piix4

00:14.1 IDE interface: Advanced Micro Devices [AMD] Device 780c (rev 40) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: Hewlett-Packard Company Device 358b
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
    I/O ports at 4128 [size=8]
    I/O ports at 4144 [size=4]
    I/O ports at 4120 [size=8]
    I/O ports at 4140 [size=4]
    I/O ports at 4100 [size=16]
    Kernel driver in use: pata_atiixp
    Kernel modules: pata_atiixp

00:14.2 Audio device: Advanced Micro Devices [AMD] Device 780d (rev 01)
    Subsystem: Hewlett-Packard Company Device 358b
    Flags: bus master, slow devsel, latency 32, IRQ 16
    Memory at f0340000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:14.3 ISA bridge: Advanced Micro Devices [AMD] Device 780e (rev 11)
    Subsystem: Hewlett-Packard Company Device 358b
    Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: Advanced Micro Devices [AMD] Device 780f (rev 40) (prog-if 01)
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=64

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

01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
    Subsystem: Hewlett-Packard Company Device 1805
    Flags: bus master, fast devsel, latency 0, IRQ 27
    I/O ports at 3000 [size=256]
    Memory at f0004000 (64-bit, prefetchable) [size=4K]
    Memory at f0000000 (64-bit, prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8176 (rev 01)
    Subsystem: Hewlett-Packard Company Device 1629
    Flags: bus master, fast devsel, latency 0, IRQ 5
    I/O ports at 2000 [size=256]
    Memory at f0200000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>

03:00.0 Class ff00: Realtek Semiconductor Co., Ltd. Device 5209 (rev 01)
    Subsystem: Hewlett-Packard Company Device 1805
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at f0101000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>

03:00.1 SD Host controller: Realtek Semiconductor Co., Ltd. Device 5209 (rev 01)
    Subsystem: Hewlett-Packard Company Device 1805
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at f0100000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci
```

---

### Post by wildmanne39 on 2012-02-23
Hi, please post the output of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by pqwoerituytrueiwoq on 2012-02-23
have you tried 11.10 as a live cd if it works with your wife you may just need a newer kernel in which case there are backports available
i would try natty's kernel first oneiric's is known to have power usage issues on some laptops

---

### Post by claracc on 2012-02-24
In my hp compaq 6720 s laptop, since karmic koala release, network manager hasn't worked with my wireless Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

So I had to install wicd and uninstall network manager. Wicd works with my wireless. You can do it throuh synaptic with your wired connection, after downloding wicd and installing it you can safely remove network manager ( I don't know if it is automatically removed in 11.10, since I am in 10.04) but not before because you can lose the wired connection. 

[http://ubuntuforums.org/showthread.php?t=1753144](http://ubuntuforums.org/showthread.php?t=1753144)

---

### Post by geewhan on 2012-02-24
for cat /etc/lsb-release; uname -a
```

gee@ubuntu:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.4 LTS"
Linux ubuntu 2.6.32-38-generic #83-Ubuntu SMP Wed Jan 4 11:13:04 UTC 2012 i686 GNU/Linux

```for Ispci -nnk | grep -iA2 net
```

gee@ubuntu:~$ lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
    Kernel driver in use: r8169
    Kernel modules: r8169
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8176] (rev 01)
03:00.0 Class [ff00]: Realtek Semiconductor Co., Ltd. Device [10ec:5209] (rev 01)
03:00.1 SD Host controller [0805]: Realtek Semiconductor Co., Ltd. Device [10ec:5209] (rev 01)

```
for iwconfig
```

gee@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```
for rfkill list all

nothing is displayed


for lsmod
```

gee@ubuntu:~$ lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_idt      52042  1 
snd_hda_codec_atihdmi     2367  1 
snd_hda_intel          22069  2 
snd_hda_codec          74201  3 snd_hda_codec_idt,snd_hda_codec_atihdmi,snd_hda_intel
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
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
uvcvideo               57438  0 
psmouse                63677  0 
softcursor              1189  1 bitblit
videodev               34425  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
serio_raw               3978  0 
sdhci_pci               5470  0 
sdhci                  15494  1 sdhci_pci
snd                    54244  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_piix4               8335  0 
hp_accel               11144  0 
lis3lv02d               6096  1 hp_accel
vga16fb                11385  1 
vgastate                8961  1 vga16fb
video                  17375  0 
output                  1871  1 video
input_polldev           2482  1 lis3lv02d
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
xhci                   37160  0 
led_class               2864  2 sdhci,hp_accel
lp                      7028  0 
parport                32635  2 ppdev,lp
usbhid                 36110  0 
hid                    67288  1 usbhid
r8169                  34140  0 
mii                     4381  1 r8169
pata_atiixp             3148  0 
ahci                   32680  1 

```

---

### Post by wildmanne39 on 2012-02-24
Hi, you will need to have a wired connection then please do:
```
sudo add-apt-repository ppa:lexical/hwe-wireless
sudo apt-get update
sudo apt-get install rtl8192ce-dkms
```
watch for errors then unplug your wired connection and reboot.
Thanks

---

### Post by geewhan on 2012-02-24
omg thank you thank you thank you

I do not know how you did it, but it works now.

Even though I wanted Ubuntu 11.10 to work, but I think I can settle with Ubuntu 10.04 since it is working.

Thank you so much for you help.

---

### Post by wildmanne39 on 2012-02-24
Hi, your welcome! Glad to help, would you please use thread tools at the top of the page and mark the thread solved.
Thanks

---

