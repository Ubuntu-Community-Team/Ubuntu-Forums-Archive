---
title: "Wifi signal deteriorating on ubuntu 12.04 LTS"
date: 2012-09-29
forum: General Help
---

### Post by DustinDavidson on 2012-09-29
hi im useung a ralinks usb wifi card on my desktop and my signal starts degrading jumps from connected to not and is suffering bad going from 1.2mbs to a crawl at 2-5kbs im wondering if theres anyway or code i can use to fix this issue as i use this OS on the computers i work on at my shop thankz for your time hope to get a reply soon

---

### Post by Eirreann on 2012-09-29
The funny thing is that I had this problem as well for the first few days that I had Ubuntu 12.04.  But after a while it just stopped doing that for some reason, so maybe it'll just be a temporary thing for you as well!  We can hope, at least!

---

### Post by DustinDavidson on 2012-09-29
the code i get from lsmod
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55605  1 vfat
snd_hda_codec_hdmi     31775  4 
bnep                   17830  2 
rfcomm                 38139  0 
bluetooth             158438  10 bnep,rfcomm
arc4                   12473  2 
rt2800usb              22300  0 
rt2800lib              53264  1 rt2800usb
crc_ccitt              12595  1 rt2800lib
rt2x00usb              20061  1 rt2800usb
rt2x00lib              48858  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              436455  3 rt2800lib,rt2x00usb,rt2x00lib
ppdev                  12849  0 
snd_hda_codec_realtek   174055  1 
snd_seq_midi           13132  0 
cfg80211              178679  2 rt2x00lib,mac80211
snd_hda_intel          32765  4 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
psmouse                72846  0 
serio_raw              13027  0 
joydev                 17393  0 
k8temp                 12905  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
nouveau               712294  3 
asus_atk0110           17742  0 
parport_pc             32114  1 
mac_hid                13077  0 
snd                    62064  18 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sp5100_tco             13495  0 
i2c_piix4              13093  0 
ttm                    65344  1 nouveau
drm_kms_helper         45466  1 nouveau
drm                   197692  5 nouveau,ttm,drm_kms_helper
soundcore              14635  1 snd
i2c_algo_bit           13199  1 nouveau
mxm_wmi                12859  1 nouveau
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
wmi                    18744  1 mxm_wmi
video                  19068  1 nouveau
ati_agp                13242  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
usbhid                 41906  0 
hid                    77367  1 usbhid
pata_atiixp            12999  2 
r8169                  56321  0 

code from iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Detour"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: 00:0E:8E:24:F6:21   
          Bit Rate=11 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=45/70  Signal level=-65 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:3561  Invalid misc:6537   Missed beacon:0

eth0      no wireless extensions.

code from lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:1b:fc:1c:94:c1
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=N/A latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:42 ioport:ee00(size=256) memory:fdcff000-fdcfffff memory:fdd00000-fdd1ffff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:2.3
       logical name: wlan0
       serial: e8:4e:06:02:20:8e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=3.2.0-23-generic-pae firmware=0.29 ip=10.10.80.25 link=yes multicast=yes wireless=IEEE 802.11bgn

plz help

---

