---
title: "speed touch 330 packages?"
date: 2011-06-21
forum: General Help
---

### Post by iebo on 2011-06-21
hey guys i'm tring to install some packages for speed touch  330 (black) usb modem :popcorn:

 it's a bit hard to manage this pks one by one ...so is there any automatic repositories out there for this list?

```
 1.python-gtkmozembed
2.python-eggtrayicon
3.python-gtkspell
4.python-gksu2
5.libgdl-1-common
6.libgdl-1-3
7.python-gdl
8.libgda-4.0-common
9.libgda-4.0-4
10.python2.5-minimal
11.libdb4.6
12.python2.5
13.python-gda
14.python-gnome2-extras" 
```also could you tell me which repositories suit my system?  [site:]("http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=python-gtkmozembed") 

 i 'm runing ubuntu 10.4  --2.6.32-28 generic kernal

---

### Post by wildmanne39 on 2011-06-21
> **iebo said:**
> hey guys i'm tring to install some packages for speed touch  330 (black) usb modem :popcorn:

 it's a bit hard to manage this pks one by one ...so is there any automatic repositories out there for this list?

```
 1.python-gtkmozembed
2.python-eggtrayicon
3.python-gtkspell
4.python-gksu2
5.libgdl-1-common
6.libgdl-1-3
7.python-gdl
8.libgda-4.0-common
9.libgda-4.0-4
10.python2.5-minimal
11.libdb4.6
12.python2.5
13.python-gda
14.python-gnome2-extras" 
```also could you tell me which repositories suit my system?  [site:]("http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=python-gtkmozembed") 

 i 'm runing ubuntu 10.4  --2.6.32-28 generic kernal
Hi, we need more information, do you only have a modem or do you also have other internet capabilities? Run this in a terminal
```
sudo lshw -C network 
```
```
lspci -nn
```
```
iwconfig
```
```
lsmod
```and also this command

[COLOR="RoyalBlue"]lsusb[/COLOR]

one at a time and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.

---

### Post by iebo on 2011-06-21
```
  tor@tor-laptop:~$ sudo lshw -C network
[sudo] password for tor: 
  *-network               
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:72:16:41:35
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 firmware=5787m-v3.23 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:28 memory:f6000000-f600ffff
  *-network
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 01
       serial: 00:47:o4:06:38:04
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k ip=192.168.1.98 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:f8000000-f800ffff
tor@tor-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a03] (rev 03)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 [8086:2843] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 03)
00:1f.2 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller [8086:2828] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03)
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express [14e4:1693] (rev 02)
04:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR5001 Wireless Network Adapter [168c:001c] (rev 01)
0f:06.0 CardBus bridge [0607]: Texas Instruments PCIxx12 Cardbus Controller [104c:8039]
0f:06.1 FireWire (IEEE 1394) [0c00]: Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller [104c:803a]
0f:06.2 Mass storage controller [0180]: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) [104c:803b]
0f:06.3 SD Host controller [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller [104c:803c]
tor@tor-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"beep_wireless"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:01:40:10:5D:A2   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=25/70  Signal level=-85 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

tor@tor-laptop:~$ lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_realtek   203408  1 
snd_hda_intel          22005  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
arc4                    1153  2 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
snd_seq_dummy           1338  0 
bitblit                 4707  1 fbcon
snd_seq_oss            26722  0 
softcursor              1189  1 bitblit
snd_seq_midi            4557  0 
vga16fb                11385  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
vgastate                8961  1 vga16fb
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ath5k                 121632  0 
snd_timer              19098  2 snd_pcm,snd_seq
joydev                  8740  0 
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mac80211              205402  1 ath5k
pcmcia                 30784  0 
i915                  287458  3 
drm_kms_helper         29329  1 i915
snd                    54180  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ath                     7611  1 ath5k
drm                   162409  4 i915,drm_kms_helper
soundcore               6620  1 snd
intel_agp              24375  2 i915
i2c_algo_bit            5028  1 i915
nsc_ircc               18220  0 
yenta_socket           20408  1 
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
video                  17375  1 i915
rsrc_nonstatic         10015  1 yenta_socket
psmouse                63245  0 
agpgart                31724  2 drm,intel_agp
lp                      7028  0 
cfg80211              126528  3 ath5k,mac80211,ath
parport                32635  2 ppdev,lp
output                  1871  1 video
acer_wmi               13861  0 
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
tifm_7xx1               3690  0 
irda                  186620  1 nsc_ircc
uvcvideo               57310  0 
serio_raw               3978  0 
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
sdhci_pci               5470  0 
sdhci                  15462  1 sdhci_pci
tifm_core               6045  1 tifm_7xx1
led_class               2864  3 ath5k,acer_wmi,sdhci
crc_ccitt               1339  1 irda
ohci1394               26950  0 
ieee1394               81181  1 ohci1394
tg3                   109324  0 
tor@tor-laptop:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 064e:a101 Suyin Corp. Acer CrystalEye Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
tor@tor-laptop:~$ 
 
```thanks wildmanne39 ...yes i have Internet access

---

### Post by wildmanne39 on 2011-06-21
Hi, I found one link about this modem, and it shows how he fixed it.
[http://ubuntuforums.org/showthread.php?t=1190096&highlight=speed+touch+330+%28black%29+usb+modem](http://ubuntuforums.org/showthread.php?t=1190096&highlight=speed+touch+330+%28black%29+usb+modem)

---

### Post by iebo on 2011-06-22
ok i will give it a try


but would you look at this 

[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=python-gtkmozembed](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=python-gtkmozembed)

i have no clue who will fit my distribution ?

---

### Post by wildmanne39 on 2011-06-22
> **iebo said:**
> ok i will give it a try


but would you look at this 

[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=python-gtkmozembed](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=python-gtkmozembed)

i have no clue who will fit my distribution ?
Hi, I looked but I do not know what version of ububntu you are using, you can find out by typing this command in a terminal
```
lsb_release -a
```and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.

---

### Post by iebo on 2011-06-22
ok many thanks it's work  fine with me now   :guitar:l
even though the buttom panel blink sometimes but it doesn't matter

---

### Post by wildmanne39 on 2011-06-22
> **iebo said:**
> ok many thanks it's work  fine with me now   :guitar:l
even though the buttom panel blink sometimes but it doesn't matterHi, your welcome would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

---

### Post by ava182 on 2011-06-22
not to criticize but i Had it its probably the worst modem ever made

---

