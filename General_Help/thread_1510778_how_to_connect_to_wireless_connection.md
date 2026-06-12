---
title: "how to connect to wireless connection"
date: 2010-06-16
forum: General Help
---

### Post by Praveen30 on 2010-06-16
[FONT=Trebuchet MS][SIZE=2]how to edit the wireless connection setup? i know how to do it in the wired network but don't know in this case..can anybody please tell me the step by step procedure...i have searched for this.seen some videos on youtube but nothing goes well...plz help[/SIZE][/FONT]

---

### Post by yeleek on 2010-06-16
[http://www.youtube.com/watch?v=m03RcFkSIA8](http://www.youtube.com/watch?v=m03RcFkSIA8)

Google is your friend

---

### Post by Praveen30 on 2010-06-16
thanx for referring the video. ..but the main problem is how to enable the driver.In the video a list comes with the software but in my case when i open the hardware driver it is totally blank..i don't know why it is blank...

---

### Post by beckols on 2010-06-16
Will you please post the output of
```
sudo lshw -C network
```
as well as
```
sudo lsmod
```

---

### Post by yeleek on 2010-06-16
As beckols is advising, you need to first find out then if Ubuntu has the drivers for your wifi card built in.

From there you can work out if its a driver issue, or simply skipping the hardware install step in the video and carrying out the rest of the config.

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by Praveen30 on 2010-06-16
Quite fuzzy for me but thanx for helping me out.here are the outputs--

---

### Post by beckols on 2010-06-16
try this:
```

sudo modprobe b43-pci-bridge

```

I believe the problem is that the driver is installed but the module isn't being loaded so it isn't talking to the kernel.  This command loads the module.

---

### Post by Praveen30 on 2010-06-16
An error is coming--

FATAL:Module b43_pci_bridge not found.

---

### Post by beckols on 2010-06-16
I think you are missing some output from lsmod, run the command again and copy and paste ALL of the results into a code block in a reply.

I think I was wrong in my last post, the driver should be just b43 I'm pretty sure.  So you might have to blacklist b43-pci-bridge.  First post the full output of lsmod and we'll go from there.

---

### Post by Praveen30 on 2010-06-16
praveen@ubuntu:~$ sudo lsmod
[sudo] password for praveen: 
Module                  Size  Used by
nls_iso8859_1           3740  0 
nls_cp437               5372  0 
vfat                   10716  0 
fat                    51452  1 vfat
usb_storage            52544  0 
binfmt_misc             8356  1 
ppdev                   6688  0 
bridge                 47952  0 
stp                     2272  1 bridge
bnep                   12060  2 
btusb                  11856  2 
snd_hda_codec_intelhdmi    12860  1 
snd_hda_codec_realtek   203328  1 
snd_hda_intel          26920  2 
snd_hda_codec          75708  3 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
b43                   122136  0 
joydev                 10272  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mac80211              181236  1 b43
iptable_filter          3100  0 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
uvcvideo               59080  0 
videodev               36736  1 uvcvideo
v4l1_compat            14496  2 uvcvideo,videodev
sdhci_pci               7100  0 
sdhci                  17472  1 sdhci_pci
snd                    59204  17 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                56180  0 
serio_raw               5280  0 
dell_wmi                2564  0 
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
lp                      8964  0 
dell_laptop             8128  0 
parport                35340  2 ppdev,lp
cfg80211               93052  2 b43,mac80211
dcdbas                  7292  1 dell_laptop
led_class               4096  2 b43,sdhci
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
usbhid                 38208  0 
ohci1394               29900  0 
ieee1394               86596  1 ohci1394
ssb                    35300  1 b43
i915                  221064  3 
drm                   159584  3 i915
i2c_algo_bit            5760  1 i915
intel_agp              27484  2 i915
agpgart                34988  2 drm,intel_agp
video                  19380  1 i915
output                  2780  1 video
tg3                   109600  0 
praveen@ubuntu:~$

---

### Post by beckols on 2010-06-16
Could you please also post the output of:
```

sudo lspci -vnn

```

---

### Post by beckols on 2010-06-16
Also open up System > Administration > Hardware Drivers, and see if there is a proprietary driver listed that you can enable.  The bcm4312 series is supposed to be supported out of the box when using the restricted driver.

I should have asked earlier, but what version of Ubuntu are you using?

---

### Post by Praveen30 on 2010-06-16
praveen@ubuntu:~$ sudo lsmod
[sudo] password for praveen: 
Module                  Size  Used by
nls_iso8859_1           3740  0 
nls_cp437               5372  0 
vfat                   10716  0 
fat                    51452  1 vfat
usb_storage            52544  0 
binfmt_misc             8356  1 
ppdev                   6688  0 
bridge                 47952  0 
stp                     2272  1 bridge
bnep                   12060  2 
btusb                  11856  2 
snd_hda_codec_intelhdmi    12860  1 
snd_hda_codec_realtek   203328  1 
snd_hda_intel          26920  2 
snd_hda_codec          75708  3 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
b43                   122136  0 
joydev                 10272  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mac80211              181236  1 b43
iptable_filter          3100  0 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
uvcvideo               59080  0 
videodev               36736  1 uvcvideo
v4l1_compat            14496  2 uvcvideo,videodev
sdhci_pci               7100  0 
sdhci                  17472  1 sdhci_pci
snd                    59204  17 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                56180  0 
serio_raw               5280  0 
dell_wmi                2564  0 
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
lp                      8964  0 
dell_laptop             8128  0 
parport                35340  2 ppdev,lp
cfg80211               93052  2 b43,mac80211
dcdbas                  7292  1 dell_laptop
led_class               4096  2 b43,sdhci
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
usbhid                 38208  0 
ohci1394               29900  0 
ieee1394               86596  1 ohci1394
ssb                    35300  1 b43
i915                  221064  3 
drm                   159584  3 i915
i2c_algo_bit            5760  1 i915
intel_agp              27484  2 i915
agpgart                34988  2 drm,intel_agp
video                  19380  1 i915
output                  2780  1 video
tg3                   109600  0 
praveen@ubuntu:~$

---

### Post by beckols on 2010-06-16
I needed 'lspci -vnn' not 'lsmod' but first check my post above about the restricted driver.

---

### Post by Praveen30 on 2010-06-16
praveen@ubuntu:~$ sudo lspci -vnn
[sudo] password for praveen: 
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 03)
	Subsystem: Dell Device [1028:025a]
	Flags: bus master, fast devsel, latency 0
	Capabilities: [e0] Vendor Specific Information <?>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 03)
	Subsystem: Dell Device [1028:025a]
	Flags: bus master, fast devsel, latency 0, IRQ 27
	Memory at f6e00000 (64-bit, non-prefetchable) [size=1M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at efe8 [size=8]
	Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [d0] Power Management version 3
	Kernel driver in use: i915
	Kernel modules: i915

00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a03] (rev 03)
	Subsystem: Dell Device [1028:025a]
	Flags: bus master, fast devsel, latency 0
	Memory at f6f00000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: [d0] Power Management version 3

00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 04)
	Subsystem: Dell Device [1028:025a]
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 6f60 [size=32]
	Kernel driver in use: uhci_hcd

00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 04)
	Subsystem: Dell Device [1028:025a]
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 6f80 [size=32]
	Kernel driver in use: uhci_hcd

00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 04) (prog-if 20)
	Subsystem: Dell Device [1028:025a]
	Flags: bus master, medium devsel, latency 0, IRQ 22
	Memory at fed1c400 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 04)
	Subsystem: Dell Device [1028:025a]
	Flags: bus master, fast devsel, latency 0, IRQ 21
	Memory at f6dfc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [130] Root Complex Link <?>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 04)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0b, subordinate=0b, sec-latency=0
	Memory behind bridge: f6c00000-f6cfffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Dell Device [1028:025a]
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.3 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 [8086:2845] (rev 04)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0c, subordinate=0d, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: f6a00000-f6bfffff
	Prefetchable memory behind bridge: 00000000f0000000-00000000f01fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Dell Device [1028:025a]
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.5 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 [8086:2849] (rev 04)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
	Memory behind bridge: f6900000-f69fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Dell Device [1028:025a]
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 04)
	Subsystem: Dell Device [1028:025a]
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 6f00 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 04)
	Subsystem: Dell Device [1028:025a]
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 6f20 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 04)
	Subsystem: Dell Device [1028:025a]
	Flags: bus master, medium devsel, latency 0, IRQ 22
	I/O ports at 6f40 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 04) (prog-if 20)
	Subsystem: Dell Device [1028:025a]
	Flags: bus master, medium devsel, latency 0, IRQ 20
	Memory at fed1c000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f4) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
	Memory behind bridge: f6800000-f68fffff
	Capabilities: [50] Subsystem: Dell Device [1028:025a]

00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 04)
	Subsystem: Dell Device [1028:025a]
	Flags: bus master, medium devsel, latency 0
	Capabilities: [e0] Vendor Specific Information <?>
	Kernel modules: iTCO_wdt

00:1f.2 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller [8086:2828] (rev 04) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Dell Device [1028:025a]
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 17
	I/O ports at 6e70 [size=8]
	I/O ports at 6e78 [size=4]
	I/O ports at 6e80 [size=8]
	I/O ports at 6e88 [size=4]
	I/O ports at 6ea0 [size=16]
	I/O ports at eff0 [size=16]
	Capabilities: [70] Power Management version 3
	Kernel driver in use: ata_piix

00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 04)
	Subsystem: Dell Device [1028:025a]
	Flags: medium devsel, IRQ 10
	Memory at f6dfbf00 (32-bit, non-prefetchable) [size=256]
	I/O ports at 10c0 [size=32]
	Kernel modules: i2c-i801

03:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05) (prog-if 10)
	Subsystem: Dell Device [1028:025a]
	Flags: bus master, medium devsel, latency 64, IRQ 19
	Memory at f68ff800 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [dc] Power Management version 2
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

03:01.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22) (prog-if 01)
	Subsystem: Dell Device [1028:025a]
	Flags: bus master, medium devsel, latency 64, IRQ 18
	Memory at f68ff500 (32-bit, non-prefetchable) [size=256]
	Capabilities: [80] Power Management version 2
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

03:01.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
	Subsystem: Dell Device [1028:025a]
	Flags: bus master, medium devsel, latency 64, IRQ 4
	Memory at f68ff600 (32-bit, non-prefetchable) [size=256]
	Capabilities: [80] Power Management version 2

03:01.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 12)
	Subsystem: Dell Device [1028:025a]
	Flags: bus master, medium devsel, latency 64, IRQ 4
	Memory at f68ff700 (32-bit, non-prefetchable) [size=256]
	Capabilities: [80] Power Management version 2

09:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe [14e4:1698] (rev 10)
	Subsystem: Dell Device [1028:025a]
	Flags: bus master, fast devsel, latency 0, IRQ 28
	Memory at f69f0000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: [48] Power Management version 3
	Capabilities: [40] Vital Product Data <?>
	Capabilities: [60] Vendor Specific Information <?>
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
	Capabilities: [cc] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [13c] Virtual Channel <?>
	Capabilities: [160] Device Serial Number ba-65-07-fe-ff-ae-23-00
	Capabilities: [16c] Power Budgeting <?>
	Kernel driver in use: tg3
	Kernel modules: tg3

0b:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
	Subsystem: Dell Device [1028:000c]
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f6cfc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [40] Power Management version 3
	Capabilities: [58] Vendor Specific Information <?>
	Capabilities: [e8] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [d0] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [13c] Virtual Channel <?>
	Capabilities: [160] Device Serial Number 22-00-72-ff-ff-5f-34-cf
	Capabilities: [16c] Power Budgeting <?>
	Kernel driver in use: b43-pci-bridge
	Kernel modules: ssb

praveen@ubuntu:~$

---

### Post by Praveen30 on 2010-06-16
there is no driver listed in hardware driver. I am using 9.10 version of ubuntu

---

### Post by beckols on 2010-06-16
According to this page: [http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43)

your card (PCI-ID: 14e4:4315) is supported by kernel version 2.6.32 and later.  I have a version of 9.10 on a virtual machine and the kernel is at 2.6.31.  If the output of 'uname -a' shows a kernel version that is less than 2.6.32, then you need to run the update-manager and make sure you have the latest and greatest updates.

---

### Post by Praveen30 on 2010-06-16
Well,i have checked the command and the result is 2.6.31..so that means i have to run the update manager..but the problem is i am unable to connect to internet via ubuntu..all the therads which i am sending you,is via window vista.but thanx for your continous replies.

---

### Post by beckols on 2010-06-16
[http://basicubuntu.blogspot.com/2009/02/install-on-ubuntu-without-internet.html](http://basicubuntu.blogspot.com/2009/02/install-on-ubuntu-without-internet.html)

The above link explains how to upgrade packages without having an active internet connection.  It is a little dated, but it should still be similar enough to work with 9.10.

---

### Post by Praveen30 on 2010-06-16
Actually BECKOLS, i am at my friend's home and there is only wireless connection.The problem started when i installed the lucid lynx..the same problem was coming.So i thought just check with the 9.10 but the same thing is happening here.i think you have found the reason it is just because of the updation..Now the crux of the problem--my friend's has also the same pc and he is not the much of the linux boy.but i make him install ubuntu,so he has to update also and the same problem will come in his pc..and your referring link demands that there must be one internet running pc having ubuntu...Is there any way to do this with the help of window?

---

### Post by Praveen30 on 2010-06-17
well ! well ! well ! somehow i have managed the wired connection and after updation
there are some wireless drivers coming in the hardware driver list.they are--

1- broadcom b43 wireless driver 
2- broadcom sta wireless driver

---

### Post by beckols on 2010-06-17
It should be the B43 driver, so it worked after you updated to Lucid then?  I was going to suggest that, but I didn't know if you hadn't upgraded on purpose or not.

---

### Post by Praveen30 on 2010-06-17
No i am still running the 9.10 version,i have not upgraded to lucid..i have just run the update command on the terminal--

sudo apt-get install update

after running this i have checked the hardware driver list and this b43 was glowing there..

---

### Post by Praveen30 on 2010-06-17
well my friend now i new problem..
--when i put my cursor on the b43 driver the message was showing it is not activate so i click on the activate button and now this error is coming---


SystemError: Failed to lock /var/cache/apt/archives/lock

what to do?

---

### Post by beckols on 2010-06-17
Do you have update-manager or synaptic running?  If so close out of them and try it again.

---

### Post by Praveen30 on 2010-06-17
Ya, my synaptic manager was running.now i have activated all the driver..i have also activated the sata driver.it was referred to me in the first page post..i have rebooted my laptop also..now what?

---

### Post by beckols on 2010-06-17
Is your wireless working correctly now?

---

### Post by Praveen30 on 2010-06-17
it was not working at that time.So i just looked in the video again,find that i also have to write the mac address..So its working and this quote is from ubuntu wireless 9.10 for you!!!

Thanx for your efforts.it all happens because of you.So in my indian culture--DHANYAWAD(thank you).i know the time differs,it is night here..what is there?










9

---

### Post by beckols on 2010-06-17
It's 11:50 a.m. here, just getting the day started :)

---

### Post by Praveen30 on 2010-06-17
Well,you are replying me just after waking up...thanx man!!! ):P

---

### Post by beckols on 2010-06-17
No problem at all, I learned a few things along the way as well.  Make sure to mark the thread as solved (Top of the page, Thread Tools).

---

