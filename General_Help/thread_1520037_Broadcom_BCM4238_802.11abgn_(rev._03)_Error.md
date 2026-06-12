---
title: "Broadcom BCM4238 802.11a/b/g/n (rev. 03) Error"
date: 2010-06-29
forum: General Help
---

### Post by mattsweegold on 2010-06-29
Hey everyone, recently I have been trying various measures at getting this device to work but to no avail. Additionally, the reality is that I have a limited knowledge of Ubuntu and I feel that I have further worsened the situation. Initially, I was able to use the wl driver but my signal was far weaker than it would be under Windows. Now, although the device is recognized, I am not even able to detect a signal with it. Also, if its of any worth, I use a 64bit version of Ubuntu, connect to a WPA 2 server and am going to post some codes I found on another post.

lspci:

00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1
00:1c.1 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 2
00:1c.2 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 3
00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 6
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 RAID bus controller: Intel Corporation 82801 SATA RAID Controller
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
02:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
03:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)

lsusb:

Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 046d:c313 Logitech, Inc. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 09da:0006 A4 Tech Co., Ltd Optical Mouse WOP-35 / Trust 450L Optical Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:21:70:5a:d9:1f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:29 Base address:0x4000 

eth1      Link encap:Ethernet  HWaddr 00:24:2b:c1:6b:60  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:7 dropped:0 overruns:0 frame:872
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:700 (700.0 B)  TX bytes:700 (700.0 B)
iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:165
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0
lsmod:

Module                  Size  Used by
cryptd                  8116  0 
aes_x86_64              7912  0 
aes_generic            27607  1 aes_x86_64
binfmt_misc             7960  1 
ppdev                   6375  0 
ndiswrapper           244768  0 
snd_hda_codec_intelhdmi    13090  1 
snd_hda_codec_realtek   278890  1 
arc4                    1473  0 
sbp2                   22819  0 
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
vga16fb                12757  0 
vgastate                9857  1 vga16fb
snd_hda_intel          25645  2 
snd_hda_codec          85727  3 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87850  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31219  0 
snd_seq_midi            5829  0 
snd_rawmidi            23388  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57417  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
rtl8187                53204  0 
lib80211_crypt_tkip     8676  0 
i915                  317872  3 
lp                      9336  0 
snd_timer              23553  2 snd_pcm,snd_seq
mac80211              238128  1 rtl8187
led_class               3732  1 rtl8187
drm_kms_helper         30742  1 i915
snd_seq_device          6824  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
parport                37160  2 ppdev,lp
snd                    70978  17 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              148386  2 rtl8187,mac80211
eeprom_93cx6            1765  1 rtl8187
dell_wmi                2177  0 
dcdbas                  6886  0 
psmouse                64608  0 
serio_raw               4918  0 
wl                   1964968  0 
lib80211                6119  2 lib80211_crypt_tkip,wl
drm                   198770  4 i915,drm_kms_helper
i2c_algo_bit            6024  1 i915
soundcore               8052  1 snd
video                  20623  1 i915
intel_agp              29225  2 i915
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
output                  2503  1 video
hid_a4tech              2518  0 
usbhid                 40988  0 
hid                    83376  2 hid_a4tech,usbhid
usb_storage            49833  0 
ohci1394               30260  0 
ieee1394               94675  2 sbp2,ohci1394
r8169                  39650  0 
mii                     5237  1 r8169
ahci                   37646  2 

sudo lshw -C network:

*-network               
       description: Wireless interface
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 03
       serial: 00:24:2b:c1:6b:60
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:17 memory:fe9fc000-fe9fffff memory:fde00000-fdefffff(prefetchable)
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:21:70:5a:d9:1f
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:29 ioport:e800(size=256) memory:febff000-febfffff memory:fdff0000-fdffffff(prefetchable) memory:febc0000-febdffff(prefetchable)

iwlist:

Usage: iwlist [interface] scanning [essid NNN] [last]
              [interface] frequency 
              [interface] channel 
              [interface] bitrate 
              [interface] rate 
              [interface] encryption 
              [interface] keys 
              [interface] power 
              [interface] txpower 
              [interface] retry 
              [interface] ap 
              [interface] accesspoints 
              [interface] peers 
              [interface] event 
              [interface] auth 
              [interface] wpakeys 
              [interface] genie 
              [interface] modulation 

lsb_release -d:

Description:	Ubuntu 10.04 LTS

uname -mr
2.6.28-11-generic i686
sudo /etc/init.d/networking restart

---

### Post by dino99 on 2010-06-29
***

Description: Ubuntu 10.04 LTS

uname -mr
2.6.28-11-generic i686

***

your kernel is outdated, open synaptic to install the latest (header+image)

Just go to System -> Admin -> Hardware Drivers and activate "Broadcom STA wireless driver"

---

### Post by mattsweegold on 2010-06-29
I've enabled the sta driver, not exactly sure why it was disabled, and there was no kernel available for update. Although I am able to detect a signal, I am not able to connect with the Broadcom device...

---

### Post by dino99 on 2010-06-29
as bcm4328 is not supported yet, you might installed the latest kernel (35) 

add this ppa to synaptic repo

[https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=lucid](https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=lucid)

then update, upgrade

found an older thread in french (use google translate if you need)

[http://doc.ubuntu-fr.org/bcm4328](http://doc.ubuntu-fr.org/bcm4328)

---

